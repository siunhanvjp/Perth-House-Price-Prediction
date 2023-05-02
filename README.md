# Perth House Price Prediction

*note* : *This starts out as a group project for Data Mining class but I made some modification with this version.*

## Goals

Perform some basic EDA and try to predict a house price based on several features and we try to incorporate with some economic index to improve the result.

## Data

The house dataset is taken from __[Perth House Prices](https://www.kaggle.com/datasets/syuzai/perth-house-prices)__ on Kaggle.

This data was scraped from http://house.speakingsame.com/ and includes data from 322 Perth suburbs, resulting in an average of about 100 rows per suburb and nearly 34,000 houses.

The economic index is taken from __[The World Bank](https://data.worldbank.org/country/AU)__, the dataset contain several economic indicators from 1960 to 2020 of Australia.

## Preprocessing

### a) Perth House Dataset
For the house dataset, I only take into account numeric features (age, bathrooms, bedrooms, etc.) and Suburb name of which the house belong to because during EDA process, I find out the location of the house has effect on the price.

For the features **School_Rank**, I decide to drop it because there are a lot of missing values. This is due to the fact that each school is ranked based on the ATAR system schools which do not have an ATAR program such as primary schools, vocational schools, special needs schools etc. are not considered.

### b) Economic Dataset
I only consider some economic indicators which can indirectly affect the housing market of Australia.

* FP.CPI.TOTL.ZG - Inflation rate
* FR.INR.LEND _ Interest rate
* SP.POP.GROW _ Population growth
* SL.UEM.TOTL.NE.ZS _ Unemployment

The **Inflation rate** will be used to scaled the price of the house from when it was sold to the current year.

## Method
Here I used 3 model to predict the house prices

### 1. Simple Neural Network

* 1 hidden layer with 16 nodes
* Using **Huber loss** with alpha = 10 as loss function
* ReLU as activation function

### 2. Random Forest

* n_estimators is 20

### 3. XGBoost

* max_depth is 5
* n_estimators is 300

## Results

### Without economic index

|  | Neural Networks   | XGBoost | RandomForest |
| :---:   | :---: | :---: | :---: |
| MAE | 71.22   | 67.79   | 73.90 |
| MSE | 10732.60   | 9671.28   | 11785.70 |
| RMSE | 103.59   | 98.34   | 108.56 |
| R^2 Score | 0.78   | 0.80   | 0.76 |

### With economic index

|  | Neural Networks   | XGBoost | RandomForest |
| :---:   | :---: | :---: | :---: |
| MAE | 68.93   | 64.19   | 71.63 |
| MSE | 10265.55   | 9018.7   | 11570.6 |
| RMSE | 101.32   | 94.97   | 107.57 |
| R^2 Score | 0.79   | 0.82   | 0.77 |

## Future Work

* Find out better way to handle outlier than just dropping it

* Tune hyperparameter to produce more accurate result

* Perform clearly EDA


