# Step 2: Student First (aka Plan B)

## Algorithm overview

If you look at the satisfaction metrics for APB, it does not look really fair for students (this was one of the main attack against APB in the past). For example, in the _100,000_ dataset, only 54% of the students obtained their first choice when recruited following an stable-marriage approach.

We propose here to evaluate a completely different strategy, where we will privileges students choices: a student who chose a school _S_ as first choice will always be preferred over a student who chose _S_ as second choice. We only use the ranking defined by the schools when the number of candidates exceed the capacity of the school.


## Expected Work

  1. Implement the _student-first_ algorithm;
  2. Identify common modules and leverages Maven to handle it;
  3. Benchmark your solution (and the APB one) at both functional and non-functional levels

### Running your project

We provide a shell script named `student_first.sh` that wraps the command line to the `mvn exec:java` plugin. It should react to the very same arguments and usage than the `apb.sh` one.

## Common modules

The `APB` and `Student-First` tools are defined as independent, but they share a lot of common code: file parsing, metrics computation, command line argument handling, ... Copy-pasting code from one project to the other is not reasonable from a software engineering point of view.

Maven modules come here to the rescue. The current project is composed of four modules:

  1. The root one (`pom.xml`), which contains all the information common to all the sub-projects;
  2. The `apb` one (`apb/pom.xml`), which contains information related to `APB`;
  3. The `student_first` one (`student_first/pom.xml`), which contains information related the algorithm described in this step;
  4. And finally the `parcoursup` one (`parcoursup/pom.xml`);

Your job here is to create a fifth module named `commons`, that will contain the library shared by all the three other projects. Look at the way the different _POM_ files were defined to understand how a module is created. 

Then, you will indicate this new module as a _dependency_ of the `commons` one. By doing so, you are using the very same mechanism than the one providing libraries such as JUnit, but for your very own work!

At the end:

  * the root `pom.xml` must references the newly created module;
  * the `pom.xml` defined in the `commons` module must have the `root` one as parent;
  * the modules `apb` and `student_first` must reference the `commons` one as a dependency.
  * executing `mvn clean install` in the root directory compiles everything

## Benchmarks

Remember that the idea here is to gather factual information about the recruitment process. We need to measure and analyse the behaviour of the different methods, at both functional (_e.g._, the quality of the service provided to the French population) and non-functional (_e.g._, the average execution time) levels.

We are expecting a `benchmark.pdf` file at the root of your project directory that will contain such an analysis.
  
### Functional level

Your work here is to use your recruitment implementations (APB and Student-first) on the given datasets, and to analyse the obtained results using the metrics defined in the previous step.

Can we conclude that one algorithm is _better_ than the other one? Can we even defined what _better_ means in this case?

Use data representation of your choices to discuss this matter, based on the functional metrics you can compute on the datasets and solutions.

### Non-Functional level

We are also worried by the execution time of the algorithms, considering the population of students and school to be considered. 

You must decompose the execution time in three: (i) _parsing_, (ii) _computing_ and (iii) _exporting_ the solution.

To compute accurate measure, you must not consider a single execution fo your program, as the JVM needs time to warm-up and uses internal optimisations that might interfere with your code. 

Students are encouraged to use the [JMH](https://openjdk.java.net/projects/code-tools/jmh/) framework to address this issue and automate benchmarks.

If you are not confident enough in your skills to use JMH (actually it is more simple than it looks like), it is perfectly fine to use the following method to approximate a reasonable average execution time:

  1. Execute `N` times (`N` being in [10,100]) your code on a given dataset;
  2. For each execution, collect the associated execution time;
  3. Remove the min and max values;
  4. Compute the average execution time with the `N-2` remaining values.

But it s clear that JMH will give you way more accurate results than this method.

Find the right graphical representation to present your non-functional benchmark to your customer (bar chart, moustache box, point cloud, ...).


## Appendix: JMH usage

[Examples](http://hg.openjdk.java.net/code-tools/jmh/file/tip/jmh-samples/src/main/java/org/openjdk/jmh/samples/) are available to help you kickstart and [understand how things work](http://blog.soat.fr/2015/07/benchmark-java-jmh-fine-tuning/).

Writing benchmarks can be difficult and [some pitfalls must be avoided](http://www.oracle.com/technetwork/articles/java/architect-benchmarking-2266277.html). The following research paper describes clearly those pitfalls and how to avoid them. It is easily readable and understandable as really focused on a problem/solution approach.

> [Automatic Microbenchmark Generation to Prevent Dead
Code Elimination and Constant Folding](http://diversify-project.eu/papers/rodriguez-cancio16.pdf) - _<span style="font-size: 0.7em;">Rodriguez-Cancio, Marcelino, Benoit Combemale, and Benoit Baudry. "Automatic microbenchmark generation to prevent dead code elimination and constant folding." Proceedings of the 31st IEEE/ACM International Conference on Automated Software Engineering. ACM, 2016.</span>_




