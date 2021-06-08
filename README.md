# Project 1: Ames Iowa Housing dataset Analysis

### Problem Statement

Using the Ames Iowa Housing dataset to create a good model for predicting the price of homes at sale.

---

### Datasets

#### Provided Data

For this project, there are two provided datasets:

- [Trainning Data](./datasets/train.csv)
- [Testing Data](./datasets/test.csv)

The trainning data gives the house SalePrice and a lot of features such as a score for quality, a house size, etc.

The testing data gives just features for the SalePrice prediction.

These datasets were from [DSI-US-11 Project 2 Regression Challenge](https://www.kaggle.com/c/dsi-us-11-project-2-regression-challenge/data).

---

### Executive Summary

#### 1. Data Cleaning and EDA
- Import the training and the testing data
- Fill in the missing values
- Delete outliers
- Save the data as [Cleaned training data](./datasets/train_cleaned_data.csv) and [Cleaned training data](./datasets/test_cleaned_data.csv)

---

#### 2. Preproccessing and Feature Engineering
- For trying various features, make 3 different datasets
- Get dummy and label data from some categorical features
- Save the data as [Training data including dummy](./datasets/train_incl_dummy.csv) and [Testing data include dummy](./datasets/test_cleaned_data.csv)
- Log transform the 'Training data including dummy'
- Save the data as [Training data log transformed](./datasets/train_log_transformed.csv) and [Testing data log transformed](./datasets/test_cleaned_data.csv)
- Make polynomial (interactive) features with the 'Training data including dummy'
- Save the data as [Training data polynomial](./datasets/train_polynomial.csv) and [Testing data polynomial](./datasets/test_polynomial.csv)

---

#### Data Dictionary for Modeling

- This data dictionary represents the training datasets features for creating models. The testing data has the same features except for the SalePrice.
- The train_log_transformed is log-transformed on the SalePrice, the ExterQual, the GrLivArea, and the Fireplaces.

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**Overall Qual**|*integer*|train_incl_dummy, train_log_trainsformed|The evaluation for overall material and finish quality (units represent quality which range from a minimum of 1 to a maximum of 10) |
|**Gr Liv Area**|*integer*|train_incl_dummy, train_log_trainsformed|The living area square feet above ground | 
|**Garage Area**|*float*|train_incl_dummy, train_log_trainsformed|The size of garage in square feet|
|**Total Bsmt SF**|*float*|train_incl_dummy, train_log_trainsformed|Total square feet of basement area|
|**Built Year**|*integer*|train_incl_dummy, train_log_trainsformed|Original construction year|
|**Fireplaces**|*integer*|train_incl_dummy, train_log_trainsformed|The number of fireplaces| 
|**Exter Qual**|*integer*|train_incl_dummy, train_log_trainsformed|The exterior material quality (units represent quality which range from a minimum of 1 to a maximum of 4) |
|**Kitchen Qual**|*integer*|train_incl_dummy, train_log_trainsformed|Kitchen quality (units represent quality which range from a minimum of 1 to a maximum of 5)|


- The features for the regression using polynomial data are a lot, so just display 5 features highly correlated to the SalePrice.

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**Overall Qual Gr Liv Area**|*float*|train_polynomial|The interactive feature the 'Overall Qual' X the 'Gr Liv Area'|
|**Overall Qual Kitchen Qual**|*float*|train_polynomial|The interactive feature the 'Overall Qual' X the 'Kitchen Qual'| 
|**Overall Qual 1st Flr SF**|*float*|train_polynomial|The interactive feature the 'Overall Qual' X the '1st Flr SF'|
|**Overall Qual Garage Area**|*float*|train_polynomial|The interactive feature the 'Overall Qual' X the 'Garage Area'|
|**Total Bsmt SF TotRms AbvGrd**|*float*|train_polynomial|The interactive feature the 'Total Bsmt SF' X the 'TotRms AbvGrd'|
|**1st Flr SF**|*float*|train_polynomial|First Floor square feet| 
|**TotRms AbvGrd**|*float*|train_polynomial|Total rooms above grade (does not include bathrooms)|

The original data dicionary is [here](https://www.kaggle.com/c/dsi-us-11-project-2-regression-challenge/data)

---

#### 3. Modeling
- Regression using [Training data including dummy](./datasets/train_incl_dummy.csv)
- Regression using [Training data log transformed](./datasets/train_log_transformed.csv)
- Regression using [Training data polynomial](./datasets/train_polynomial.csv)
- The table below displays each r2 scores

|  | Linear Regression | Ridge Regression | Lasso Regression |
|:---------|:---------|:---------|:---------|
| Model using training data including dummy | 0.8594 | 0.8593 | 0.8594 |
| Model using training data log transformed | 0.8567 | 0.8572 | Failed to make a model |
| Model using training data polynomial | 0.9119 | 0.9128 | 0.9130 |

---

#### 4. Production Model and Insights
- The production model is a Lasso regression using [Training data polynomial]
- The model R^2 score is about 0.91.
- The model is good to predict the sale price in Ames since the R^2 score is about 0.91.
- This model can be applied to other cities similar to Ames.
- If this model would be applied to other places like New York, the model should be trained for the place's data since their city charastaristics are different.
- Neiborhood information should be important for a better model to predict house prices.
- The neiborhood data improve the model (the R^2 score is about 0.92).
- It would be better to gather more neiborhood data such as distance to a station, crime rates, etc. to create a better model.

---

#### 5. Kaggle Submissions
- Prediction with a Lasso regresssion using [Testing data including dummy](./datasets/test_incl_dummy.csv). The submission file is [submission_2](./submissions/submission_2.csv)
- Prediction with a Lasso regresssion using [Testing data polynomial](./datasets/test_polynomial.csv). The submission file is [submission_3](./submissions/submission_3.csv)
- There is a file named submission_1. This file was a mistake but it's uploaded on Kaggle, so it's kept on the directory. 
---
