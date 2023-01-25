# Group_Project_2
 
## Project Overview

Our primary objective of the project was to create a machine learning model that effectively predicted the value of Bitcoin using a couple different machine learning libraries not previously covered in class. <br>

First, we attempted to use a library called XGBoost. Early on we ran into challenges when trying to complete the xgb.XGBRegressor() command. However, after some additional research we were able to move past that error and copmlete the model and fit component of the process. Once that was completed, we applied the details we had to calculate the mean squared error, the root mean squared error, and the r-squared. Although we did not move beyond these calculations for XGBoost, it did provide a good comparison for our alternative model, the Kernel Ridge Regression.

The Kernel Ridge Regression model we applied worked a bit better than XGBoost, and we were able to complete both the RMSE calculation as well as develop predicted prices for Bitcoin out into the future. Those predictions, compared to actual values we've seen in the last several days, appear to have under estimated the performance.<br>

## Data Gathering

We used the yfinance import to pull Bitcoin performance from December 1st, 2017 through December 31st, 2022. While pulling that data we dropped the following features: <br>

-Adjust Close<br>
-High<br>
-Low<br>

Dropping the features above and rounding the values as a part of the data pull gave us a clean dataset to work with from the start.<br>

## Overview of Models Used
### Kernel Ridge Regression 
[Overview here]<br>

### XGBoost
[Overview here]

## Developing and Running the Models
### Kernel Ridge Regression
[This is where Kernel Ridge details will go] <br>

### XGBoost 
Prior to running the library, we confirmed that the imported data did not include any null values. Not surprisingly given the data source, no null values were imported. Then, we dropped both the Open and Volume features from the dataset, leaving us with just the Date and Close price. <br>

Once we had our cleaned dataset, we developed rolling windows at 3, 7, and 30 day windows and calculated the mean. Following this step, we did shift the dataset to account for the rolling windows and the associated null values. <br>

Once we established the rolling day features, we split the training and validation data. The training data using nearly 70%, while the remaining data was used for validation. Once we split the data, we ran xgb.XGBRegressor and applied the following parameters:<br>

-Learning Rate<br>
-Max Depth<br>
-Estimators<br>
-Min Child Weight<br>
-Gamma<br>
-Subsample<br>
-Sample by Tree<br>
-Sample by Level<br>

Once we setup the parameters, we ran model.fit on the training dataset and then the following step was to use model.best_estimator_. Following those steps we calculated the mean absolute error, the root mean squared error and the correlation coefficient (r-sqaured) for both the training and test data.<br>

    Train MAE: .19
    Train RMSE: .26
    Train R2: .99

    Test MAE: 2511.70
    Test RMSE: 3201.43
    Test R2: .94

## Model Evaluation
### Kernel Ridge Regression
[This is where we will place model evaluation]<br>

## Model Comparison
### Comparison between available XGB outputs and KR