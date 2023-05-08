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
Here I used 4 model to predict the house prices

### 1. Simple Neural Network

* 1 hidden layer with 16 nodes
* Using **Huber loss** with alpha = 10 as loss function
* ReLU as activation function

### 2. Random Forest


### 3. XGBoost

* max_depth is 4
* learning_rate is 0.1

### 4. Gradient Boosting

* max_depth is 5
* n_estimators is 500
* learning_rate is 0.1

## Results

### Without economic index

|  | Neural Networks   | XGBoost | RandomForest | Gradient Boosting |
| :---:   | :---: | :---: | :---: | :---: |
| MAE | 110.19   | 102.55   |110.4 | 105.14 |
| MSE | 33946.54   | 27289.3   | 33964.11 | 28352.32 |
| RMSE | 184.24   | 165.19   | 184.29 | 168.38 |
| R^2 Score | 0.765   | 0.81   | 0.764 | 0.803 |

### With economic index


|  | Neural Networks   | XGBoost | RandomForest | Gradient Boosting |
| :---:   | :---: | :---: | :---: | :---: |
| MAE | 106.38   | 97.21   | 104.65 | 97.89 |
| MSE | 33414.91   | 25251.42   | 32065.77 | 25627.29 |
| RMSE | 182.79   | 158.90   |  179.06 | 160.08 |
| R^2 Score |  0.772   | 0.825   | 0.777 | 0.822 |





