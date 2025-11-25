---
downloads:
  - file: ./data/fake_or_real_news.csv
    title: Fake and Real News Articles
---
# Assignment 8: Fake News

## Quick Facts

- __first: 2024-12-04__
- __final: 2024-12-11__



```{attention}
there are 2 deadlines for this instead of an assignment 9. This means that we will review whatever you have done by the 12/4 on 12/5-6 and then give you personalized feedback in order to finish the assignment or extend it.  
```
<!-- - First feedback: {{ early }}
__Final due date: {{ date }}__ -->

## Submission Instructions

1. Create one notebook for this assignment, `fake_or_real`
1. Export as myst markdown (by [installing jupytext](https://jupytext.readthedocs.io/en/latest/install.html) which should include [frontend features](https://jupytext.readthedocs.io/en/latest/jupyterlab-extension.html) )
1. Upload (or push) to a branch called `assignment8`
1. Open a [PR](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)


## Instructions

Use the dataset linked above to answer the following questions:

1. Is the text or the title of an article more predictive of whether it is real or fake?
1. Are titles of real or fake news more similar to one another?

The data includes three columns:
- ‘text’: contents of an article
- ‘label’: whether it is real or fake news
- 'title': title of the article



:::{tip}
Tuesday November 25 will be a problem solving session where we will discuss how to break this problem down.  You should be able to leave class with an approved outline tht will set you up to complete the assignment.  I will also provide help in planning your final portfolio submissions. 
:::


Include narrative around the code required to answer the following questions and interpret the results to give an actual answer. 
- Provide context on your answer and consider how strong it is based on what differences you can have in how you represent the data and how that might impact your model performance. 
- Consider if the analysis you have done is enough evidence answer the question from the analysis you have completed or could something else change the answer. 
- Use summary statistics and visualizations appropriately in order to explain your results.
- To earn compare, you can compare classifiers or representations, but make sure it is an appriate comparison
- If you have questions about how to work on any specific achievement post an issue on the repo


```{hint}
The data set contains a large number of articles (takes a long time to train), you can downsample this to something like a 1,000 articles or so in order to speed up training and evaluation (hint: use sample).

```

## Extension ideas


:::{note}
For each of these you need to show, in your report, *why* this works with evidence based on your data analysis. If you do steps outside the notebook (eg prompting an llm) you need to include, in a markdown cell, a detailed explanation of what you did, for example:
> I used LLMX to generate Y new articles, using the prompt <PROMPT> and ...
:::

Some ideas to earn innovative

- deepen the analysis  by breaking down the two questions above to make the more specific and detailed. For example, how much more predictive, how reliably more predictie, how sensitive to train/test split is your answer, is the more predictive model slower? if so what would be the tradeoff point? 
- stress test your model by generating additional fake news using an LLM and scraping additional, newer, high quality news articles(if possible, some news agencies are mad at LLM training procedures and have locked their content down) or using the ones in the 20 news groups dataset
- based on your analysis how could you help teach a person to spot fake news? (hint: model inspection)
- How could you get an llm to generate news articles that your classifier thinks are real? (hint: model inspection)
- how does it work if you use both the text and the title? Could you give people a simple flowchart that guides them to scan the title for things and then the article? How reliable can that be? 
- apply clustering to the data and interpret what the results would mean? Do the clusters relate to the articles being real or fake or something else?
- add quantitative outcomes computed from the text and see if that value can be predicted from the titles (even as simple as article length)

:::{note}
It is okay to use an AI to help get ideas, but **you** have to make sure your work is completely correct, AI **will** give you incorrect, at least outdated, information and code patterns, your job is to make sure that you submit something  **good**.
:::


