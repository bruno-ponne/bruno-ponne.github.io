---
title: "Predicting the price direction of Petrobras stock - PETR4"
author: "Bruno Gasparotto Ponne - bruno.ponne@gmail.com"
layout: project
abstract: In this project, I use Random Forest and AdaBoost models to predict if a stock price will increase or decrease in the next hour based on data of the last hour. It was presented as the final paper in the Specialization Course in Machine Learning at PUC Minas University, in 2022.
image: capa05.png
---

### Introduction

The prediction of stocks' price movement is complex since price data presents high volatility and high noise levels. Nonetheless, several studies have pointed out the possibility to take advantage of market inefficiencies to predict stocks' movements. This projects uses sentiment analysis, technical indicators and other features to predict the price movement of PETR4 with two algorithms: Random Forest and Adaboost.

<br>

### Data Employed

![Data scheme - stock price prediction](/assets/data_scheme_02.png)

### Steps

1. Gathering data with the following Python libraries: yfinance, tweepy, pytrends;
2. Feature Engineering, missing data and outliers treatment
![Missing data imputation](/assets/na_imputation.png)
![Outlier treatment](/assets/outlier_treatment.png) 
3. Visualizing and getting insights from data;
![Data Visualization](/assets/PETR4_viz.png)
4. Training the models, hyperparameters tunning, backtesting and evaluation.
{: .larger-img }

<br>

### Main Learnings

- Feature Engineering, outlier treatment and imputation of missing data play an important role in the prediction task;
- Random Forest models outperformed Adaboost;
- Sentiment analysis of tweets about finance seem to improve predictions;
- At a first glance, it seems that the models are not better than choosing the price direction by chance. However, when only extreme movements are considered, the precisions are higher, providing a profit.
<br>
<br>

<div class = "github">
    <div class = "github-img">
        <img src="/assets/github-mark.png"/>
    </div>
    <div class = "github-link">
        Visit the complete project at
        <a href='https://github.com/bruno-ponne/Market-Prediction' target="_blank"> my Github repository.</a>
    </div>
</div>

