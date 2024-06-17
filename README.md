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

5. Feature extraction - turned the comments into nuerical format via arrays

* vectorizer used to determine importance in words in sentence

```
from sklearn.feature_extraction.text import TfidfVectorizer
vectorizer = TfidfVectorizer(max_features=2000, min_df=2, max_df = .6) #min df = minimum number times word appears in comment to be considered important
#max_features = how many words we want to collect
#max_df = gets rid of words occuring in x% of documents

X = vectorizer.fit_transform(corpus).toarray() #comments to number

X
```
6. Trained and Tested Neural Network Model

Input:

```
pred_sample = ["I don't know maybe I might get sick with Covid..."]
pred_sample = vectorizer.transform(pred_sample).toarray()
pred_sample
```

Output: 

``` 
Results from prediction:
tensor([[-19.1400,   0.0000, -22.3309, -55.0754, -43.5176]],
       grad_fn=<LogSoftmaxBackward0>)
```
* first item in array = 0 = Extremely Negative
* Second item in array = 1 = Negative
* third item in array = 2 = Neutral
* fourth item in array = 3 = Positive
* fifth item in array = 4 = Extremely positive

* The index in array with highest value means that sentiment best labels the imput comment.

## Future Works

* Have program output the respective label for the comment being predicted for based on the array output.

## Credits

* [futureXskills](https://www.youtube.com/watch?v=Ezm0HDD-2zw&list=PLXCw5VdOQb7jqMtFIDa0T02y4zWfYvrki&index=3&ab_channel=futureXskills)

