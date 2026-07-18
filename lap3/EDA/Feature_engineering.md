# Feature Engineering

Feature Engineering is the process of selecting, transforming, and preparing features before training a Machine Learning model. The objective is to improve data quality, enhance model performance, and remove irrelevant or redundant information.

In this project, the processed dataset is used to train a **K-Means clustering model** for customer segmentation based on customer purchasing behavior.

---

# 1. Data Cleaning

## Missing Values

The first step is to ensure the dataset is complete.

### Tasks

* Detect missing values in all features.
* Calculate the percentage of missing values.
* Remove or impute missing values if necessary.

### Expected Outcome

* The dataset contains no missing values before clustering.

---

## Duplicate Records

### Tasks

* Identify duplicate records.
* Remove duplicated observations if any exist.

### Expected Outcome

* Each customer is represented by a unique record.

---

## Invalid Values

### Tasks

* Detect inconsistent or unrealistic values.
* Correct or remove invalid records if necessary.

Examples include:

* Negative age values.
* Negative annual income.
* Spending scores outside the valid range (1–100).

---

# 2. Data Type Transformation

Ensure that all variables have appropriate data types.

## Numerical Features

The numerical features include:

* Age
* Annual Income (k$)
* Spending Score (1–100)

These variables should be stored as integer or floating-point values.

---

## Categorical Feature

The categorical feature is:

* Gender

If required for future analysis, it can be converted into numerical values using an appropriate encoding technique.

Since the final clustering model uses only **Annual Income** and **Spending Score**, the Gender attribute is not included in model training.

---

# 3. Feature Selection

Based on the exploratory data analysis, the following features are selected:

* Annual Income (k$)
* Spending Score (1–100)

### Reasons

* They directly describe customers' purchasing power and spending behavior.
* They produce easily interpretable customer segments.
* They are suitable for two-dimensional visualization.

The following features are excluded:

* CustomerID (identifier only)
* Age (used for analysis only)
* Gender (used for interpretation only)

---

# 4. Feature Scaling

K-Means clustering relies on Euclidean distance; therefore, feature scaling is required.

## Standardization (Z-score Normalization)

The selected numerical features are standardized using **StandardScaler**.

After scaling:

* Mean = 0
* Standard Deviation = 1

### Objective

* Ensure equal contribution of each feature.
* Prevent one variable from dominating the clustering process.
* Improve clustering accuracy.

---

# 5. Feature Transformation

For this dataset, no additional feature transformations are required.

### Analysis

* Log transformation is unnecessary because the selected features have reasonable distributions.
* Binning is not applied since continuous numerical values provide better clustering performance.

---

# 6. Feature Creation

No new features are created in this project.

The original features **Annual Income** and **Spending Score** already provide sufficient information for customer segmentation.

Future improvements may include creating additional behavioral features, such as:

* Spending-to-Income Ratio
* Estimated Purchasing Capacity
* Customer Age Group

However, these features are beyond the scope of this project.

---

# 7. Feature Validation

Before training the clustering model, the selected features are verified.

### Validation Steps

* Confirm that the selected features contain no missing values.
* Verify the data types.
* Check the feature distributions.
* Confirm successful standardization.

These steps ensure that the dataset is ready for clustering.

---

# 8. Prepare Data for K-Means Clustering

After preprocessing, the dataset is prepared for model training.

### Tasks

* Remove unnecessary attributes.
* Select the input features.
* Apply StandardScaler.
* Store the standardized feature matrix.
* Prepare the dataset for the K-Means algorithm.

Unlike supervised learning models, K-Means does not require:

* Target labels
* Training and testing datasets
* Tensor conversion
* DataLoader

The algorithm is trained directly using the standardized feature matrix.

---

# Expected Results

After completing the Feature Engineering stage, the following outcomes are expected:

* A clean and consistent dataset.
* Missing values and duplicate records removed or verified.
* Appropriate data types assigned to all features.
* Irrelevant features excluded from the clustering process.
* Annual Income and Spending Score selected as the clustering variables.
* Numerical features standardized using StandardScaler.
* A processed dataset ready for K-Means clustering.
* Improved clustering performance and more meaningful customer segmentation results.
