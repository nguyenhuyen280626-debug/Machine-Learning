# Model Implementation

# Customer Segmentation Using K-Means Clustering

This stage focuses on implementing, training, and evaluating the **K-Means clustering algorithm** for customer segmentation. After completing the **Exploratory Data Analysis (EDA)** and **Feature Selection** stages, the processed dataset is used to identify customer groups based on purchasing behavior.

---

# 1. Import Required Libraries

Import the necessary libraries for data processing, visualization, clustering, and evaluation.

### Data Processing

* NumPy
* Pandas

### Data Visualization

* Matplotlib
* Seaborn

### Machine Learning

* Scikit-learn
* KMeans
* StandardScaler

### Model Evaluation

* Silhouette Score
* Within-Cluster Sum of Squares (WCSS)

---

# 2. Load the Dataset

Load the customer dataset and prepare it for clustering.

### Tasks

* Read the **Mall_Customers.csv** dataset.
* Display the first five rows.
* Verify the dataset dimensions.
* Select the relevant features for clustering.

The selected features are:

* Annual Income (k$)
* Spending Score (1–100)

These two variables best represent customers' financial capability and purchasing behavior.

---

# 3. Data Preprocessing

Before applying K-Means clustering, the dataset must be prepared.

### Tasks

* Remove the **CustomerID** column.
* Select the clustering features.
* Verify the shape of the input data.

---

# 4. Feature Scaling

Since K-Means is a distance-based algorithm, feature scaling is essential.

### Method

* StandardScaler

### Objective

* Standardize all numerical features.
* Ensure that each feature contributes equally to the Euclidean distance.
* Improve clustering performance.

---

# 5. Determine the Optimal Number of Clusters

The Elbow Method is used to identify the most appropriate number of clusters.

### Procedure

* Train K-Means models using different values of **K**.
* Compute the Within-Cluster Sum of Squares (WCSS) for each value.
* Plot the Elbow Curve.

### Objective

* Identify the optimal number of customer segments before training the final model.

---

# 6. Build the K-Means Clustering Model

After determining the optimal number of clusters, train the final K-Means model.

### Model Configuration

* Number of clusters (K)
* Random state for reproducibility
* Number of centroid initializations (n_init)

### Training Process

* Initialize cluster centroids.
* Assign each customer to the nearest centroid.
* Update centroid locations.
* Repeat until convergence.

The resulting cluster labels are then assigned to each customer.

---

# 7. Model Evaluation

Evaluate the quality of the clustering results.

### Silhouette Score

The Silhouette Score measures how well each customer fits within its assigned cluster compared to neighboring clusters.

Interpretation:

* Above 0.70 : Excellent clustering
* 0.50 – 0.70 : Good clustering
* 0.25 – 0.50 : Fair clustering
* Below 0.25 : Poor clustering

A higher Silhouette Score indicates better-separated and more compact clusters.

---

# 8. Visualize Customer Segments

Visualize the clustering results using scatter plots.

### Scatter Plot

Plot:

* Annual Income (k$)
* Spending Score (1–100)

Each color represents a different customer segment.

### Objective

* Observe the separation between customer groups.
* Evaluate whether the clusters are clearly distinguishable.

---

# 9. Interpret Customer Segments

Analyze the characteristics of each cluster.

Possible customer groups include:

* High Income – High Spending
* High Income – Low Spending
* Low Income – High Spending
* Low Income – Low Spending

These customer segments provide valuable insights for targeted marketing strategies and business decision-making.

---

# 10. Save the Trained Model (Optional)

After training, the clustering model can be saved for future use.

Possible files include:

* kmeans_model.pkl
* scaler.pkl

Saving the model allows new customer data to be assigned to existing clusters without retraining.

---

# 11. Predict New Customer Segments

The trained model can be used to classify new customers.

### Prediction Process

* Load the saved K-Means model.
* Load the saved StandardScaler.
* Read new customer data.
* Apply the same preprocessing and feature scaling steps.
* Predict the cluster label.
* Assign the customer to the corresponding segment.

---

# Expected Results

After completing the model implementation stage, the following outcomes are expected:

* A successfully trained K-Means clustering model.
* Customer groups identified based on annual income and spending behavior.
* The optimal number of clusters determined using the Elbow Method.
* Clustering quality evaluated using the Silhouette Score.
* Clear visualization of customer segments.
* Meaningful interpretation of each customer group for marketing analysis.
* A reusable clustering model capable of assigning new customers to existing segments.
* A complete customer segmentation pipeline from data preprocessing to customer classification.
