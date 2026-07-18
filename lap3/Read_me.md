https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python/data

# Customer Segmentation Using K-Means Clustering

## 1. Introduction

Customer Segmentation is the process of dividing customers into groups based on similar characteristics and behaviors. This technique helps businesses better understand their customers and develop more effective marketing strategies.

In this project, the K-Means clustering algorithm is used to segment retail store customers based on their income and spending behavior.

---

## 2. Problem Statement

The dataset contains information about customers of a retail store, including:

* CustomerID
* Gender
* Age
* Annual Income (k$)
* Spending Score (1-100)

The objective is to identify different customer groups according to their purchasing power and spending habits.

---

## 3. Dataset Description

| Feature                | Description                       |
| ---------------------- | --------------------------------- |
| CustomerID             | Unique customer identifier        |
| Gender                 | Customer gender                   |
| Age                    | Customer age                      |
| Annual Income (k$)     | Annual income in thousand dollars |
| Spending Score (1-100) | Customer spending behavior score  |

---

## 4. Data Exploration

### Load Dataset

```python
import pandas as pd

df = pd.read_csv("Mall_Customers.csv")
df.head()
```

### Dataset Information

```python
df.info()
df.describe()
```

### Check Missing Values

```python
df.isnull().sum()
```

### Check Outliers

```python
import seaborn as sns

sns.boxplot(data=df[['Age',
                     'Annual Income (k$)',
                     'Spending Score (1-100)']])
```

---

## 5. Data Visualization

### Histogram

```python
df.hist(figsize=(10,6))
```

Purpose:

* Observe data distributions.
* Identify skewed features.

### Scatter Plot

```python
import matplotlib.pyplot as plt

plt.scatter(
    df['Annual Income (k$)'],
    df['Spending Score (1-100)']
)

plt.xlabel('Annual Income')
plt.ylabel('Spending Score')
plt.title('Income vs Spending Score')
plt.show()
```

Purpose:

* Observe relationships between income and spending.
* Identify potential customer groups.

---

## 6. Feature Selection

The original dataset contains five attributes:

* CustomerID
* Gender
* Age
* Annual Income (k$)
* Spending Score (1-100)

### Remove Unnecessary Feature

CustomerID is removed because it only acts as an identifier and does not describe customer behavior.

```python
df = df.drop('CustomerID', axis=1)
```

### Why Not Use All Features?

Although Age and Gender can provide additional information, the primary objective of this project is to segment customers based on:

* Financial capability
* Spending behavior

Therefore, the two most relevant features are selected:

```python
X = df[['Annual Income (k$)',
        'Spending Score (1-100)']]
```

### Business Interpretation

These features allow us to identify customer groups such as:

| Customer Group | Characteristics             |
| -------------- | --------------------------- |
| Cluster 1      | High Income – High Spending |
| Cluster 2      | High Income – Low Spending  |
| Cluster 3      | Low Income – High Spending  |
| Cluster 4      | Low Income – Low Spending   |

This makes the clustering results easier to interpret and more useful for marketing strategies.

---

## 7. Feature Scaling

K-Means is sensitive to feature scales. Therefore, standardization is required.

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_scaled = scaler.fit_transform(X)
```

Benefits:

* Prevents one feature from dominating another.
* Improves clustering performance.

---

## 8. Finding the Optimal Number of Clusters

### Elbow Method

```python
from sklearn.cluster import KMeans

wcss = []

for k in range(1,11):
    kmeans = KMeans(
        n_clusters=k,
        random_state=42,
        n_init=10
    )

    kmeans.fit(X_scaled)
    wcss.append(kmeans.inertia_)
```

### Plot Elbow Curve

```python
plt.plot(range(1,11), wcss, marker='o')
plt.xlabel('Number of Clusters')
plt.ylabel('WCSS')
plt.title('Elbow Method')
plt.show()
```

The elbow point indicates the optimal value of K.

---

## 9. K-Means Clustering

kmeans = KMeans(
    n_clusters=4,
    random_state=42,
    n_init=10
)

clusters = kmeans.fit_predict(X_scaled)

df['Cluster'] = clusters

K-Means Process:

Initialize K centroids randomly.
Assign each data point to the nearest centroid.
Update the centroid positions based on the mean of all points in each cluster.
Repeat the assignment and update steps until convergence.

The value K = 4 was selected to align with the feature selection strategy, where customers are categorized into four intuitive groups based on annual income and spending score:

High Income – High Spending
High Income – Low Spending
Low Income – High Spending
Low Income – Low Spending

This configuration provides a simple, interpretable, and effective customer segmentation model for business analysis.

---

## 10. Model Evaluation

### Silhouette Score

```python
from sklearn.metrics import silhouette_score

score = silhouette_score(
    X_scaled,
    clusters
)

print(score)
```

Interpretation:

| Score      | Meaning   |
| ---------- | --------- |
| > 0.7      | Excellent |
| 0.5 - 0.7  | Good      |
| 0.25 - 0.5 | Fair      |
| < 0.25     | Poor      |

---

## 11. Cluster Visualization

```python
plt.figure(figsize=(8,6))

plt.scatter(
    df['Annual Income (k$)'],
    df['Spending Score (1-100)'],
    c=df['Cluster']
)

plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.title('Customer Segments')
plt.show()
```

Each color represents a different customer segment.

---

## 12. Results and Discussion

After applying K-Means clustering, customers are grouped into several segments based on their income and spending behavior.

Examples of customer segments:

### Cluster 0

High Income – High Spending

### Cluster 1

High Income – Low Spending

### Cluster 2

Low Income – High Spending

### Cluster 3

Low Income – Low Spending

These groups provide valuable insights for targeted marketing campaigns.

---

## 13. Conclusion

This project successfully applied the K-Means clustering algorithm to customer segmentation.

Key findings:

* Annual Income and Spending Score are the most informative features for customer segmentation.
* CustomerID was removed because it does not contribute to clustering.
* K-Means effectively identifies groups of customers with similar behaviors.
* The results can help businesses improve customer targeting and marketing strategies.

---

## References

* Scikit-Learn Documentation
* Mall Customers Dataset
* K-Means Clustering Algorithm Documentation
