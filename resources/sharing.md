---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.17.3
kernelspec:
  display_name: rhodyds
  language: python
  name: rhodyds
---


# Sharing Models

```{code-cell} ipython3
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

```{code-cell} ipython3
corner_data = 'https://raw.githubusercontent.com/rhodyprog4ds/06-naive-bayes/f425ba121cc0c4dd8bcaa7ebb2ff0b40b0b03bff/data/dataset6.csv'
df6= pd.read_csv(corner_data,usecols=[1,2,3])
```

:::::{warning}
This page is **not** a notebook, it does not show the output of these steps, because I cannot have it authenticate to huggingface on the github action that makes the website. 
:::::::

You need to do **one** time:
```Python
from huggingface_hub import login
login()
```

## Sharing data
Then [create a repo on huggingface](https://huggingface.co/new) and set the owner to the course organization, `CSC310-fall25`.  

Then save the data (eg with `to_csv`) to a folder and upload that folder: 

So, for example, I did: 
```Python
df6.sample(50).to_csv('corners/corners.csv')
api = HfApi(token=os.getenv("HF_TOKEN"))
api.upload_folder(
    folder_path="corners",
    repo_id="CSC310-fall25/example_corners",
    repo_type="dataset",
)
```
:::::{important}
You will need to set your `folder_path` and `repo_id` to your own. 
::::


## Sharing your model
::::{note} 
If you are testing this for extra credit, you can upload any model, with a minimal model card, but for your assignment you should make sure that the model card is complete
:::::

Then create train your model, create a folder and use `skio` to dump the model parameters to a pkl file (read pickle)
```Python
local_repo = 'example_decision_tree'
with open(os.path.join(local_repo,'model.pkl'), mode="bw") as f:
    sio.dump(dt, file=f)
```

Then make a model card, but customized to your actual model: 
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

and save that to a file
```Python
model_card.save(Path(local_repo) / "README.md")
```


Also add a configuration that describes your model 
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

and finally upload the model
```Python
api = HfApi(token=os.getenv("HF_TOKEN"))
api.upload_folder(
    folder_path=local_repo,
    repo_id="CSC310-fall25/example_decision_tree",
    repo_type="model",
)
```

## Downloading and using a model

In your `eval` notebooks, you will: 
```Python
from huggingface_hub import hf_hub_download
hf_hub_download(repo_id="CSC310-fall25/example_decision_tree", filename="model.pkl",local_dir='.')
dt_loaded = sio.load('model.pkl')
```

You can confirm it works like: 
```Python
dt_loaded.score(X_test,y_test)
```
and then do the rest of your eval.  You will also need their test dataset. 


```{code-cell} ipython3
```

