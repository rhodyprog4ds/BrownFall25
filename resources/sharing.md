---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.17.3
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---


# Sharing Models

🤗Hugging Face is the main AI/ML model sharing platform.  It is where the weights for basically all major open weight models are hosted.  

We will share our much smaller models for class using huggingface so that you get familiar with its process.  That will be the same as how you can use and contribute to any open AI/ML projects in the future.  

the `huggingface_hub` library just [reached version 1.0](https://huggingface.co/blog/huggingface-hub-v1) on October 27, 2025! So you are getting truly state of the art skills in trying out this process.  

We will use only a couple of the features here, but using it more is 


:::::{warning}
Most of the code on this page is **not** a notebook, so it does not show the output of these steps, because I cannot have it authenticate to huggingface on the github action that makes the website.   

You should still run this in a notebook
:::::::


(share:install)=
## Install tools
To do this exercise you will need to install two new packages
- [huggingface_hub](https://huggingface.co/docs/huggingface_hub/en/installation#install-with-conda) tools by 🤗huggingface for uploading
- [skops](https://skops.readthedocs.io/en/stable/installation.html) tools for managing sklearn models

Be sure to install in the same environment you do your work for class: 

:::::{tab-set}
:::{tab} Install with pip
```bash
pip install huggingface_hub skops  ipywidgets
```
:::
:::{tab} Install with conda

```bash
conda install conda-forge::skops
conda install -c conda-forge huggingface_hub
conda install -c conda-forge ipywidgets
```
:::
:::::

(sharing:login)=
## Login to Huggingface

:::::{important}
Make sure that you have joined the course organization. The join link is on the members only view of the course [github organization](https://github.com/rhodyprog4ds). If you do not see it at that page, email Dr. Brown
:::::::

You need to do **one** time per computer(this does not need to be in your submitted assignment if you have done it in class or when making up class):
```Python
from huggingface_hub import login
login()
```
When you create a token, choose the `write` tab at the top to simplify the decision instead of making a fine-grained token (the page that shows). 


:::::{important}
You need to paste the **value** of the token (a long alphanumeric string) not the *name* of the token (that you chose)
::::::::



 <!-- can [request]() and if your username matches your github handle that is in the course github organization, you'll be approved.  -->

## Create your test data and train a model
Then you'll do your regular work

```Python
# include only what you need for training
import numpy as np
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
from sklearn import tree
from sklearn.model_selection import train_test_split

# required for this process:
import os
import json
from huggingface_hub import HfApi
import skops.io as sio
from skops import card
sns.set_theme(palette='colorblind')
```


```Python
corner_data = 'https://raw.githubusercontent.com/rhodyprog4ds/06-naive-bayes/f425ba121cc0c4dd8bcaa7ebb2ff0b40b0b03bff/data/dataset6.csv'
df6= pd.read_csv(corner_data,usecols=[1,2,3])
df6_train, df6_test = train_test_split(df6)
```

::::{tip}
Above I split into train and test without separating the features and target first so that I could upload the features and target all as one dataset.  You could also upload two files
:::::::



```Python
dt =tree.DecisionTreeClassifier()
dt.fit(df6_train[['x0','x1']],df6_train['char'])
```


## Create a Repo

🤗Hugging Face also uses [repositories](https://huggingface.co/docs/hub/en/repositories) to share things. THey are git repositories that are specialized for AI and ML. In particular for large files and model weights. 


You will need to [create a model repo on huggingface](https://huggingface.co/new) and set the owner to the course organization, `CSC310-fall25`.  

or create it with code: 
```Python
api = HfApi()
api.create_repo(repo_id="CSC310-fall25/example_decision_tree",)
```

::::::{warning}
Your model *can be private* if you only want it to be visible to classmates, but the **owner must be `CSC310-fall25`** so that it is easy for us all to see. 
:::::::::::


Next create a local folder, where you will put all of the things to upload. I made one called `example_decision_tree` in the same folder as the notebook where I ran this code. 

## Prepare your Test Data

Save the test data to the folder locally

```Python
df6_test.to_csv('example_decision_tree/corners.csv')
```


## Prepare your model


Then create train your model, create a folder and use `skio` to dump the model parameters to a pkl file (read pickle). 


Save your model to the folder
```Python
local_repo = 'example_decision_tree'
with open(os.path.join(local_repo,'model.pkl'), mode="bw") as f:
    sio.dump(dt, file=f)
```



Also add a configuration that describes your model  (again you will need to customize this, this is for hat in class corners dataset)
```Python
config = {
    "sklearn": {
        "columns": [
            "x0",
            "x1",
            "char"
        ],
        "environment": [
            "scikit-learn=1.0.2"
        ],
        "example_input": {
            "x0": [
                6.14,
                2.22,
                2.27
            ],
            "x1": [
                2.2,
                2.0,
                5.9
            ],
            "char": [
                'A',
                'B',
                'A'
            ]
        },
        "model": {
            "file": "model.pkl"
        },
        "task": "tabular-classification"
    }
}
with open(os.path.join(local_repo,'config.json'),'w')as f:
    f.write(json.dumps(config))
```

## Create a Model Card
Then make a [model card](https://huggingface.co/docs/hub/en/model-cards). 

You can use `skops` to do it
```Python
model_card = card.Card(dt)
limitations = (
    "This model is made for educational purposes and is not ready to be used in"
    " production."
)
model_description = (
    "This is a Decision tree model trained on a 2D 4 corners dataset. "
)
model_card_authors = "brownsarahm "
model_card.add(
    folded=False,
    **{
        "Model Card Authors": model_card_authors,
        "Intended uses & limitations": limitations,
        "Model description": model_description,
        "Model description/Intended uses & limitations": limitations,
    },
)
```

or you can use the [huggingface tools](https://huggingface.co/docs/huggingface_hub/guides/model-cards#create-and-share-model-cards). This can be done programmatically using their web interface.  



and save that to a file
```Python
mc_path =os.path.join(local_repo, "README.md")
model_card.save(mc_path)
```


## Share your Model repo

You should now have a folder that has data, a model card


:::::{important}
You will need to set your `folder_path` and `repo_id` to your own. 
::::::::

and finally upload the model
```Python
api = HfApi(token=os.getenv("HF_TOKEN"))
api.upload_folder(
    folder_path=local_repo,
    repo_id="CSC310-fall25/example_decision_tree",
    repo_type="model",
)
```

(getmodel)=
## Downloading and using a model

In your `eval` notebooks, you will: 
```Python
from huggingface_hub import hf_hub_download
hf_hub_download(repo_id="CSC310-fall25/example_decision_tree", filename="model.pkl",local_dir='.')
dt_loaded = sio.load('model.pkl')
```

You can then use that object like any other `sklearn` estimator. 

```Python
dt_loaded.score(X_test,y_test)
```
and then do the rest of your eval.  You will also need their test dataset. 

You can download datasets just like models, but by specifying the data's file name instead of `model.pkl` above. 


::::{attention}
If you get an `InconsistentVersionWarning` error because you and the person who trained the model are different versions, that is probably okay, but if you get really low performance or errors this could also be the problem. 

You can [learn more from `sklearn` docs](https://scikit-learn.org/stable/model_persistence.html#security-maintainability-limitations)
:::::::



<!--
 ```{code-cell} ipython3
``` 
-->

