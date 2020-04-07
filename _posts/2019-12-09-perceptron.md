---
title: "Data Science and Machine Learning Projects"
date: 2019-12-09
tags: [data science, machine learning, deep learning, neural networks]
header:
  image: "/images/data_science_background.jpg"
excerpt: "A collection of various data science and machine learning projects that I’ve previously worked on."
mathjax: "true"
---


## A collection of various data science and machine learning projects that I've previously worked on.

### [Covid-19 Data Dashboard](https://moe9195.github.io/covid19/#/)
Data Dashboard for visualising COVID-19 cases, with a focus on the Middle East and North Africa region. Uses [this API](https://github.com/backtrackbaba/covid-api) which uses the dataset by John Hopkins University. Data is updated daily.
<img src="{{ site.url }}{{ site.baseurl }}/images/covid19.png" alt="COVID-19 DASHBOARD">
### [Diagnosing Pneumonia using Chest X-Ray Images](https://nbviewer.jupyter.org/github/moe9195/Machine-Learning-Projects/blob/master/chest_xray.ipynb)

Using chest x-ray images to diagnose pneumonia using convolutional neural networks. I implement a neural network with five hidden convolutional layers followed by a fully connected layer, which I train on 5638 labelled x-ray images. The model is then tested on a test set and had an accuracy of 84.48% 


<img src="{{ https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia }}{{ https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia }}/images/xray.png" alt="chest x-rays">

### [Principle Component Analysis of US Senators Based on Voting Patterns](https://nbviewer.jupyter.org/github/moe9195/Machine-Learning-Projects/blob/master/US_Senate.ipynb)

I perform principle component analysis on US Senate voting patterns to identify clusters amongst US Senators. The voting history is used to compare polarization in US politics for the years 1993 to 2016. Despite the analysis being based only on roll call votes and not policy positions, clear clusters emerge from the voting data. The trend towards more polarization in Congress over the past few decades naturally forms from this analysis. Moreover, the analysis is very successful at highlighting outliers and swing voters.

 <img src="{{ site.url }}{{ site.baseurl }}/images/senate_clusters.jpg" alt="senate clusters">

### [Predicting Vorticity from Temperature and Kinetic Energy Sattelite Data using Convolutional Neural Networks](https://nbviewer.jupyter.org/github/moe9195/OceanData/blob/master/report.ipynb)

I implement a convolutional neural network which takes an input 75x75 grid of temperature or kinetic energy readings and predicts the vorticity in those regions.

The dataset used to train the network consists of CMEMS data from 1993 to 2016 of various oceans. Each 600x600 grid of data was split into 64 75x75 grids where each pixel represents 1/12 degrees as shown in the image below. The neural network is able to accurately predict regions of high vorticity from kinetic energy and temperature data.


 <img src="{{ site.url }}{{ site.baseurl }}/images/vorticity.jpg" alt="vorticity prediction">
 <img src="{{ site.url }}{{ site.baseurl }}/images/ocean_loss.jpg" alt="loss plots">
 
### [Student Performance Exploratory Data Analysis and Visualisation](https://nbviewer.jupyter.org/github/moe9195/Machine-Learning-Projects/blob/master/exam_performance.ipynb)
 
I use generated data, which includes scores from three exams and a variety of socio-economic factors to understand how these factors impact students performance.  

From the data, I am able to determine which variables have the largest impact in predicting whether a student is going to pass or fail.

 <img src="{{ site.url }}{{ site.baseurl }}/images/exams.png" alt="vorticity prediction">
 
 
 
### [Training MobileNet on the Fruits-360 Dataset](https://nbviewer.jupyter.org/github/moe9195/Machine-Learning-Projects/blob/master/fruits.ipynb)

I train the [MobileNetV2](https://arxiv.org/abs/1801.04381) network on the Fruits-360 Dataset. The [dataset](https://github.com/Horea94/Fruit-Images-Dataset) consists of 82213 images of 120 fruits and vegetables split into Training and Test sets. 

The trained network is able to achieve an accuracy of 99.1% within 50 epochs.

 <img src="{{ site.url }}{{ site.baseurl }}/images/fruits1.png" alt="class distribution">
 <img src="{{ site.url }}{{ site.baseurl }}/images/fruits2.png" alt="fruits">
 
 

