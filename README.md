# Bike Rental Dataset Prediction

**Simple bike-sharing prediction project created with data manipulation and machine learning libraries of Python.**

This project consists of three files which are as follows:

- **Code script file** with the data visualization and step by step working

- **Function file** which is the automated code script

- **Azure file**- This project is implemented in Azure ML Studio as well, so screenshots of the model built on Azure are also attached.


# Table of Contents 

- **1.  Loading libraries**

- **2.  Introduction**

   - *2.1 Exploring the data*
   
- **3.  Exploring data analysis**

   - *3.1   Describing features*
  
   - *3.2   Exploratory Data analysis*
   
       - 3.2.1.Distribution Plot
       
       - 3.2.2. Box Plot
       
       - 3.2.3. Outlier Detection
       
       - 3.2.4. Correlation Matrix
    
- **4.  Split the data into train and test sets**

- **5. Fitting baseline model.**

- **6.  Check for multicollinearity**

- **7.  Fitting the improvised models**

   - *7.1 Linear Regression*
   
   - *7.2 RandomForest Regressor*

- **8.  Checking for the important features.**


# 2.Introduction

**About the project**- Bike-sharing systems are a new generation of traditional bike rentals where the whole process from membership, rental, and the return has become automatic. Through these systems, the user can easily rent a bike from a particular position and return to another position. Currently, there are about over 500 bike-sharing programs around the world which are composed of over 500 thousand bicycles. Today, there exists a great interest in these systems due to their important role in traffic, 
environmental and health issues. 

Apart from interesting real-world applications of bike-sharing systems, the characteristics of data being generated by
these systems make them attractive for the research. Opposed to other transport services such as bus or subway, the duration
of travel, departure, and arrival position is explicitly recorded in these systems. This feature turns the bike-sharing system into
a virtual sensor network that can be used for sensing mobility in the city. 

**Feature characteristics**

day.csv has the following fields
- instant: record index
- dteday : date
- season : season (1:springer, 2:summer, 3:fall, 4:winter)
- yr : year (0: 2011, 1:2012)
- mnth : month ( 1 to 12)
- holiday : weather day is holiday or not (extracted from http://dchr.dc.gov/page/holiday-schedule)
- weekday : day of the week
- workingday : if day is neither weekend nor holiday is 1, otherwise is 0.
+ weathersit : 
    - 1: Clear, Few clouds, Partly cloudy, Partly cloudy
    - 2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist
    - 3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds
    - 4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog
- temp : Normalized temperature in Celsius. The values are divided to 41 (max)
- atemp: Normalized feeling temperature in Celsius. The values are divided to 50 (max)
- hum: Normalized humidity. The values are divided to 100 (max)
- windspeed: Normalized wind speed. The values are divided to 67 (max)
- casual: count of casual users
- registered: count of registered users
- cnt: count of total rental bikes including both casual and registered


**Aim of the project**- This project aims to predict the bike rental count daily based on the environmental and seasonal settings.


# 3. Launch

## 3.1. Technologies 

**1.Python**- Python programming language is utilized as a standalone base to solve the purpose of the project.

**2.Jupyter IDE**- Jupyter is utilized as a platform to write code scripts in python and do the data pre-processing, visualization, and Machine Learning tasks.

**Pandas**- Pandas library in python is put to use for data manipulation and analysis.

**3.NumPy**- NumPy library of python is used for statistical purposes and also for making use of multidimensional arrays.

**4.Matplotlib**-This library of python is used for data visualization.

**5.seaborn**- This library of python is used for data visualization.

**6.scikit-learn**- The sklearn library is used for building Machine learning models like Linear regression and RandomForest Regressor. It also gives the functionality of splitting the data into train and test sets and is useful for calculating the statistical scores like RMSE, accuracy score, and Mean absolute error. Lastly, its functionality also extends to assisting in finding multicollinearity and doing cross-fold validation.

## 3.2. Launch

### 3.2.1. Setup

To run the code script please follow the steps below.

1.Install Anaconda(64-bit graphical installer version, if not previously installed), it can be installed via https://www.anaconda.com/products/individual

2.Launch Jupyter Notebook(version 6.0.3) from the anaconda navigator page or it can be directly launched from the terminal if Anaconda is previously installed(in case of MacBook).

3.Download the code script from this GitHub repository and save it in your working directory of Jupyter notebook. Alternatively, the code script can be uploaded directly in the jupyter notebook.

4.The required dataset 'day.csv' also needs to be uploaded in the current working directory of jupyter.

5.Install the libraries pandas, NumPy,scikit-learn,matplotlib, seaborn, and statsmodels if not previously installed.

6.Import the list of libraries below.

### 3.2.2.Detailed list of libraries

All the libraries mentioned below are a prerequisite to run the project.

import pandas as pd
import numpy as np
import scipy as sp
from numpy import mean
from numpy import std
import matplotlib.pyplot as plt
import matplotlib.cm as cm
import seaborn as sns
%matplotlib inline
from sklearn import model_selection
from sklearn import preprocessing
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split as sklearn_train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import r2_score, mean_squared_error, mean_absolute_error
from statsmodels.stats.outliers_influence import variance_inflation_factor
from sklearn.model_selection import KFold
from sklearn.model_selection import cross_val_score
import statsmodels.api as sm

### 3.2.3. Importing the dataset

The dataset 'day.csv' needs to be imported using the command (daydata=pd.read_csv('day.csv')).This file format has to be in .csv format.


# 4. Project Overview

**Exploring the data**- In this section descriptive statistics have been performed to understand the nature of the data and to analyze its shape and if it consists of any missing values.

**Exploratory data analysis(EDA)**- EDA is performed via distribution plots, box plots, and correlation matrix to understand the distribution of the data and to check if there exist any outliers and the correlation of variables with each other.

**Modelling**- Data is then split into train and test sets with 75% into the train set and 25% into the test set. After this, the data is scaled and a baseline linear regression model is fitted to check the performance. Moreover, multicollinearity is removed and linear regression and Random Forest Regressor is fitted to the data, and scores are analyzed. Lastly, OLS(Ordinary least squares) linear model is fitted to check the p-values of the important features.

**Results**- 1. The most important factors which influence the renting of bike count as per the analyzed data are:

 - year
 - month
 - holiday
 - weekday
 - temp 
 - windspeed

2. The baseline model gives similar results to that of the model after removing multicollinearity which indicates that multicollinearity does not affect the prediction here.

3. Using the baseline model and two different improvised models that is Linear Regression and Random Forest Regressor, the latter fits the data 6.6% better and has predicting ability with fewer errors via RandomForest Regressor. We have achieved 17.24% efficiency in RMSE and 26.78% efficiency in MAE by using the RandomForest Regressor.

4. Using Random Forest Regressor we would better be able to predict the daily rental count of the bikes.

# 5. Azure Machine Learning Studio

This project was implemented on Azure ML Studio and a pdf file in regards to it showing the work process has been attached in this repository. This pdf file consists of the following contents:


1. Creating an Azure ML workspace
2. Creating Compute instance
3. Creating Compute cluster
4. Creating Inference cluster
5. Uploading bike data to Azure cloud
6. Setup and run Auto ML
7. Make ML pipeline on Azure Designer
8. Set up model for deployment



# Example of use

1.This prediction model can be utilized for predicting the bike rental count daily and hourly.

2.It can also be put into use for predicting the car rental count daily and hourly.



# Project Status

This project is developed.


# References

1.UCI Machine Learning Repository.Retrieved from https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset

2.Cross-validation with linear regression. Retrieved from https://www.kaggle.com/jnikhilsai/cross-validation-with-linear-regression

3.Code methodologies adopted from the DSDJ-Kyle McKiou team.

