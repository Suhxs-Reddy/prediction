# Walmart Sales Prediction

This repository contains code for building predictive models to estimate weekly sales for Walmart departments. The goal is to forecast future sales based on historical data, store features, and additional external variables like temperature, fuel prices, and markdowns.

---

## Table of Contents

1. [Dataset Description](#dataset-description)
2. [Methodology](#methodology)
   - [Data Cleaning](#data-cleaning)
   - [Data Integration](#data-integration)
   - [Data Visualization](#data-visualization)
   - [Time Series Decomposition](#time-series-decomposition)
   - [Data Transformation & Reduction](#data-transformation--reduction)
   - [Data Splitting](#data-splitting)
3. [Modeling](#modeling)
4. [Model Performance](#model-performance)

---

## Dataset Description

The dataset is composed of the following files:

- **stores.csv**: Contains information about 45 Walmart stores, such as store type, size, and other features.
- **train.csv**: Contains historical sales data, including store number, department number, date, weekly sales, and holiday flag.
- **test.csv**: Similar to `train.csv`, but with sales values withheld for prediction.
- **features.csv**: Includes additional store features like:
  - Temperature
  - Fuel prices
  - Promotional markdowns
  - Consumer Price Index (CPI)
  - Unemployment rate

### Holidays:
The dataset includes sales data around the following holidays:
- Super Bowl
- Labor Day
- Thanksgiving
- Christmas

### Evaluation Metric:
The model performance is evaluated using **Weighted Mean Absolute Error (WMAE)**, with holiday weeks given 5 times more weight than non-holiday weeks.

---

## Methodology

### Data Cleaning
To ensure accurate analysis, several data preprocessing steps are followed:
- **Missing Values**: Missing data is imputed to maintain the integrity of the dataset.
- **Date Parsing**: The date column is parsed into separate components (year, month, day) to enable better temporal analysis.
- **Outlier Detection**: Outliers that could negatively impact the model are identified and removed.

### Data Integration
The `train.csv` and `features.csv` datasets are merged based on the store identifier to combine sales data with store-specific features like:
- Store type
- Store size
- Economic indicators

### Data Visualization
Visualizations are created to uncover insights into sales patterns:
- **Monthly Sales**: The total sales for each month are visualized to identify seasonal trends.
- **Yearly Trends**: Sales trends over multiple years are examined.
- **Store Performance**: Average sales per store are calculated to identify underperforming or overperforming stores.

### Time Series Decomposition
To understand underlying patterns in the data, the sales time series is decomposed into:
- **Trend**: The long-term movement (e.g., overall increase or decrease).
- **Seasonality**: Regular fluctuations, such as those during holidays.
- **Residuals**: The "noise" or irregular components.

This decomposition is done using the `seasonal_decompose` function from `statsmodels`.

### Data Transformation & Reduction
- **Normalization**: Min-Max scaling is applied to normalize the data, ensuring all features have the same scale and no feature dominates due to its magnitude.

### Data Splitting
The dataset is split into training and testing sets using `train_test_split` from `scikit-learn`:
- **X_train**: Predictor variables for training the model.
- **X_test**: Predictor variables for testing the model.
- **y_train**: Target variable (weekly sales) for training.
- **y_test**: Target variable (weekly sales) for testing.

---

## Modeling

Several machine learning models are used to predict weekly sales:
1. **Linear Regression**
2. **XGBoost Regressor**
3. **KNN Regressor**
4. **Random Forest Regressor**
5. **Deep Neural Network (DNN)**

Each model is trained on the training dataset and evaluated on the testing dataset.

---

## Model Performance

The models are evaluated using several performance metrics, including **accuracy**, **Mean Absolute Error (MAE)**, **Mean Squared Error (MSE)**, **Root Mean Squared Error (RMSE)**, and **R²**.

### 1. **Linear Regression**
- **Accuracy**: 92.32%
- **MAE**: 0.0302
- **MSE**: 0.0035
- **RMSE**: 0.0589
- **R²**: 0.9232

### 2. **XGBoost Regressor**
- **Accuracy**: 97.50%
- **MAE**: 0.0188
- **MSE**: 0.0011
- **RMSE**: 0.0336
- **R²**: 0.9750

### 3. **KNN Regressor**
- **Accuracy**: 95.62%
- **MAE**: 0.0211
- **MSE**: 0.0020
- **RMSE**: 0.0444
- **R²**: 0.9562

### 4. **Random Forest Regressor**
- **Accuracy**: 97.93%
- **MAE**: 0.0154
- **MSE**: 0.0009
- **RMSE**: 0.0306
- **R²**: 0.9793

### 5. **Deep Neural Network (DNN)**
- **Accuracy**: 97.87%
- **MAE**: 0.0343
- **MSE**: 0.0039
- **RMSE**: 0.0628
- **R²**: 0.9127
