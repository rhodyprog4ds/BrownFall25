---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.12
    jupytext_version: 1.6.0
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Grading

This section of the syllabus describes the principles and mechanics of the grading for the course.
This course will be graded on a basis of a set of *skills* (described in detail the next section of the syllabus). This is in contrast to more common grading on a basis of points earned through assignments.

+++

## Principles of Grading

Learning happens through practice and feedback. My goal as a teacher is for you to learn. The grading in this course is based on your learning of the material, rather than your completion of the activities that are assigned.


This course is designed to encourage you to work steadily at learning the material and demonstrating your new knowledge. There are no single points of failure, where you lose points that cannot be recovered. Also, you cannot cram anything one time and then forget it. The material will build and you have to demonstrate that you retained things.

- Earning a C in this class means you have a general understanding of Data Science and could participate in a basic conversation about all of the topics we cover. I expect everyone to reach this level.
- Earning a B means that you could solve simple data science problems on your own and complete parts of more complex problems as instructed by, for example, a supervisor in an internship or entry level job. This is a very accessible goal, it does not require you to get anything on the first try or to explore topics on your own. I expect most students to reach this level.
- Earning an A means that you could solve moderately complex problems independently and discus the quality of others' data science solutions. This class will be challenging, it requires you to explore topics a little deeper than we cover them in class, but unlike typical grading it does not require all of your assignments to be near perfect.
<!-- Earning an A  -->



Grading this way also is more amenable to the fact that there are correct and incorrect ways to do things, but there is not always a single correct answer to a realistic data science problem. Your work will be assessed on whether or not it demonstrates your learning of the targeted skills. You will also receive feedback on how to improve.

+++

## How it works

```{warning}
This is a significant revision, so this is the first time with this grading scheme, some things may get updated as we go. They will be announced clearly and will be in students' favor in general.  
```

Different activities will be an opportunity to demonstrate your *level of competency* at a specific *objective* for the course. These will be converted into your grade. 


The Objectives are:
- *experience*: gain hands on experience with data science- earned by answering prismia questions
- *communication*: effective communication with data and code - earned in assignments and extensions
- *data manipulation*: manipulating data - earned in assignments and extensions
- *exploratory data analysis*: explore data, get preliminary insights - earned in assignments and extensions
- *modeling*: build models with data - earned in assignments and extensions
- *process*: discuss and apply the data science process in different forms  - earned in assignments and extensions


There will be multiple opportunities to demonstrate each objective. 



### Experience 

- absent: not in class, not made up, or no answers in prismia
- present: in class and questions answered, even if not correct or class made up
- active: in class and most questions answered correctly or class made up

### Communiation, Process, Data, EDA, Modeling

- unattempted: not submitted or significant [style](#style:hard) violations
- partial: good faith attempt, but not quite complete understanding **some assigments may only be eligible for partial demonstration of an objective**
- complete: good, correct understanding at a basic level **assigments are generally designed for compelte demonstration of an objective**
- innovative: in depth analysis **required to earn above a B, generally in extensions of assignments**


## Activities

The activities are what you will *do* to demonstrate your learning. 

### Participation

While attending synchronous class sessions, there will be understanding checks and in class exercises.
Completing in class exercises counts as toward your participation grade. If you miss class you can read the notes, follow along with them try out the code yourself and then attend office hours to discuss with a TA or Dr. Brown. 

After each class you will add your in class notebook to your portfolio. 

### Assignments

For your learning to progress, you will practice with the skills outside of class time. You will submit all of your assignments in your portfolio repository.  All instructions will be posted on this site. 



Assignments will each evaluate certain objectives. After your assignment is reviewed, you will get qualitative feedback on your work, and an assessment of your demonstration of the targeted skills. In general you will earn either partial or complete for the applicable objectives in an assignment.  

These are the assignments where you *can* earn **complete** on each objective. 
:::::{csv-table}
:header: outcome,A1,A2,A3,A4,A5,A6,A7,A8

process,🟨,🟨,🟨,✅,✅,✅,✅,✅,✅
communication,✅,✅,✅,✅,✅,✅,✅,✅
data,✅,✅,✅,✅,✅,✅,✅,✅
modeling,,,,,✅,✅,✅,✅
exploratory,🟨 ,✅,✅,✅,✅,✅,✅,✅

:::::

- 🟨 indicates you can at most earn partial
- ✅ inidcates you can earn compelte

You *can* revise assignments if you do not earn achievements. Revisions need to include reflections about what you misunderstood and how you fixed it. 

You can revise what you submitted and resubmit it, with reflections and explanation of what you were confused about, what you tried initially, how you eventually figured it out, and explains the correct answer. 

In general, the 

### Extensions

```{warning}
Details on how to submit extensions will follow, you cannot submit any until after assignments are done anyway. 
```

After you practice with a concept at a basic level in assignments, you can extend your work 

+++

(grade:calculation)=
## Grade Calculation


For communication and process you need to show continued progess. For modeling, exploratory, and data you need to have analyses that are compelte most of the time and a smaller number of innovative analyses.  

::::::::{csv-table} Minimum evaluations for each grade
:header: outcome,level,A,A-,B+,B,B-,C+,C,C-,D+,D,F
:label: minevals

experience,active,15,15,15,15,10,10,10,5,5,5,0
experience,present,22,22,22,22,22,22,22,22,22,22,0
process,innovative,      3,2,1,1,0,0,0,0,0,0,0
process,complete,        4,4,4,4,4,4,3,2,2,1,0
process,partial,         5,5,5,5,5,5,5,5,5,3,0
communication,innovative,3,2,1,0,0,0,0,0,0,0,0
communication,complete,  6,6,6,6,0,0,0,0,0,0,0
communication,partial,   4,4,4,4,4,4,4,4,4,3,0
data,innovative,         3,2,1,0,0,0,0,0,0,0,0
data,complete,           6,6,6,5,5,5,4,4,3,2,0
modeling,innovative,     3,2,1,0,0,0,0,0,0,0,0
modeling,complete,       4,4,4,4,3,3,2,2,1,1,0
exploratory,innovative,  3,2,1,0,0,0,0,0,0,0,0
exploratory,complete,    4,6,6,6,5,4,3,2,1,1,0
::::::::

These are all minimums and "or better" applies, so innovative ratings count toward the count of complete ratings, but not the other way around.  `Partial` ratings only impact your grade for process and communication. For other objectives you might receive a rating or partial to acknowledge that you made some progress, but you will need to reach complete for your grade.  

Your grade will go up slowly, but it can only go up.  It is **not** an average. 

The last couple of assignments will have more open-ended challenges to them, where you can earn *innovative* for process in the assignment.  

This means you only need to do 3 extensions to get an A. 

(ramtoken)=
## Ram Tokens

We will have "ram tokens" that are like extra credit.  

They can be spent for:
- hints when you are very close to get a suggestion instead of a question (graders's discretion)
- to upgrade experiences from present to active


Some ways to earn them include: 
- contribute additional examples or interpretation to the notes.  
- attend office hours to ask for clarification about material based on your notes taken in class and the notes here (eg not just assignment questions) **especially useful if you miss class**