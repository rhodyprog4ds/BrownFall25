# Glossary



```{glossary}

accuracy
: percentage of correct predictions

aggregate
:  to combine data in some way, a function that can produce a customized summary table
: [more](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.core.groupby.DataFrameGroupBy.aggregate.html#pandas.core.groupby.DataFrameGroupBy.aggregate)

anonymous function
:  a function that's defined on the fly, typically to lighten syntax or return a function within a function. In python, they're defined with the {term}`lambda` keyword.
:  [docs](https://en.wikipedia.org/wiki/Anonymous_function#:~:text=Anonymous%20functions%20are%20often%20arguments,than%20using%20a%20named%20function)

balanced dataset
:  when the {term}` <class>` are equally or close to equally well represented


BeautifulSoup
:  a python library used to assist in web scraping, it pulls data from html and xml files that can be parsed in a variety of different ways using different methods.
: [docs](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)


cast
:  convert a variable from one type to another. in Python, done by using the constructor method of the object type or builtin function for builtin types

categorical variable
:  a variable that represents a quantity with discrete outcomes

classification
:  a type of machine learning where a {term}`categorical` {term}`target` variable is predicted from {term}`features <feature>`

class
:  a value of the {term}`target` variable

cluster
:  a group of samples that is similar by some definition

clustering
:  a type of {term}`unsupervised learning` that finds groups or clusters among the samples

conditional 
:  a logical control to do something, conditioned on something else, for example `if`, `elif`, `else` 

confusion matrix
:  counts the number of samples of each *actual* category that were *predicted$ to be in each category for every pair of categories.  For a two class(binary) problem, the table has 4 outcomes: {term}`true positive`, {term}`false positive`, {term}`false negative` and {term}`true negative`

continuous variable
:  a value that represents a smoothly varying quantity 
:  or that is best approximated as such; for example an integer value with a large range may be best modeled as continuouse and post-processed by rounding

corpus
:  (NLP) a set of documents for analysis 

cross validation
:  repeated measures of the model's performance in order to get a better estimate of performance or optimize {term}`hyperparameters <hyperparameter>`

[DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html)
:  a data structure provided by pandas for tabular data in python.

data leakage
:  data from the test set is used in training and then falsely improves the test performance

dictionary
:  (data type) a mapping array that matches keys to values. [doc](https://docs.python.org/3/glossary.html#term-dictionary)
:   (in NLP) all of the possible tokens a model knows

discriminative model
:  a model that describes the decision rule for labeling a sample as one class or another

display
:  in jupyter notebooks, an HTML rendering of the output of a cell

document
:  unit of text for analysis (one sample). Could be one sentence, one paragraph, or an article, depending on the goal


error bars
:  typically vertical, but sometimes also horizontal lines on a point in a line graph or bar in  bar chart that indicate the spread of the samples used to create that point or bar height

estimator object
:  the `sklearn` class that all {term}`model` objects inherit from
:  an object that has `fit`, `predict`, and `score` methods among other common ones

false negative
:  items in the positive class that were predicted in the negative class 
:  items incorrectly predicted as members of the negative class

false negative rate
:  the percentage of actual positive items that were incorrectly classified
:  $FNR = \frac{FN}{P}$ for $FN$ {term}`false negatives <false negative>` and $P$ actual positive items. 

false positive
:  items in the negative class that were predicted in the postive class 
:  items incorrectly predicted as members of the positive class


feature
:  an input variable in a prediction algorithm
:  an independent variable

fold
:  a chunk of the data (split row-wise) used in {term}`cross validation`

generalize
:  to describe previously unseen data, solving related, but not in the training data problems

generative model
:  a model that describes the data and therefore can also be used to generate new data that looks like the training data. 

gh 
:  GitHub's command line tools

git
:  a version control tool; it's a fully open source and always free tool, that can be hosted by anyone or used without a host, locally only.

GitHub
:  a hosting service for git repositories

hyperparameter
:  parameters of the learning *algorithm* that are set by the user and possibly optimized over in an outer loop; in `sklearn` these are set when instantiating the estimator object

index
:  (verb) to index into a data structure means to pick out specified items, for example index into a list or a index into a data frame. Indexing usually invovlees square brackets `[]`
:  (noun) the index of a dataframe is like a column, but it can be used to refer to the rows. It's the list of names for the rows.

interpreter
:  the translator from human readable python code to something the computer can run.  An interpreted language means you can work with python interactively

iterate
: To do the same thing to each item in an {term}`iterable` data structure, typically, an iterable type. Iterating is usually described as iterate over some data structure and typically uses the `for` keyword


iterative
:  a property of an algorithm that means that it involves solving a problem by repeating a set of steps until a {term}`stopping criterion` is met or over a number of steps

iterable
:  any object in python that can return its members one at a time. The most common example is a list, but there are others.
:  [docs](https://docs.python.org/3/glossary.html#term-iterable)

kernel
:  in the jupyter environment, [the kernel](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html#kernel) is a language specific computational engine

Kfold cross validation
: splitting the data into `K` sections, each called a {term}`fold` training on `K-1` and scoring on the last one, repeating `K` times so that each sample is used for testing one time. 

lambda
:  the keyword used to define an anonymous function; lambda functions are defined with a compact syntax `<name> = lambda <parameters>: <body>`
: [docs](https://docs.python.org/3.9/reference/expressions.html#lambda)

learning algorithm
:  an algorithm that finds patterns in data
:  implemented in the `fit` method in `sklearn`

location parameter
:  parameter of a distribution that controls where it is spatially. e.g. mean in a Gaussian

mask
:  take a subset using booleans; False values are dropped and True are kept
:  like multiplying by an array with 0 and 1s in it. 

metric
:  (in ML) a score that measures the quality of a model's predictions

model
:  (general) the set of assumptions, the simplification of the world 
:  (statistics) a mathematical simplification of the world in probabilistic terms

numpy array 
:  a type provided by numpy to represent matrices, used by `pd.DataFrame.values` [doc](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.values.html) and accessed by `pd.DataFrame.to_numpy` [doc](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_numpy.html#pandas.DataFrame.to_numpy)
:  [](xref:numpy#reference/arrays.ndarray)

objective function
:  a function that describes how much errors should be penalized

overfitting
:  when a model fits the training data much better than the test set, it has fit the noise in the training data instead of the core underlying pattern
: a model that does not {term}`generalize` well

parameter
:  (general programming) all inputs to a function
:  (in ML) the values that transform a generic function into a specific function

partition
:  a subset of samples

partitioning
:  a splitting of samples

PEP 8
:  [Python Enhancement Proposal](https://www.python.org/dev/peps/) 8, is the Style Guide for Python Code.
:  [pep 8 ](https://www.python.org/dev/peps/pep-0008/pep-0008/)

precision
:  the percentage of positive predictions that were actually members of the positive class  $P = \frac{TP}{PP}$ for $TP$ True positives and $PP$ positive predictions
:  For a {term}`confusion matrix`, $C$ as sklearn:  $ P = \frac{C_{1,1}}{C_{0,1} + C_{1,1}}$
: also called the positive predictive value

prediction
:  the estimated value of the {term}`target` variable for a sample based on what was learned
: the output of the {term}`prediction algorithm`

prediction algorithm
: an algorithm that takes an input and predicts the output value. 

recall
:  the percentage of the actual positives that were predicted as the positive outcomes. $R = \frac{TP}{P}$ for $TP$ True positives and $P$ items in the positive class
:  For a {term}`confusion matrix`, $C$ as sklearn: $R = \frac{C_{1,1}}{C_{1,0} + C_{1,1}}$

regression
: {term}`supervised learning` that predicts a continuous valued output

repository
:  a project folder with tracking information in it in the form of a .git file

residual
:  error in regression predictions; the amount of variance that is left unexplained by the predictive model

scale parameter
:  a parameter of a distribution that controls its width. e.g. variance in a Guassian

schema
:  (formal)a description of how a database is set up
:  (informal) a description of what different columns in a data set mean 

Series
:  a data structure provided by pandas for single columnar data with an index.  Subsetting a Dataframe or applying a function to one will often produce a Series
:  [docs](xref:pandas#pandas.Series)

shape
:  of a dataframe, or matrix is the number of rows and columns. 

side effect
:  an action that occurs in a function (like printing or writing a file) other than it returning a vlaue

silhouette score
: a score for clustering that captures how compact and separate the clusters are

slice
:  a subset of an iterable item based on the start, stop, and step
:  implemented by the [slice](https://docs.python.org/3/library/functions.html#slice) built in

Split Apply Combine
:  a paradigm for splitting data into groups using a column, applying some function(aggregation, transformation, or filtration) to each piece and combinging in the individual pieces back together to a single table
:  [pandas guide](https://pandas.pydata.org/pandas-docs/stable/user_guide/groupby.html#group-by-split-apply-combine)

stop words
:  Words that do not convey important meaning, we don’t need them (like a, the, an,). Note that this is context dependent. These words are removed when transforming text to numerical representation

stopping criterion
:  a condition that will terminate an algorithm. typically a value meeting a threshold

suffix
:  additional part of the name that gets added to end of a name in a merge operation

supervised learning
: a type of machine learning that requires both features and target variables at time of training
:  machine learning with labeled examples

target
:  the output of a prediction algorithm
:  also called the dependent variable or label

test accuracy
:  percentage of predictions that the model predict correctly, based on held-out (previously unseen) test data

test data
:  data that was not used in training that is instead used to evaluate the perforance of a model 

Tidy Data Format
: Tidy data is a database format that ensures data is easy to manipulate, model and visualize. The specific rules of Tidy Data are as follows: Each variable is a column, each row is an observation, and each observable unit is a table.
:  [original paper](https://www.jstatsoft.org/article/view/v059i10)

token
:  a sequence of characters in some particular document that are grouped together as a useful semantic unit for processing (typically a word, but more gneeral)

TraceBack
:  an error message in python that traces back from the line of code that had caused the exception back through all of the functions that called other functions to reach that line. This is sometimes call tracing back through the stack

training accuracy
:  percentage of predictions that the model predict correctly, based on the training data

training algorithm
:  another namde for {term}`learning algorithm`

training data
:  data used to fit the model to the specific domain or problem, provided to the {term}`learning algorithm`
:  the data used to find patterns and determine parameter values that will work for the problem at hand

transpose
:  swap the rows and columns of a matrix or dataframe

true negative
:  items in the negative class that were predicted in the negative class 
:  items correctly predicted as members of the negative class

true positive
:  items in the positive class that were predicted in the postive class 
:  items correctly predicted as members of the positive class

unsupervised learning
: a type of machine learning that does not use target variables at learning (fit) time. 
: machine learning from unlabeled examples

validation accuracy
: the percentage of the validation data that the model predictions were correct for. 

validation data
:  data for {term}`hyperparameter` optimization
:  used for testing in progress of development, not it the learning algorithm, but the model may be changed based on the performance on this set of data

Web Scraping
:  the process of extracting data from a website. In the context of this class, this is usually done using
:  the python library beautiful soup and a html parser to retrieve specific data.
```
