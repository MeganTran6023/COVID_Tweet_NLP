# COVID_Tweet_NLP

## Table of Contents
* [Purpose of Program](#Purpose-of-program)  
* [Technologies](#technologies)
* [Setup](#setup)
* [Using the Program](#Using-the-Program)
* [Future Works](#Future-Works)
* [Credits](#Credits)

## Purpose of Program

This program was created to practice using PyTorch for NLP projects. In this specific project, a text classifier was made to predict whether a comment was negative or positive.


## Technologies
Languages/ Technologies used:

* Jupyter Notebook

* Python3

## Setup

Download and import the necessary libraries and packages:
```
pip install numpy
pip install pandas
pip install json
```
```
import os
import nltk
import nltk.corpus
import re

from sklearn.model_selection import train_test_split
import torch
import torch.nn as nn
from torch.nn import functional as F

import torch.optim as optim
```
Check to see if version of Python/Python3 (if on jupyter Notebook) is used, this is to ensure packages work properly. Python 3.8 or better is recommended.

```
import sys
sys.version
```

  
## Using the Program

1. Import and use file of choice

2. Since target values were strings, they had to be transformed into floats using a dictionary.

```
sentiment_labels_to_numbers = {
    "Extremely Negative" : 0,
    "Negative" : 1,
    "Neutral": 2,
    "Positive" : 3,
    "Extremely Positive" : 4
}

```
3. Original file used was too large, so subset file was created to prevent Jupyter from crashing.

4. Tokenizing and Stemming COVID tweets. This allows the model to properly identify important word(s) that influences its assigned sentiment label when learning from the training dataset.
<img width="650" alt="image" src="https://github.com/MeganTran6023/COVID_Tweet_NLP/assets/68253811/910f6e88-bd65-41fd-9e5a-6b77efa09e16">



## Future Works

* Have program output the respective label for the comment being predicted for based on the array output.

## Credits

* [futureXskills](https://www.youtube.com/watch?v=Ezm0HDD-2zw&list=PLXCw5VdOQb7jqMtFIDa0T02y4zWfYvrki&index=3&ab_channel=futureXskills)

