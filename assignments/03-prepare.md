---
downloads:
  - file: ./data/stack_overflow_24.csv
    title: 2000 random rows from the 2024 stack overflow survey
  - file: data/stack_overflow_25.csv
    title: 2000 random rows from the 2025 stack overflow survey
  - file: data/stack_overflow_schema_24.csv
    title: schema for the 2024 stack overflow survey
  - file: data/stack_overflow_schema_25.csv
    title: schema for the 2025 stack overflow survey
---

# Assignment 3: Preparing for Analysis

Due: 2025-10-13


## Submission Instructions

1. Create one notebook for each of the following tasks
1. Export as myst markdown (using jupytext)
1. Upload to a branch called `assignment3`


## Job Satisfaction Dataset

You can download the following files from this page (at the top the download icon). 

```{list-table}
:header-rows:1

* - file 
  - description
* - stack_overflow_24.csv
  - 2000 random rows from the 2024 stack overflow survey
* - stack_overflow_25.csv
  - 2000 random rows from the 2025 stack overflow survey
* - stack_overflow_schema_24.csv
  - {term}`schema` for the 2024 stack overflow survey
* - stack_overflow_schema_25.csv
  - {term}`schema` for the 2025 stack overflow survey

```
Your task is to create a dataset that someone can be used to compare how developer job satisfaction changed from 2024 to 2025. 

Note that you were given only a random sample of 2000 rows from each year, but your code should work, for the full datasets (49000+ rows) so you should do everything programmatically. 

Keep all of the columns that could be helpful in answering the question and combine the two csvs into one in a way that lets someone see trends year over year. 

In this, you should handle missing values appropriately in service of that general goal. 

## UN Votes

use the data from the tidy tuesday on [UN Votes](https://github.com/rfordatascience/tidytuesday/tree/main/data/2021/2021-03-23) to create a dataset and then answer (using stats and/or plots): 

> Which (if any) countries vote together often, but not for all issues? 


## Today I learned

Write a notebook that can, on any given day, tell you how many of the most recent 25 posts to r/TodayILearned are from wikipedia

Tips:
- `'https://www.reddit.com/r/todayilearned.json'` gives you 25 recent posts
-  there is a `url` column, once that is unpacked. 