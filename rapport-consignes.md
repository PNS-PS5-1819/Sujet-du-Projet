| Topic        | Expected           |
| :-------------: |:-------------:|
| Location     | at the root of your git project-structure| 
| Name     | `Team-X-report` (replace `X` by your team ID) | 
| Format     | `PDF`| 
| Date     | see [the subject file](https://github.com/PNS-PS5-1819/informations/blob/master/sujet.md#schedule)| 
| Content     | see below| 



# Content of the report
Items below are labeled with `professional`, `expert`, `raw data`, or `scientific`, meaning that they will be used to grade a specific aspect of your work. See Grading section for more details.

- A first page that contains project information, your team name and describes the composition of your team (`professional`)


- Two sections, one for APB and one for Parcoursup ; both containing the following template:
  - what is the algorithm behind it? What are its characteristics? (`expert`)
  - what are the pros, and the cons of such algorithm? (`expert`)
  - how well/bad did you perform on the provided datasets (both in term of students affectations and execution time)?  (`raw data`)
  - how many ticks of simulation does it take to reach an affectation rate of 5%? 50% 80%? 100%?
  Answer for each dataset, if possible and applicable.  (`expert`, `raw data`)
 
 - A section that explains *how* you obtained these numbers. 
 More factually, **how did you measure the execution times** and the other metrics you provided? 
 How does your execution-time evolve? 
 Can you guess your execution time for 10 millions students? 100 millions? Can you give us a function that describes your execution time, given a number of students and/or universities? (`scientific`)
 
 
- A section that factually compares APB and Parcoursup and give metrics to answer the ministry question: APB or Parcoursup? ( `expert`, `scientific`)

- A section focused only one your software quality. 
This section will give the ministry condidence in your proposition and in you as professionals. 
This will also be used for the ministry to state if it can be easily passed to another team, or if only s part can be used, or nothing (`professional`)
  - How well/bad tested in your codebase? 
  - How well/badly decoupled is your code?
  - Can I reuse your parser only?
  - Can I use my own parser and use your algorithm easily?
  - What is the best thing in your codebase? (eg small classes, easy to swape algorithm, well-tested)
  - What is the worst thing in your codebase (eg huge classes, not-so-easy to swape algorithm, poorly-tested)
  - Is your code well-documented?
  A good documentation does not mean that you have to document and comment everything everywhere everytime. 
  Document/comment some code, and explain in this section why it mattered to document this.
  - If you had `400` effort-points to spread accross your team, how would you spread them? 
  A 100 points repartition means that each member of the team has provided the exact same effort in this project.
  A 400/0/0/0 point repartitions means that only one member of the team worked on the project.
  Use only numbers that can be divided by `5` or `10`, no need for things like `102.7598`.
  
# Grading  
  We will use those criteria: `professional`, `expert`, `raw data`, and `scientific` to evaluate your work.
  Items in the text above are marked with those criteria.
  All those criteria are important and will weigth approximately the same in your final grading.
  
  Why? because:
  
  - A project made by experts, but can't be used because it is not professional is only a half-done work and does not give me confidence in your team.
  - A project made by skillful developers but without expertise nor scientific approach does not give confidence in your understanding of the ministry issues, neither in your results nor mathematical foundation of your background.
  - A professional project, made with expertise, but without data nor analysis, is useless for the ministry and the mission they gave to you.
