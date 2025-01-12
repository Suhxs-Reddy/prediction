Here’s a README template for your GitHub repository based on the dataset description and model evaluation results you provided:

---

# Walmart Sales Prediction

This repository contains the code and models used to predict department-wide sales for Walmart stores using historical sales data, promotional markdowns, and regional factors. The challenge also involves modeling the effect of holidays on sales during special markdown events.

## Dataset Description

The dataset contains historical sales data for 45 Walmart stores, including various departments within each store. The data spans from 2010 to 2012 and includes features such as sales figures, markdowns, temperature, fuel prices, CPI, unemployment rates, and whether the week corresponds to a special holiday.

### Files Provided:
- **stores.csv**: Information about the 45 stores (type and size).
- **train.csv**: Historical sales data for training the model (Weekly_Sales, Store, Dept, Date, IsHoliday).
- **test.csv**: Sales data similar to train.csv, but without the Weekly_Sales column (used for prediction).
- **features.csv**: Additional data on store, department, and regional activity (Temperature, Fuel_Price, MarkDown1-5, CPI, Unemployment, IsHoliday).

The dataset includes information about special holidays:
- **Super Bowl**: 12-Feb-10, 11-Feb-11, 10-Feb-12, 8-Feb-13
- **Labor Day**: 10-Sep-10, 9-Sep-11, 7-Sep-12, 6-Sep-13
- **Thanksgiving**: 26-Nov-10, 25-Nov-11, 23-Nov-12, 29-Nov-13
- **Christmas**: 31-Dec-10, 30-Dec-11, 28-Dec-12, 27-Dec-13

## Objective

The goal of this project is to predict the **Weekly_Sales** for each store, department, and date in the test dataset. The model must take into account the impact of holidays, regional activity, and promotional markdowns.

The competition is evaluated based on the **Weighted Mean Absolute Error (WMAE)**, where holiday weeks are weighted five times more than regular weeks.

## Models Used

We used multiple machine learning models to predict the sales, and their performance is detailed below:

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

### 3. **K-Nearest Neighbors (KNN) Regressor**
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

## Approach

We approached this problem using multiple machine learning techniques, first preprocessing the data to handle missing values, encode categorical variables, and engineer features such as holiday weeks. Then, we trained different models on the training data and evaluated them based on various metrics.

### Data Preprocessing
- Handling missing data for MarkDown features.
- Encoding `IsHoliday` as a binary feature.
- Merging `train.csv`, `test.csv`, and `features.csv` into one dataset for model training and testing.
- Scaling continuous features like `Temperature`, `Fuel_Price`, `CPI`, and `Unemployment`.

### Model Training
- **Linear Regression**: A simple baseline model for predicting sales.
- **XGBoost**: An optimized gradient boosting method that handled the non-linearity in the dataset.
- **KNN Regressor**: A non-parametric model for predicting sales based on similar past observations.
- **Random Forest**: An ensemble of decision trees for robust predictions.
- **Deep Neural Network**: A neural network
