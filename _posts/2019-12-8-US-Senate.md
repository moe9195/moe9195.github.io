---
title: "US Senate"
date: 2019-12-8
tags: [data wrangling, data science, messy data]
header:
  image: "/images/perceptron/percept.jpg"
excerpt: "Data Wrangling, Data Science, Messy Data"
mathjax: "true"
---


```python
import csv, os, re
import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA, TruncatedSVD
import matplotlib.pyplot as plt
```


```python
def numericalSort(list):
    def key(value):
        numbers = re.compile(r'(\d+)')
        parts = numbers.split(value)
        parts[1::2] = map(int, parts[1::2])
        return parts
    return sorted(list, key=key)

year = 1993
path = './data/data/'
plt.figure();
plt.figure(figsize=(40,40));
plt.xticks(fontsize=12);
plt.yticks(fontsize=14);
plt.xlabel('Principal Component - 1',fontsize=20);
plt.ylabel('Principal Component - 2',fontsize=20);
for filename in numericalSort(os.listdir(path)):
    df = pd.read_csv(path+filename, sep=',')
    if 'name' not in df.columns:
        df = pd.read_csv(path+filename, sep=',', header=1)
    df.set_index('name', inplace=True)
    df = df.drop(df.columns[0], axis=1)
    names = df.index.values
    parties = df['party'].values
    df = df.replace([True, False], [1, 0])
    del df['party']
    x = df.to_numpy()
    x = StandardScaler().fit_transform(x)
    pca = PCA(n_components=2)
    principalComponents = pca.fit_transform(x)

    print('Explained variation per principal component: {}'.format(pca.explained_variance_ratio_))
    print('PCA holds '+str(round(100*np.sum(pca.explained_variance_ratio_),2))+
                          '% of the information. '+ str(round(100*(1-
                           np.sum(pca.explained_variance_ratio_)),2))+'% is lost')
    plt.title("Principal Component Analysis of U.S Senator Voting Record "+str(year),fontsize=20)

    x1 = principalComponents[:,0]
    x2 = principalComponents[:,1]
    labels = names + ' (' + parties +')'

    plt.scatter(x1, x2, s=50);
    for i, txt in enumerate(labels):
        plt.annotate(txt, (x1[i], x2[i]));
    plt.savefig('PCA '+str(year)+'.png');
    plt.clf();
    year+=1
    
```

    Explained variation per principal component: [0.3631718  0.04068121]
    PCA holds 40.39% of the information. 59.61% is lost
    Explained variation per principal component: [0.28579626 0.04702635]
    PCA holds 33.28% of the information. 66.72% is lost
    Explained variation per principal component: [0.38998621 0.02882016]
    PCA holds 41.88% of the information. 58.12% is lost
    Explained variation per principal component: [0.40293948 0.30686564]
    PCA holds 70.98% of the information. 29.02% is lost
    Explained variation per principal component: [0.32706887 0.04287145]
    PCA holds 36.99% of the information. 63.01% is lost
    Explained variation per principal component: [0.34018263 0.04830591]
    PCA holds 38.85% of the information. 61.15% is lost
    Explained variation per principal component: [0.43556697 0.04745869]
    PCA holds 48.3% of the information. 51.7% is lost
    Explained variation per principal component: [0.32592049 0.05946762]
    PCA holds 38.54% of the information. 61.46% is lost
    Explained variation per principal component: [0.39078203 0.03203727]
    PCA holds 42.28% of the information. 57.72% is lost
    Explained variation per principal component: [0.23457801 0.12038355]
    PCA holds 35.5% of the information. 64.5% is lost
    Explained variation per principal component: [0.42624339 0.13973488]
    PCA holds 56.6% of the information. 43.4% is lost
    Explained variation per principal component: [0.32234444 0.15906849]
    PCA holds 48.14% of the information. 51.86% is lost
    Explained variation per principal component: [0.41472449 0.04823107]
    PCA holds 46.3% of the information. 53.7% is lost
    Explained variation per principal component: [0.35607981 0.06719286]
    PCA holds 42.33% of the information. 57.67% is lost
    Explained variation per principal component: [0.19845758 0.12285288]
    PCA holds 32.13% of the information. 67.87% is lost
    Explained variation per principal component: [0.31488861 0.1489245 ]
    PCA holds 46.38% of the information. 53.62% is lost
    Explained variation per principal component: [0.50230131 0.15946146]
    PCA holds 66.18% of the information. 33.82% is lost
    Explained variation per principal component: [0.43738389 0.05870191]
    PCA holds 49.61% of the information. 50.39% is lost
    Explained variation per principal component: [0.34757911 0.05000554]
    PCA holds 39.76% of the information. 60.24% is lost
    Explained variation per principal component: [0.34214318 0.1071864 ]
    PCA holds 44.93% of the information. 55.07% is lost
    Explained variation per principal component: [0.40345005 0.06096851]
    PCA holds 46.44% of the information. 53.56% is lost
    Explained variation per principal component: [0.36678191 0.04910385]
    PCA holds 41.59% of the information. 58.41% is lost
    Explained variation per principal component: [0.46007781 0.06580662]
    PCA holds 52.59% of the information. 47.41% is lost
    Explained variation per principal component: [0.26333024 0.13378809]
    PCA holds 39.71% of the information. 60.29% is lost



    <Figure size 432x288 with 0 Axes>



    <Figure size 2880x2880 with 0 Axes>



```python
path = './data/data/'

df_merged=pd.read_csv(path+'senate114_2.csv', sep=',')
df_merged.set_index('name', inplace=True)
df_merged = df_merged.drop(df_merged.columns[0], axis=1)


for filename in os.listdir(path):
    df = pd.read_csv(path+filename, sep=',')
    if 'name' not in df.columns:
        df = pd.read_csv(path+filename, sep=',', header=1)
        
    df.set_index('name', inplace=True)
    df = df.drop(df.columns[0], axis=1)
    df_merged = pd.merge(left=df_merged, right=df, left_on='name', right_on='name')
    #df_merged = pd.concat([df_merged, df], axis=1)
    
names = df_merged.index.values
parties = df_merged['party_y'].values[:,2]
df_merged = df_merged.replace([True, False], [1, 0])
del df_merged['party_y']
del df_merged['party_x']
x = df_merged.to_numpy()
x = StandardScaler().fit_transform(x)



```


```python
def numericalSort(list):
    def key(value):
        numbers = re.compile(r'(\d+)')
        parts = numbers.split(value)
        parts[1::2] = map(int, parts[1::2])
        return parts
    return sorted(list, key=key)

numericalSort(os.listdir(path))

#for filename in os.listdir(path)
#    print(filename)
```


```python
pca = PCA(n_components=2)
principalComponents = pca.fit_transform(x)

print('Explained variation per principal component: {}'.format(pca.explained_variance_ratio_))
print('PCA holds '+str(round(100*np.sum(pca.explained_variance_ratio_),2))+
                          '% of the information. '+ str(round(100*(1-
                           np.sum(pca.explained_variance_ratio_)),2))+'% is lost')
                          


```


```python
plt.figure()
plt.figure(figsize=(40,40))
plt.xticks(fontsize=12)
plt.yticks(fontsize=14)
plt.xlabel('Principal Component - 1',fontsize=20)
plt.ylabel('Principal Component - 2',fontsize=20)
plt.title("Principal Component Analysis of U.S Senator Voting Patterns",fontsize=20)

x1 = principalComponents[:,0]
x2 = principalComponents[:,1]
labels = names + ' (' + parties +')'

plt.scatter(x1, x2, s=50);
for i, txt in enumerate(labels):
    plt.annotate(txt, (x1[i], x2[i]))

plt.savefig('PCA(2011-2016).png')


```


```python










```
