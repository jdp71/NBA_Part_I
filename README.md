# NBA Salary Predictions

## Introduction
The National Basketball Association (NBA) is a men’s professional basketball league comprised of 30 teams.  Each of these teams have multi-million dollar budgets that they use in order to build a talented team that will hopefully win enough games to bring home the NBA title.  To do this, the teams build their rosters based on talent and budget.  While team payrolls are large, they are not unlimited and strategic decisions must be made to develop the most talented team while maintaining budget constraints.  The assumption of most teams, and players as well, is that the more money a particular player demands, the better the player.  This is not always the case, however.  There are numerous instances where players have been drastically overpaid and dramatically underperformed. Conversely, there have been players that have performed well above their higher-paid counter-parts.  Ideally, there would be a mechanism where player salary could be determined by consistent player performance.  It is reasonable to assume that NBA front offices do indeed subscribe to this premise, but some player salaries would suggest otherwise.  The purpose behind this project is to use predictive analytics to predict what a player’s salary should be by looking at player statistics.

## Data Sources Used
This project uses the NBA player statistics dataset that was obtained from Kaggle and can be found [here](https://www.kaggle.com/koki25ando/salary).  The website lists the statistics as originating from 2017-2018 team rosters, but upon further verification, the rosters are more in line with 2016-2017 data.  The downloaded data contained 88 missing salary values.  All but two of these were obtained from the [HoopsHype.com](https://hoopshype.com/salaries/players/2016-2017/) website of player salaries.

## Technologies Used
* Python 3+  
* Jupyter Notebook 5.7.8  
* R 3.5.0

## Required Packages
### Python Packages
```python
import pandas as pd
from pandas import DataFrame
from sklearn import preprocessing
from collections import defaultdict
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score
from sklearn.feature_selection import RFE
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import ExtraTreesClassifier
from sklearn import preprocessing
from collections import defaultdict
from sklearn.feature_selection import SelectKBest
from sklearn.feature_selection import chi2
from sklearn.svm import LinearSVC
from sklearn.feature_selection import SelectFromModel
from functools import reduce
import numpy as np
from sklearn import model_selection
from sklearn.linear_model import LinearRegression
from sklearn.linear_model import Ridge
from sklearn.linear_model import Lasso
from sklearn.linear_model import ElasticNet
from sklearn.neighbors import KNeighborsRegressor
from sklearn.tree import DecisionTreeRegressor
from sklearn.svm import SVR
from sklearn.metrics import r2_score
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from xgboost import XGBRegressor, plot_importance
from math import sqrt
from rpy2.robjects.packages import importr
import rpy2.robjects as robjects
import rpy2.robjects.packages as rpackages
from rpy2.robjects.vectors import StrVector
```
### R Libraries
```R
library(ggplot2)
library(gridExtra)
library(grid)
library(forcats)
library(magrittr)
library(dplyr)
```

## Analysis Methods Used
* Linear Regression
* Ridge Regression
* Lasso Regression
* ElasticNet Regression
* Extreme Gradient Boosting Modeling
* Feature Selection
* Graphical Analysis

## Model Deployment
The initial linear model results were good, but we wanted to include other models to ensure that we were making the most accurate predictions possible.  Of the five models we considered, the Extreme Gradient Boosting Regression (XGBR) proved to me the most accurate.  We obtained an R2 value of 0.92 for our training subset of data.  This was about a 30% improvement over the other four models used.  

## Summary of Results
| Model | R^2 | RMSE |  
| ----- | ----- | ---- |  
| Ordinary Least Squares | 0.63 | 4398500 |  
| Ridge Regression | 0.63 | 4398504 |  
| Lasso Regression | 0.63 | 4398500 |  
| ElasticNet Regression | 0.62 | 4432638 |  
| Extreme Gradient Boosting | 0.92 | 1818766 |  

An R^2 value of 0.92 was observed for the training subset of data.  This was about a 30% improvement over the other four models used.  Also, the root mean square error (RMSE) was also significantly lower with the XGBR model.

The model was then used to predict the 10 most overpaid and 10 most underpaid players based on their performance statistics.  The following plots indicate those predictions.
