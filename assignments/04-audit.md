---
downloads:
  - file: ./data/adult_models_only.csv
    title: Model predictions on adult reconstruction
  - file: ./data/adult_reconstruction_bin.csv
    title: full dataset of adult reconstruction
---

# Assignment 4: Auditing Algorithms

Due: 2025-10-23

## Submission Instructions

1. Create one notebook for this assignment, `audits`
1. Export as myst markdown (by [installing jupytext](https://jupytext.readthedocs.io/en/latest/install.html) which should include [frontend features](https://jupytext.readthedocs.io/en/latest/jupyterlab-extension.html) )
1. Upload (or push) to a branch called `assignment4`
1. Open a [PR](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)

## About the data


We have provided a  copy of [reconstructed version](https://github.com/socialfoundations/folktables) of the [Adult](https://archive.ics.uci.edu/dataset/2/adult) Dataset, which is a popular benchmark dataset for training machine learning models that comes from a [recent paper](https://arxiv.org/abs/2108.04884) about the risks of that dataset.  The classic [Adult](https://archive.ics.uci.edu/dataset/2/adult) dataset tries to predict if a person makes more or less than 50k.  

Researchers reconstructed the Adult dataset with the actual value of the income from the original census data.  We trained models to predict `income>=$10k`, `income>=$20k` , etc.  We used three different learning algorithms, nicknamed 'LR', 'GPR', and 'RPR' for each target (`>10k`, `>20k` ,..., `>90k`).

There are two datasets you can download from this page: 
- `adult_models_only.csv` has the model's predictions 
- `adult_reconstruction_bin.csv` has the data. 


Both data files have a unique identifier column included.

```{hint}
:class: dropdown
Why might the dataset have more samples in it than the model predictions one? 
```

## Complete an audit



Thoroughly audit two randomly selected  models.  If you load the `adult_models_only.csv` to `models_df` then the following will give you replicable, but random, two columns
```
import numpy as np
my_num = # pick a number
np.random.seed(my_num)
models_to_audit = np.random.choice( models_df.columns,2)
```

In your audit, use at least three different performance metrics. Interpret all of the metrics. Compare and contrast performance in those metrics across racial or gender groups. 

Include easy to read tables and visuals with your performance metrics and interpretations of the model's overall performance and any disparities that could be understood by a general audience.  

Which of the two would you think is better to deploy? Justify your choice. 