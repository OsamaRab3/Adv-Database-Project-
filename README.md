# Housing Price Prediction Project

## Overview
This project involves building predictive models to estimate housing prices using a dataset containing various features of houses. The dataset is preprocessed and analyzed before applying regression models to predict the target variable, `price`. Various evaluation metrics are used to measure the performance of the models.

## Dataset
The dataset, `Housing_Price_Data.csv`, contains 545 entries and 13 columns with the following attributes:

- `price` (Target): The price of the house (integer).
- `area`: The area of the house (integer).
- `bedrooms`: Number of bedrooms (integer).
- `bathrooms`: Number of bathrooms (integer).
- `stories`: Number of stories (integer).
- `mainroad`: Whether the house is on the main road (categorical, yes/no).
- `guestroom`: Whether the house has a guestroom (categorical, yes/no).
- `basement`: Whether the house has a basement (categorical, yes/no).
- `hotwaterheating`: Whether the house has hot water heating (categorical, yes/no).
- `airconditioning`: Whether the house has air conditioning (categorical, yes/no).
- `parking`: Number of parking spaces (integer).
- `prefarea`: Whether the house is in a preferred area (categorical, yes/no).
- `furnishingstatus`: Furnishing status of the house (categorical with 3 values: furnished, semi-furnished, unfurnished).

## Preprocessing Steps

### 1. Data Inspection
- Identified numerical columns: `['price', 'area', 'bedrooms', 'bathrooms', 'stories', 'parking']`
- Identified categorical columns: `['mainroad', 'guestroom', 'basement', 'hotwaterheating', 'airconditioning', 'prefarea', 'furnishingstatus']`
- Checked the dataset structure, summary statistics, and data types.

### 2. Handling Missing Values
- Checked for missing values and calculated the percentage of missing data for each column.
- Imputed missing categorical values with the mode.
- Imputed missing numerical values based on skewness:
  - Used the median for highly skewed columns (|skewness| > 1).
  - Used the mean for columns with low skewness.

### 3. Encoding Categorical Variables
- Label encoding was applied to `furnishingstatus`.
- One-hot encoding was applied to binary and low/medium cardinality categorical variables.

### 4. Outlier Handling
- Applied the Interquartile Range (IQR) method to cap outliers in numerical columns.

### 5. Low Variance Features
- Identified and removed columns with very low variance (standard deviation < 0.01).

## Model Building

### Models Used
1. **Linear Regression**
2. **Decision Tree Regressor**
3. **Random Forest Regressor**

### Train-Test Split
- Split the data into training (80%) and testing (20%) sets.
- Features (X): All columns except `price`.
- Target (y): The `price` column.

### Model Evaluation Metrics
- **Mean Absolute Error (MAE)**: Average absolute difference between predicted and actual values.
- **Mean Squared Error (MSE)**: Average squared difference between predicted and actual values.
- **R-squared (R²)**: Proportion of variance in the target variable explained by the model.

### Results
#### Linear Regression
- MAE: 891,676.37
- MSE: 1,296,375,172,659.51
- R²: 0.6791

#### Decision Tree Regressor
- MAE: 1,184,669.72
- MSE: 2,596,013,256,880.73
- R²: 0.3574

#### Random Forest Regressor
- MAE: 973,089.28
- MSE: 1,558,283,760,707.95
- R²: 0.6143

## Observations
- **Linear Regression** performed the best with the highest R² value (0.6791) and lowest MSE.
- **Random Forest Regressor** also showed good performance but had a slightly higher MSE and lower R² than Linear Regression.
- **Decision Tree Regressor** had the lowest R² and highest MSE, indicating overfitting.

## Conclusion
Linear Regression is the most suitable model for predicting housing prices in this dataset based on its performance metrics. Further improvements could involve feature engineering, hyperparameter tuning, and exploring additional algorithms.

## Next Steps
- Implement hyperparameter optimization for the Random Forest model.
- Explore advanced regression models such as Gradient Boosting or XGBoost.
- Consider additional feature engineering and data augmentation techniques to improve predictions.

## Requirements
- **Python Libraries:**
  - numpy
  - pandas
  - scikit-learn
- **File:** Housing_Price_Data.csv

