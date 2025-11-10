
# Assignment 6: Optimizing Model Parameters

## Quick Facts
- [accept the assignment](https://classroom.github.com/a/ecryLTE8)
- __Due: 2023-11-13__



## Instructions

**summary** Extend the work you did in assignment 5 by optimizing the model parameters for the (or one of the if you worked alone) model you trained.

1. Choose your dataset, task, and a model[^model]. It can be any model we have used in class so far. Include a breif description of the task[^copydesc].
1. Fit the model with default parameters and check the score. Interpret the score in context.[^copydefault]
2. Choose reasonable model parameter values for your parameter grid by assessing how well the model fit with the default values.
3. Use grid search to find the best performing model parameters.
4. Examine the best fit model, how different is it from the default?  Score the best fit model on a held out test set.
5. Examine and interpret the cross validation results. How do they vary in terms of time? Is the performance meaningfully different or just a little?
6. Try varying the cross validation parameters (eg the number of folds and/or type of cross validation). Does this change your conclusions?

[^model]: if the model you used in Assignment 5 model does not have hyperparameters to optimize, swap in a different model. For example, use `LASSO` instead of `LinearRegression` or `DecisionTreeClassifier instead of `GaussianNaiveBayes`. You should be able to copy your previous training and only change a single line to accomodate for this. 
[^copydesc]: this can be copied from 5 if applicable or revised if you think it was vague
[^copydefault]: again, can be reused, but please do copy it in

```{tip}
this is best for regression or classification, but if you use clustering
use the `scoring` parameter to pass better metrics than the default
of the score method.
```

