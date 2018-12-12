# Introduction

Our client is the french ministry of education. On September 2017, it gave us a critical mission. 
It asked us, along with the evolution of french cyber-ecosystem, to think about *a new solution for APB* (the system that matches students with universities). 
The minister thought about it already and depicted what it called Parcoursup. 
**It wants to analyze both APB and Parcoursup, and run simulations of how well or bad they behave given different contexts.**
We told them that we will put our best specialists on this topic, and that is why you are reading this.
You are the specialists in charge of analyzing APB, along with the new proposition, Parcoursup.
The ministry will not provide the source code of APB nor Parcoursup, so you will develop them from scratch.
Then, you will compare them. You are in charge of providing meaningful insights with carefully chosen metrics, so the minister can make the choice to either deploy, or stash Parcoursup based on data simulations.
You have one week to complete this mission (until 23/12/2018-23h59m- GMT+1), and the minister wants to have results early during the week.
This document summarizes you mission: it gives you background information on APB and Parcoursup, and details the ministry expectations as they gave them to us.

# Background

During their last year of high-school, french students have to chose where they want to go at the University. 
Universities, will then chose which students they accept ; students give their opinion ; and are thus registered. 
During the following year, the affectation-system may change in many ways. 
In this section we will present the old (named *APB*) and new candidate (named *ParcourSup*) systems with their characteristics.


## Admission Post-Bac

Admission Post-Bac was launched in 2009 and after 8 years of loyal services, the ministry wants to shut it down in 2017. 
During the last year of high-school, students will build up a *list*[^1] of wishes, the first element of the list being their best/top-wish, the last one being their worst. 
In a real-life scenario, students' wish-lists are ruled in many ways (*e.g.* minimal and maximal number of total wishes, minimal and maximal number of wishes targeting a specific type of formations) ; rules that **we will not take into account**. 
At some point the wish-lists are closed and send to the designated schools. 
Then, schools will in their turn, build up a ranked wish-list of students, the first-one being the one they want the most.

To sum up, at this point both parties (students and universities) have their own wish-lists built. 
Now it is time to match students' and universities' wishes. An algorithm will perform this match. 
A lot of different rules are taken into account when performing the match, (*e.g.* *Is the student repeating? Does her actual location matches the wish's location? What is the rank of the wish in the student's wish-list? What is the rank of the wish in the university's wish list? Is the formation selective or not?*) ; rules that **we will not take into account**.

This problem is a stable-marriage-problem[^2]. Gale-Shapley proposed an algorithm to fix it in 1962. 
The real-life APB context is different and more complex, but is still based on the Gale-Shapley algorithm. 
We will stick to a plain Gale Shapley algorithm here.
The algorithm will return student-university matches.

Thus, the selection occurs and students' wishes are either *accepted* or rejected. 
When a student's wish is accepted, her wish-list is cleared. 
When a student's wish is rejected, her next wish receive her student's file, and the selection occurs again.

The Gale-Shapley algorithm works on mapping between two sets, where allthe elements of both sets have emitted wishes to be mapped to elements of the other sets. 
Nothing here would be said that can not be found on the Wikipedia page of the Stable-marriage problem.
You will find explanations, example, variants, pseudo-code, algorithm explanation and animations on it.

The APB solution will run in one phase: students and universities will be matched only once, then students will either be affected or not affected. 
This phase takes place over a full week. 
The affectation and satisfaction rate may be interesting metrics to be measured.


## Parcoursup

Parcoursup is the brand new shiny affectation system. 
It shares commonalities with APB but we will focus only on their differences here. 
Parcoursup (PSup) does not allow a sorted students' wish-list. 
Students provide a *set*[^3] of wishes so students can wait for all the answers from the universities before taking their decisions. 
Students can hold a wish if the university stated that she were in the waiting-list or if the university didn't answered yet.

From mid-march, to the 17th of June, then from the 24th of June to mid-september, universities answer to students each day (but not necessarily every day). 
The simulation of Parcoursup is thus a discrete simulation, every day represent a tick of the simulation, and the simulation evolves tick after tick (*i.e.* day by day).


# Expected work

Your mission is to **implement** APB and Parcoursup given the provided specifications. 
Your solutions must be clear, well-organized, documented, commented, as, by law, the ministry have to open-source all algorithms involving the public[^4]. 
We will then expect for you to **benchmark** them and **compare** them. 
We provide here some metrics for you to start, but others are expected: number of days (weeks or months) needed to end the simulation, average satisfaction of the students. 
*Apply* your APB proposition over the provided datasets, *record* relevant metrics, then *save* and *report* them.
*Apply* your Parcoursup proposition over the provided datasets, *record* relevant metrics, then *save* and *report* them. 
Finally, compare your metrics, your approaches, and give your final decision on whether the ministry should stick with APB or go for large scale Parcoursup deployment.

Your propositions should be developed in Java, and use the Maven tool. 
Your project architecture should be multi-modules, meaning that there is a parent maven project, and n modules, linked to the parent project. 
More information can be found on the sonatype website[^5].

# Schedule

| Topic                                                         | Deadline (GMT+1)   |
| :-------------:                                               |:-------------:     |
| Starting your mission                                         | 17/12/2018-08AM    |
| APB is working                                                | 18/12/2018-12AM    |
| Parcoursup is working, Demonstration to the ministry          | 20/12/2018-Morning |
| Comparison Parcoursup/APB is working                          | 21/12/2018-11h59AM |
| Deadline for your report to the ministry, End of the mission  | 23/12/2018-11h59PM | 

# Resources and technical reference

We provide datasets of different sizes along with their acceptable solutions (*i.e.* other solutions are acceptable, but you are more likely to find the one provided) for you to apply your proposition. 
Small datasets are made for you to quickly check your implementation, and see how things go. 
Big ones are more realistic, and such large data can have a huge impact on your execution time. 
But how huge? How much time do you take to parse, process, and affect 1.000.000 students? 
How much time do you take to solely parse the input file? 
As a comparison, our internal specialist provided a APB-solution that takes 3.7 seconds to compute a solution on the 100.000 dataset , and 78 seconds to parse, match, and output the result on the 1.000.000 dataset.

A dataset (or *input-file*) is made of 3 sections: metadata, student descriptions, and school descriptions.

The first section is one line that contains 3 integers separated by spaces. 
They respectively represent the number of students' profiles **P**, the number of schools **S**, the size of the wish-list **W** (the number of choices made by the students) of all and every students.

Then, the second section contains **P** lines, each describing a student profile. 
A student profile is made of (5+**W**) information, spaces-separated, presented in the following order: `first name` ; `family name` ; `gender` F or M ; `birth-date` in the `yyyy-mm-dd` format ; actual `school academy` of the student ; and finally W `school identifiers` which is a sequence of integers.

Then the third and last section contains **S** lines, each describing a school profile. 
A school profile is made of 4 information, spaces-separated, presented in the following order: `school name` ; its `capacity` *i.e.* the number (integer) of students that the school can welcome this year ; `academy` of the school ; `size` of the wish-list N ; and the school `wish-list` which is N student identifiers. 
A student is identified by her row-index in the **P** list.

*Note*: All text-fields can be upper/lower-cased letters with accents, dashes, and quotes.

Below is an example of input file.

        10 5 3
        Geraldine   TELLIER          F 2000-02-25 Saint-Chamond     1 2 3
        Filipe      DAVY             M 2000-08-18 Libourne          2 1 0
        Brice       MANY             M 1998-12-20 Limoges           1 2 0
        Erwan       GIRONDE          M 2000-08-24 Nice              1 2 3
        Roxanne     FERNANDES        F 2001-08-21 Lanester          2 1 0
        Thomas      BERTHET          M 2001-05-23 Dole              1 2 3
        Marine      LOZACH           F 2000-01-30 Dijon             1 2 4
        Clarisse    LEBAILLIF        F 1999-10-28 Avignon           0 1 3
        Charlène    BENMANSOUR       F 2000-11-24 Marseille         4 3 1
        Océane      BONNEFOY         F 1999-04-07 Villenave-d'Ornon 2 1 0
        CPGE_Lycée_Bellevue          1 Toulouse         5 2 9 1 7 4
        Université_Clermont-Auvergne 4 Clermont-Ferrand 10 7 9 1 3 2 5 0 4 6 8
        Universitée_d’Angers         3 Angers           8 9 1 3 2 5 0 4 6
        IUT_Chimie                   1 Grenoble         5 7 0 3 5 8
        IUT_Environnement            1 Reims            2 6 8

As described in the first section of the file, they are 10 student profiles, each making 3 choices, across 5 different schools. The first line of the second section states that a girl named Geraldine TELLIER, born the 25th of february in 2000, actually in Saint-Chamond, wants to go to schools identified by 1, 2 and 3. By looking at the third section, we can say that she wants to go to the Université Clermont Auvergne first, then to Université d'Angers, then finally to IUT Chimie of Grenoble ; in that specific order. We can also note that IUT Chimie has ranked her in third position and has a capacity of 1 student.

[^1]: <https://en.wikipedia.org/wiki/List_(abstract_data_type)>

[^2]: <https://en.wikipedia.org/wiki/Stable_marriage_problem>

[^3]: <https://en.wikipedia.org/wiki/Set_(mathematics)#Definition>

[^4]: <https://fr.wikipedia.org/wiki/Loi_pour_une_R%C3%A9publique_num%C3%A9rique>

[^5]: <https://books.sonatype.com/mvnex-book/reference/multimodule-sect-simple-parent.html>
