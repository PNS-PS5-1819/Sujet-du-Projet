### Execution time (`Benchmark`)
Your project is going to evolve in a real-life use-case with time limitation.
We want to fastly register students.
Fastly can thus mean two things: 

1. the students are affected in a small number of simulation `tick`
2. the whole alorgithm that takes students, universities, wish-lists, and output the affectation is fast.

For the former, you need to measure how many students are affectated at a given point in time, and do that during all the simulation.
For the latter, how do you measure your raw-execution time? How can the ministry states that your proposition is more efficient because it provides an answer in less second that other teams?
We need to know how much time it takes to run your solution on a given input, to have an idea of execution times and maybe to compare your solution with another provider.
> This means you will develop a **benchmark**.

The benchmark will be performed using [JMH](http://openjdk.java.net/projects/code-tools/jmh/). [Examples](http://hg.openjdk.java.net/code-tools/jmh/file/tip/jmh-samples/src/main/java/org/openjdk/jmh/samples/) are available to help you kickstart and [understand how things work](http://blog.soat.fr/2015/07/benchmark-java-jmh-fine-tuning/).

Writing benchmarks can be difficult and [some pitfalls must be avoided](http://www.oracle.com/technetwork/articles/java/architect-benchmarking-2266277.html). The following research paper describes clearly those pitfalls and how to avoid them. It is easily readable and understandable as really focused on a problem/solution approach.

[Automatic Microbenchmark Generation to Prevent Dead
Code Elimination and Constant Folding](http://diversify-project.eu/papers/rodriguez-cancio16.pdf) - _<span style="font-size: 0.7em;">Rodriguez-Cancio, Marcelino, Benoit Combemale, and Benoit Baudry. "Automatic microbenchmark generation to prevent dead code elimination and constant folding." Proceedings of the 31st IEEE/ACM International Conference on Automated Software Engineering. ACM, 2016.</span>_

You will have to fill the benchmark module.
To start and run your benchmark we will perform:

```bash
cd teamX/benchmark
mvn clean install
java -jar target/benchmarks.jar -rf json
```

This will automatically output the execution of the benchmark in a `json` file.
