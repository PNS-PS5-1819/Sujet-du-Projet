# Step 1: Implementing Admission PostBac

## Algorithm overview

In APB, each student defines an ordered _wish list_ of schools, and each school ranks the students who applied to this curriculum in an ordered way. The objective is to match each student to a school, maximising the "happiness" of both stakeholders: A student *must* be accepted to the *best* school she ranked, with respect to the ranking expressed by all the school she applied to.

This is a variation of the _Stable Marriage_ problem, The following text is an extract of the [Wikipedia page](https://en.wikipedia.org/wiki/Stable_marriage_problem) dedicated to this problem

The _Stable Marriage_ problem is stated as the following:


> Given **n** men and **n** women, where each person has ranked all members of the opposite sex in order of preference, marry the men and women together such that there are no two people of opposite sex who would both rather have each other than their current partners. When there are no such pairs of people, the set of marriages is deemed stable.


David Gale and Lloyd Shapley provided in 1962 an algorithm to solve this problem:

```
function stableMatching { 				// source: wikipedia
    Initialize all m ∈ M and w ∈ W to free
    while ∃ free man m who still has a woman w to propose to {
       w = first woman on m’s list to whom m has not yet proposed
       if w is free
         (m, w) become engaged
       else some pair (m', w) already exists
         if w prefers m to m'
            m' becomes free
           (m, w) become engaged 
         else
           (m', w) remain engaged
    }
}
```

This algorithm ensures the two following properties:

  - **Everyone gets married**:
    - _At the end, there cannot be a man and a woman both unengaged, as he must have proposed to her at some point (since a man will eventually propose to everyone, if necessary) and, being proposed to, she would necessarily be engaged (to someone) thereafter._ 
  - **The marriages are stable**:
    - _Let Alice and Bob both be engaged, but not to each other. Upon completion of the algorithm, it is not possible for both Alice and Bob to prefer each other over their current partners. If Bob prefers Alice to his current partner, he must have proposed to Alice before he proposed to his current partner. If Alice accepted his proposal, yet is not married to him at the end, she must have dumped him for someone she likes more, and therefore doesn't like Bob more than her current partner. If Alice rejected his proposal, she was already with someone she liked more than Bob._

## Expected Work

  1. Implement a parser that support the input files available in the provided dataset;
  2. Adapt the Gale-Shapley algorithm to work with schools and students instead of men and women;
  3. Implement a set of metrics to measure your solution

## Running your project

We provide a shell script named `app.sh` that wraps the command line to the `mvn exec:java` plugin.

### Command line arguments

You have to support the command line arguments, given in an arbitrary order:

  - `-i filename`: a path to the dataset to be used as input
  - `-o filename`: a path to the solution file to be created
  - `--distance`: a boolean flag to compute the distance between a solution and a baseline (see `-b`)
  - `--satisfaction`: a boolean flag that triggers the satisfaction metrics computation if activated.
  - `-b filename`: a path to a reference solution, when needed (see `--distance`)
  - `--stability`: a boolean flag to compute the stability of the solution.

**Hints**:
 
  - to handle command line parsing, you can consider using [Apache Commons CLI](https://commons.apache.org/proper/commons-cli/), a reference API to support this task properly.
  - Input files can be bogus. In such a situation, you program must exit with an exit code equals to `1`.

### Compute a stable marriage 

For example, to create a file named `s10.txt` that contains the recruitment made according to the dataset stored in `.txt`, you will invoke your code according to the following command line:

```
azrael:apb mosser$ ./apb.sh -i ../dataset/samples/sample_10.txt -o s10.txt
```

The contents of the `s10.txt` file must be conform to the solution file format (see dataset description):

```
azrael:apb mosser$ cat s10.txt
1 2 1 1 2 1 4 0 3 2
```

### Measure the distance between two solutions

A _difference_ is defined as the fact that a student affectation is not the same in the solution than in the baseline. Consequently, the _distance_ between a solution and a baseline is defined as the sum of the detected differences. 

To compute the distance between two solutions, you will invoke your code as the following:

```
azrael:apb mosser$ ./apb.sh -b ../dataset/solutions/solution_10.txt -o s10.txt --distance
0
```

The `0` printed on the standard output indicates that there is no differences between `s10.txt` and the baseline. 

```
azrael:apb mosser$ ./apb.sh -b ../dataset/solutions/solution_10.txt -o s10-bad.txt --distance
2
```

The `2` here indicates that there is a couple of students who differs in `s10-bad.txt` with respect to the given baseline.


### Measure the satisfaction of stakeholders

The satisfaction metrics measure the _hapinness_ of both schools and students. 

From the student point of view, considering wish lists of size `n`, we compute:

  -  the number of students who obtained their first choice, the number of students who obtained their second choice, ..., and finally the number of students who did not obtain an affectation at the end;
  - and the average choice obtained by the student population.

For the school point of view, we measure the average distance between each recruitment. Consider a school with a capacity of 3 students. If the school recruits its three first choices, then its satisfaction is maximal. But if this school recruits students ranked `4`, `8` & `12`, then its distance to the maximal satisfaction increases. We mesure such a distance as the average difference with an optimal recruitment. Here, `d = ( (4-1) + (8-2) + (12-3) ) / 3 = 6` (and in the optimal case, `do = ( (1-1) + (2-2) + (3-3) ) / 3 = 0`).


The program is invoked as the following: 

```
azrael:apb mosser$ ./apb.sh --satisfaction -o s10.txt -i ../dataset/samples/sample_10.txt
0  1  2  X
8  1  1  0
1.3
2.3
```

It means that considering the data stored in `sample_10.txt` and the solution stored in `s10.txt`:

  - `8` students obtained their first choice (rank `0`);
  - `1` student obtained her second choice (rank `1`);
  - `1` student obtained her third choice (rank `2`);
  - No students were out at the end of the recruitment process (rank `X`);
  - The average choice for students is `1.3` (`=  (8*1 + 1*2 + 1*3) / 10`);  
  - The average distance to optimal recruitment for schools is `2.3`.


### Measure the stability of the recruitment

This metrics measures that the _stability_ property of the algorithm is respected. A couple (_i.e._, a student-school pair) is defined as _unstable_ when a student preferred a school _S_ but was recruited in _S'_ even if she could have been recruited in _S_ based on the school ranking. A single student might be involved in multiple unstable couples.

To compute such an information, one can:

  1. Go through the list of schools and identify the rank of the last recruited candidate;
  2. Go through the list of students, and identify an _instability_ when the candidate has a rank higher than the last recruited candidate for a preferred school (_i.e._, a school ranked higher in the wish list than the one the candidate obtained at the end).

The program is invoked as the following: 

```
azrael:apb mosser$ ./apb.sh --stability -o s1000.txt -i ../dataset/samples/sample_1_000.txt
316
126
```

In this case, it means that:

  - `316` couples are detected as unstable;
  - `126` students are involved in these couples.

  
## Appendix: Error cases

  - Bad input file : exit code `1`
  - Missing file: exit code `2`
  - Cheated solution used as input: exit code `3`

