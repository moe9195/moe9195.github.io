---
title: "Data Science and Machine Learning Projects"
date: 2019-12-09
tags: [data science, machine learning, deep learning, neural networks]
header:
  image: "/images/data_science_background.jpg"
excerpt: "Data Science, Machine Learning, Deep Learning, Neural Networks"
mathjax: "true"
---


## A collection of various data science and machine learning projects that I've previously worked on.

### [Diagnosing Pneumonia using Chest X-Ray Images](https://nbviewer.jupyter.org/github/moe9195/Machine-Learning-Projects/blob/master/chest_xray.ipynb)

Using chest x-ray images to diagnose pneumonia using convolutional neural networks. I implement a neural network with five hidden convolutional layers followed by a fully connected layer, which I train on 5638 labelled x-ray images. The model is then tested on a test set and had an accuracy of 84.48% 


Here's a numbered list:
1. First
2. Second
3. Third

Python code block:
```python
    import numpy as np

    def test_function(x, y):
      z = np.sum(x,y)
      return z
```

R code block:
```r
library(tidyverse)
df <- read_csv("some_file.csv")
head(df)
```

Here's some inline code `x+y`.

Here's an image:
<img src="{{ site.url }}{{ site.baseurl }}/images/perceptron/linsep.jpg" alt="linearly separable data">

Here's another image using Kramdown:
![alt]({{ site.url }}{{ site.baseurl }}/images/perceptron/linsep.jpg)

Here's some math:

$$z=x+y$$

You can also put it inline $$z=x+y$$

