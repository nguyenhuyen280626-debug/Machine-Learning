# Exploratory Data Analysis (EDA)

# Customer Segmentation Using K-Means Clustering

## 1. Dataset Overview

The dataset used in this project is **Mall_Customers.csv**, which contains customer information collected from a shopping mall. The objective is to analyze customer behavior and perform customer segmentation using the K-Means clustering algorithm.

### Tasks

* Load the dataset using Pandas.
* Display the first five rows of the dataset.
* Determine the number of observations and features.
* Examine the data types of all attributes.
* Generate descriptive statistics for numerical variables.
* Identify the purpose of each feature.

### Dataset Attributes

| Attribute              | Description                                           |
| ---------------------- | ----------------------------------------------------- |
| CustomerID             | Unique customer identifier                            |
| Gender                 | Customer gender                                       |
| Age                    | Customer age                                          |
| Annual Income (k$)     | Annual income in thousands of dollars                 |
| Spending Score (1–100) | Customer spending behavior score assigned by the mall |

Since **CustomerID** is only an identifier and does not provide meaningful information for clustering, it will be removed before model training.

---

# 2. Missing Value Analysis

The objective of this step is to ensure that the dataset is clean before applying the clustering algorithm.

### Tasks

* Detect missing values in each feature.
* Calculate the percentage of missing values.
* Identify duplicate records.
* Decide whether missing values should be removed or imputed.

### Expected Outcome

* The dataset contains no missing values.
* No duplicate records significantly affect the clustering process.

---

# 3. Univariate Analysis

## 3.1 Numerical Features

The numerical features include:

* Age
* Annual Income (k$)
* Spending Score (1–100)

### Analysis

* Generate descriptive statistics.
* Plot histograms.
* Plot density distributions.
* Visualize boxplots.
* Analyze the skewness of each feature.

### Objective

* Understand the distribution of each numerical feature.
* Observe the range and spread of the data.
* Detect potential outliers.

---

## 3.2 Categorical Feature

The categorical feature is:

* Gender

### Analysis

* Compute frequency counts.
* Plot a bar chart.
* Calculate the proportion of male and female customers.

### Objective

* Examine the distribution of customer genders.
* Identify any imbalance between categories.

---

# 4. Bivariate Analysis

## 4.1 Annual Income vs. Spending Score

These are the two most important variables used for customer segmentation.

### Analysis

* Create a scatter plot.
* Observe the natural grouping of customers.
* Estimate the potential number of clusters.

These two features are selected as the input variables for the K-Means clustering model.

---

## 4.2 Age vs. Spending Score

### Analysis

* Generate a scatter plot.

### Objective

* Investigate the relationship between customer age and spending behavior.

---

## 4.3 Age vs. Annual Income

### Analysis

* Generate a scatter plot.

### Objective

* Explore the relationship between age and annual income.

---

## 4.4 Gender vs. Spending Score

### Analysis

* Create boxplots.
* Calculate the average spending score for each gender.

### Objective

* Compare spending behavior between male and female customers.

---

# 5. Correlation Analysis

### Analysis

* Compute the correlation matrix.
* Visualize the correlations using a heatmap.

### Objective

* Identify relationships among numerical variables.
* Support feature selection before clustering.

---

# 6. Outlier Detection

### Analysis

* Visualize boxplots.
* Apply the Interquartile Range (IQR) method.

The following numerical features are examined:

* Age
* Annual Income (k$)
* Spending Score (1–100)

### Objective

* Detect unusual customer records.
* Evaluate the impact of outliers on the K-Means clustering algorithm.

---

# 7. Feature Selection

Based on the exploratory data analysis, the following features are selected for clustering:

* Annual Income (k$)
* Spending Score (1–100)

### Reasons

* They directly represent customers' financial capability and purchasing behavior.
* They provide clear and interpretable customer segments.
* They are suitable for two-dimensional visualization.
* CustomerID does not contain useful information for clustering.
* Age and Gender are retained only for exploratory analysis and interpretation, but are not used for training the clustering model.

---

# 8. Feature Scaling

Since K-Means is a distance-based algorithm that relies on Euclidean distance, feature scaling is necessary.

### Method

* StandardScaler

### Objective

* Standardize numerical features to the same scale.
* Prevent one feature from dominating the distance calculation.
* Improve clustering performance.

---

# 9. Determining the Optimal Number of Clusters

### Method

* Elbow Method

### Analysis

* Train K-Means models with different values of **K**.
* Calculate the Within-Cluster Sum of Squares (WCSS).
* Plot the Elbow Curve.

### Objective

* Determine the optimal number of clusters before training the final model.

---

# 10. Expected Insights

After completing the Exploratory Data Analysis (EDA), the following insights are expected:

* Gain a comprehensive understanding of the customer dataset.
* Confirm that the dataset is clean and contains no missing values.
* Understand the distribution of both numerical and categorical features.
* Explore the relationship between annual income and spending behavior.
* Identify the most informative features for customer segmentation.
* Detect potential outliers that may influence clustering performance.
* Determine the optimal number of clusters using the Elbow Method.
* Prepare a standardized dataset suitable for K-Means clustering.
* Provide meaningful customer segments that can support marketing strategies and business decision-making.
