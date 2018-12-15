# Step 3: ParcourSup

## Algorithm overview

ParcourSup does not follow the same principles than the two previous algorithms. The key idea of this approach is to consider that student does not express ordered wishes, but only a _set_ of wishes. For schools, it does not change anything, they still have to rank the student who apply to them.

At a given date, the schools start to answer. A student can receive three kind of answers:

  - `accepted`: the school is OK to recruit this student if the student is OK to join;
  - `waiting list`: the school might accept the student but prefer others;
  - `rejected`: the school does not want to recruit this student.

When a student receives an `accepted` proposition, she can:

  - `accept` it, then she is recruited in this school and the process stops for her;
  - `reject` it, then she will never join this school;
  - `wait` for something better.

At any point in time, she can only keep only _ONE_ which in `wait` state. If she receives two `accepted` proposition, she has to chose between those two (_i.e._, `accept` or `reject` one of the two). 

Each proposition made to a student has a given _Time To Live_ (TTL). We consider by default a TTL of 7 days. If the school does not receive an answer before the TTL, the proposition is considered as `rejected` by the candidate.

Based on the answer received from the students, each school chan then change a `waiting list` answer into an `accepted` one.

In 2018, the process started the 22th of May and ended the 21th of September, giving a period of 123 days to process the recruitement.


## Expected Work

We ask you to develop a simulation engine that allows one to play with different parameter and simulate the behaviour of ParsourSup. 

Developers will be able to add new school or candidate profiles according to the _Open/Closed_ principle[^1]. We provide two default profile description, and it is your responsibility to add new ones, and demonstrate how your simulation engine supports easily the creation of such new profiles.

Member of the MESRI cabinet will then be able to configure a given simulation using command line parameters, for example stating that 20% percents of the students behave as `X`, and 80% as `Y` (same for schools).

### Default profile for Students: `Caution`

By default, we consider students who show caution. A student who receive a proposition will automatically accept it. And, if multiple acceptation are received at the very same time, the student will then use her wish list to select her preferred one.


### Default profile for Schools: `Ranked`

By default, a school will accept all the students in its ranking until it reach its capacity, consider an overbooking of 25% as waiting and reject all the other candidates.

### New metric: `--filling`

This metric is dedicated to schools. Based on the input dataset and the computed solution, the metrics computes the following information:

  - the number of school that recruited the right number of students;
  - the number of school that didn't recruit enough students;
  - the number of school that recruits more students than their initial capacity.

These three integers are printed on `stdout` in this very order.

### New output: Recruitment graph

The MESRI wants to publicly demonstrate the efficiency of ParcourSup. The idea here is to generate a graph where the `x` acts represents the days and the `y` axis the number of student without affectation.

This graph must be generated as a PNG image.

To do so, you might consider using a plotting language and embed it into your language[^2]. Good candidates are `Gnu Plot` or `R`.

## Running your project

The `parcoursup.sh` tool must be conforms with the specifications of the two previous tools (_i.e._, handle the following arguments: `-i`, `-o`, `-b`, `--distance`, `--satisfaction`, `--stability`).

In addition, it must accept the following ones : 

  - `--profiles`: lists all available profiles, identifying the default ones for school and students;
  -  `-c profile:percentage`: specifies that a given percentage of candidates follow a given profile. By default, all the candidates follow the default candidate profile;
  -  `-s profile:percentage`: specifies that a given percentage of schools follow a given profile. By default, all the schools follow the default school profile.
  - `-g image`: generate the recruitment graph into the `image` PNG file. If not provided, you do not have to generate an image;
  - `--ttl i`: change the default TTL to `i`;
  - `--days i`: specify `i` as the number of days available for this simulation (default is `123`).
  - `--seed i`: specify a seed for the random generator to make an experiment reproducible.
  - `--filling`: compute the `filling` metric.
 
 At the end of the execution of a given simulation, the program must write on `stdout`:
 
   - the number of days consumed to find a solution for all students;
   - or `timeout` if some students are still not recruited after available numbers of days.

## Hints to define profiles

Here are some hints to define profiles, but your are encouraged to create your own.

### Candidates 

  - `curious`: a curious student will wait until the very end of the recruitment process to accept its preferred proposition. It means that even if she receives an `accept` to her first wish, she will keep it in `wait` mode until the very last day of the process.
  - `top5`: such a student will wait until a proposition in her first five wishes is made. If so, the proposition is automatically accepted.
  - `stubborn`: a stubborn student will reject any proposition that is not her first or second choice. 
  - `lowering_expectation`: Let us consider a student who have 15 schools in her which list. During the first 20% of the simulation, she will wait for a positive answer from her first 5 schools. Then for 30% of the simulation, she will wait for a proposition from her first 10 schools. Finally, during the remaining 50% of the simulation, she will accept any proposition.

  
### Schools

  - `open_doors`: these schools will accept all the ranked students (_i.e._, no wait list or rejection)
  - `picky`:  These schools accepts the first students that meet their capacity, and reject all the others (no wait list).
  - `overbooking-n`: such a school accept students with `n`% of  overbooking.



[^1]: _"An object-oriented system should be open for extension, but closed for modification"_.

[^2]: A simple embedding is to use a `System.exec("...")` instruction in your code calling the plotting tool