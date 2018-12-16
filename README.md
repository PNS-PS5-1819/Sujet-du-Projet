# Semester Final Project

  * Timeframe: 17/12/2018 → 23/12/2018
  * Staff: 
  	* [Benjamin Benni](mailto:benni@i3s.unice.fr): facilitation, software engineering.
    * [Sébastien Mosser](mailto:mosser@i3s.unice.fr): facilitation, software engineering.
    * [Christophe Papazian](mailto:papazian@polytech.unice.fr): algorithmic.

## Pedagogical Objectives

  1. Integrate a project framework with legacy artefacts that are not under your control;
  2. Improve your _programming-in-the-small_ skills;
  3. Deliver as fast as possible; 
  4. Discover continuous integration; 
  5. Use computer science and software engineering to answer a societal question.

## Project Summary
  
You client is the Department of Higher Education, Research and Innovation (_i.e._, _Ministère de l'Enseignement Supérieur, de la Recherche et de l'Innovation_, **MESRI**) of the French government. Or at least let's pretend it is, for the next five days.

After obtaining their _baccalauréat_ at the end of high school, students who wants to pursue their studies in the higher education system must follow a national recruitment process. Until 2017, this process uses a method called _Admission Post-Bac_ (APB), which was replaced in 2018 by a new method _ParcourSup_.

Changing from _APB_ to _ParcourSup_ triggered strikes and violent events (even from a French referential). The Minister ordered a study to your consulting company to compare both systems, and gather factual arguments to feed the public debate.

Your mission for the next five days is the following:
  
  - [Understand the legacy ecosystem](./steps/0_setup.md)
  - [Implement the algorithm used by APB](./steps/1_apb.md)
  - [Give priority to students](./steps/2_student_first.md)
  - [Implement a simulation engine for ParcourSup](./steps/3_ParcourSup.md)
  - [Write a report intended to the Minister's cabinet](./steps/4_Report.md)

## Timeline & Deliveries

  - Monday:
    - 08:00: Kick-off presentation (amphitheater)
    - 10:00: All teams declared __properly__ in GitHub Classroom
    - 19:00: _APB_ is working
  - Tuesday:
    - 13:15: Q&A (amphitheater)
    - 19:00: _Plan B_ + Benchmark available 
  - Wednesday: 
    - 19:00: Delivery script executed for the first time (tag: `first`)
  - Thurdsay:
    - 08:00 - 12:15: Demonstration to cabinet's member of the first results (APB, Plan B & ParcourSup)
  - Friday: 
    - 19:00: Delivery script executed for the second time (tag: `almost`)
  - Sunday:
    - 19:00: Delivery script executed for the last time (tag: `final`)

## Technological Stack

  * Version control: Git (+ github classroom)
  * Programming language: Java 8
  * Unit tests: JUnit (4.12, 5)
  * Benchmarks: JMH
  * Build: Maven
  * Continuous Integration: Travis


## Contact

We use Slack for discussions (strict "no email" policy), particularly the `#ps5-final` channel. Use the public channel for questions/remarks related to the project, or direct message to your facilitator (Benjamin or Sebastien) for questions related to your group.

## Evaluation

  - Code: 30%
  - Delivery / Execution: 20%
  - Demonstration (Thursday): 10%
  - Report: 40%
  
## Frequently Asked Questions

> Will the input file always be valid?

No, and error should be yielded. But start simple.

> Do we need to parse entirely the input file?

Yes. You won't have all the information otherwise.

> Do we have to test our code?

Yes. Obviously. Unit testing is expected and required. 

> Do we have to use git?

Yes.

> Will the code be evaluated?

Yes. Especially the complexity, clarity, and respect to OOP principles will be evaluated.

> We don’t agree with the given architecture, can we change it?

No.
