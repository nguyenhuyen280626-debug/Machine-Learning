# Feature Engineering Guide - Predicting Product Sales

## 1. Feature Engineering Overview

Feature Engineering is the process of transforming and preparing raw data to create a dataset suitable for building a machine learning model. This stage improves data quality, enhances the predictive capability of features, and optimizes the performance of the product sales prediction model.

The processed dataset generated in this stage will be used for model training and evaluation.

---

## 2. Feature Selection

Feature Selection is the process of identifying the most relevant variables for predicting the target variable.

### Input Features

The following features are selected as input variables:

- Age
- Gender
- City
- Product_Category
- Unit_Price
- Quantity
- Discount_Amount
- Payment_Method
- Device_Type
- Session_Duration_Minutes
- Pages_Viewed
- Is_Returning_Customer
- Delivery_Time_Days
- Customer_Rating

### Target Variable

The target variable is:

- Total_Amount

These selected features represent customer demographics, purchasing behavior, product information, transaction details, and customer experience, all of which may influence product sales.

---

## 3. Data Type Transformation

Data type transformation ensures that every feature has the appropriate data type before further preprocessing.

### 3.1 Datetime Conversion

The dataset should first be checked to determine whether it contains any date or time features.

If datetime columns (such as `Order_Date`, `Purchase_Date`, or `Transaction_Date`) are available, they should be converted to the `datetime` data type using the `pd.to_datetime()` function.

After conversion, additional temporal features may be extracted, including:

- Year
- Month
- Day
- Day of the Week
- Quarter
- Weekend Indicator

These features can help capture seasonal purchasing trends and customer shopping behavior.

For the current dataset, no datetime features are available; therefore, no datetime conversion is required.

---

### 3.2 Categorical Type Conversion

Categorical variables should be converted to the `category` data type before encoding. This reduces memory usage and improves processing efficiency.

Typical categorical features include:

- Gender
- City
- Product_Category
- Payment_Method
- Device_Type

These features will later be transformed into numerical representations through encoding techniques.

---

### 3.3 Numerical Type Validation

All numerical variables should be validated to ensure they are stored as numeric data types (`int64` or `float64`).

Numerical features include:

- Age
- Unit_Price
- Quantity
- Discount_Amount
- Session_Duration_Minutes
- Pages_Viewed
- Delivery_Time_Days
- Customer_Rating
- Total_Amount

If any numerical feature is stored as a string (`object`), it should be converted using functions such as `pd.to_numeric()`.

---

### 3.4 Data Type Consistency

Finally, the transformed dataset should be validated to ensure that every feature has the correct data type before proceeding to feature encoding and feature scaling.

The expected outcome is:

- All numerical variables are stored as numeric data types.
- All categorical variables are correctly identified.
- Datetime variables are converted correctly (if available).
- The dataset is ready for the next preprocessing steps.

---

## 4. Categorical Feature Encoding

Machine learning algorithms require numerical input; therefore, categorical variables must be converted into numerical representations.

The categorical features include:

- Gender
- City
- Product_Category
- Payment_Method
- Device_Type

Common encoding techniques include:

- Label Encoding
- One-Hot Encoding

The encoding technique should be selected based on the characteristics of each feature and the machine learning algorithm being used.

---

## 5. Feature Scaling

Feature Scaling is performed to normalize numerical variables so that they are on a comparable scale.

Scaling prevents variables with large numerical ranges from dominating the learning process and improves the performance of many machine learning algorithms.

Common scaling techniques include:

- StandardScaler
- MinMaxScaler

The following numerical features are typically scaled:

- Age
- Unit_Price
- Quantity
- Discount_Amount
- Session_Duration_Minutes
- Pages_Viewed
- Delivery_Time_Days
- Customer_Rating

The target variable (`Total_Amount`) is generally not scaled unless required by a specific machine learning algorithm.

---

## 6. Feature Matrix and Target Variable

After preprocessing, the dataset is separated into:

### Feature Matrix (X)

The input feature matrix contains all selected predictor variables.

### Target Variable (y)

The target variable is:

- Total_Amount

This separation prepares the dataset for machine learning model training.

---

## 7. Train-Test Split

Before training the machine learning models, the processed dataset is divided into training and testing sets.

A common split ratio is:

- Training Set: 80%
- Testing Set: 20%

The training set is used to train the models, while the testing set is used to evaluate prediction performance on unseen data.

---

## 8. Save Processed Data

The processed dataset is saved in the `data/ready_train/` directory.

Typical saved files may include:

- X_train
- X_test
- y_train
- y_test

or a processed dataset file such as:

- processed_dataset.csv

Saving the processed data improves reproducibility and avoids repeating preprocessing in future experiments.

---

## Expected Output

After completing the Feature Engineering process:

- Relevant features have been selected for model training.
- All variables have the correct data types.
- Categorical variables have been encoded appropriately.
- Numerical variables have been scaled when necessary.
- The dataset has been separated into feature matrix (`X`) and target variable (`y`).
- The dataset has been divided into training and testing sets.
- The processed dataset has been saved for the modeling stage.
- The data is fully prepared for machine learning model training and evaluation.