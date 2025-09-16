# Assignment 1: Portfolio Setup

::::{important} Key facts

- Due: 2025-09-18
- submission in class on 9/18
:::::


## Related Notes

- [](../notes/2025-09-04.md)
- [](../notes/2025-09-09.md)
- [](../notes/2025-09-11.md) 



:::::::{important}
Remember that your code always has to adhere to the course [style guide](#style:hard). Small violations may receive a warning, but major violations will not be evaluated.  This means no progress toward your grade **and** no tips about any other errors. 
::::::::


## Setting

Next week, we are going to learn about summarizing data. In this assignment, you are going to build a small dataset about datasets. In class next week, we will combine all of your datasets about datasets together in order to be able to answer questions like:

- how much total data did you all load
- how many students picked the same dataset?
- how many total rows of data did each student load?

## Steps

### Set up your Portfolio

:::{warning}
We will submit the assignment and do these steps in class 9/18
:::

1. Create your portfolio {term}`repository` by accepting the assignment from the [course organization page](https://github.com/rhodyprog4ds) 
1. Fill in the two files in the `about` folder


### Find Datasets

Find 3 [datasets](#data:basic) of interest to you that are provided in at least two different file formats. Choose datasets that are not too big, so that they do not take more than a few second to load. At least one dataset must have non numerical (eg string or boolean) data in at least 1 column.

In a notebook called `dataset_of_datasets.ipynb`, create a markdown cell for each dataset that includes:
- heading of the dataset's name
- a 1-2 sentence summary of what the dataset contains and why it was collected
- a "more info" link to where someone can learn about the dataset
- 1-2 questions you would like to answer with that dataset.

:::::{important}
For this assignment, Kaggle and UCI datasets will not work, you **must** to be able to load the dataset from URL. We want to be able to run your submitted code, without you adding any data files to your repository. 
::::::

### Store them for loading

Create a list of dictionaries in `datasets.py`, so that there is one dictionary for each dataset. Each dictionary should have the keys specified in {ref}`dict_meta`

```{list-table} Meta Data Description of the dictionary to create
:header-rows: 0
:label: dict_meta

* - `url`
  - the full url of the dataset
* - `short_name`
  - a short name
* - `load_function`
  - (the actual function handle) what function should be used to load the data into a `pandas.DataFrame`.
```

### Make a dataset about your datasets

````{margin}
```{hint}
See the [python module docs for examples](https://docs.python.org/3/tutorial/modules.html#modules)
```
````

In a notebook called `dataset_of_datasets.ipynb`, import the list of dictionaries from the `datasets` module you created in the step above. 
Then {term}`iterate` over the list of dictionaries, and for each:  

1. load each dataset like using the function from the dictionary
1. save it to a local csv using the short name you provided for the dataset as the file name, without writing the index column to the file.
1. record attributes about the dataset as in {ref}`df_meta` in a list of lists or dictionary of lists 
1. Use that to create a [DataFrame](https://pandas.pydata.org/docs/reference/frame.html) with columns that match the rows of the following table.

::::{hint}
Use only `pandas` methods or attributes for these
::::

```{list-table} Meta Data Description of the DataFrame to build
:header-rows: 1
:label: df_meta

* - name
  - a short name for the dataset
* - source
  - a url to where you found the data
* - num_rows
  - number of rows in the dataset
* - num_columns
  - number of columns in the dataset
* - num_numerical
  - number of numerical variables in the dataset
```

### Explore Your Datasets


In a second notebook file called `exploration.ipynb`: 

For one dataset that includes nonnumerical data:
- read it in from your local csv using a relative path
- {term}`display` the header with the last 7 rows
- make a numpy array of only the numerical data and save it to a new variable (select these programmatically, without hardcoding the column names)
- was the format that the data was provided in a good format? why or why not?


For any other dataset:
- read it in from your local csv using a relative path
- {term}`display` the heading with the first two rows
- {term}`display` the datatype for each column
- Are there any variables where pandas may have read in the data as a datatype that's not what you expect (eg a numerical column mistaken for strings)? If so, investigate and try to figure out why.

For the third dataset:
- read it in from your local csv using a relative path
- display the first 3 multiples of 3 rows (eg 3,6,9) of the data for two columns of your choice


### Upload (or push) Your notebook and py files

::::{warning}
We will use class time on Sept 18 to do this
::::


Add the files to your portfolio repository. 

