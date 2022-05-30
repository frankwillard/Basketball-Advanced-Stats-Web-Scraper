# Basketball-Advanced-Stats-Web-Scraper

This is my attempt at using my machine learning skill set to predict the 2022 Champion. All work was done before the playoffs to ensure an unbiased prediction.

<br/>

## Part 1) Web Scraping

Web scraper developed by adapting scripts from [Medium Basketball Reference Article](https://medium.com/analytics-vidhya/intro-to-scraping-basketball-reference-data-8adcaa79664a) based on knowledge of Python, pandas, web scraping. 

Pulled Advanced Basketball Stats from years 1990-2020 from links in format:
https://www.basketball-reference.com/leagues/NBA_{year}.html (Example: https://www.basketball-reference.com/leagues/NBA_2021.html)

A testing dataset was then collected using data from the NBA 2022 regular season. 

In scraping the dataset, several variables were feature engineered from the Basketball Reference data including won_last and won_last_3 (lag features of previous championships in the last 1 and 3 years respectively), Win Loss Percentage (as several seasons varied in length due to lockout such that it is a better predictor of regular season performance)

A further explanation of the variables collected in the dataset can be found in the [Data Dictionary](https://github.com/frankwillard/NBA-Web-Scraper-And-ANN/blob/main/data/Data%20Dictionary.md).

<br/>

## Part 2) Exploratory Data Analysis

Exploratory data analysis of the dataset can be found in the eda folder, featuring various plots of variables in the dataset in R. 

[Link To EDA Code](https://github.com/frankwillard/NBA-Web-Scraper-And-ANN/blob/main/eda/Basketball_EDA.rmd)

[Link to PDF of Visualizations](https://github.com/frankwillard/NBA-Web-Scraper-And-ANN/blob/main/eda/Basketball_EDA.pdf)

<br/>

## Part 3) Data Cleaning, Modeling, and Prediction

All teams that did not make the playoffs were not included in the model in order to prioritize differentiating top-level teams from each other.

### Approach 1: Artificial Neural Network

Using an Artificial Neural Network in TensorFlow with Batch Normalization, Dropout, and several class imbalance techniques including oversampling, we then developed a model using the training data and predicted on the 2022 testing data. 

Early stopping was used in order to reduce the possibility of overfitting and use the weights that produce the optimal validation PR curve, or rather combination of precision (how many predictions were truely Champion) and recall (how many Champions were identified by model). 

The model predicts the Phoenix Suns and the Golden State Warriors as the likely teams to win the 2022 championship (highest output scores from ANN), with the Suns having the highest log-odds, such that they are the model's predicted champion. 

The visualizations and class imbalance techniques used in the ANN Notebook are based on the [TensorFlow Core Tutorial on Working with Class Imbalance](https://www.tensorflow.org/tutorials/structured_data/imbalanced_data)

<br/>

### Approach 2: Decision Tree

Decision Trees are known to be effective at dealing with imbalanced data. Thus, after optimizing the hyperparameters of a decision tree via grid search, a decision tree was used to predict on the 2022 testing data. The model predicts the Phoenix Suns to win the championship.
