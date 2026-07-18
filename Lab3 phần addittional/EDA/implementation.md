# K-Means Image Segmentation

# Model Implementation

This stage focuses on implementing the K-Means clustering algorithm for image segmentation. After completing the Exploratory Data Analysis (EDA), the preprocessed image is converted into pixel features and grouped into clusters based on color similarity.

---

# 1. Import Required Libraries

Import all libraries required for image processing, visualization, numerical computation, and clustering.

### Image Processing

* OpenCV (cv2)

### Numerical Computation

* NumPy

### Data Visualization

* Matplotlib

### Machine Learning

* Scikit-learn
* KMeans

---

# 2. Load the Image

Read the selected image from the Intel Image Dataset.

```python
image = cv2.imread(image_path)
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
```

Purpose:

* Load the image into memory.
* Convert the image from BGR to RGB for correct visualization.

---

# 3. Image Preprocessing

Resize the image before clustering.

```python
image = cv2.resize(image,(256,256))
```

Purpose:

* Standardize image dimensions.
* Reduce computational cost.
* Improve clustering speed.

---

# 4. Convert the Image into Pixel Features

Transform the image into a two-dimensional matrix.

```python
pixel_values = image.reshape((-1,3))

pixel_values = np.float32(pixel_values)
```

Purpose:

* Convert image pixels into feature vectors.
* Each row represents one pixel.
* Each column corresponds to one RGB color channel.

---

# 5. Build the K-Means Model

Initialize the K-Means clustering model.

```python
k = 5

kmeans = KMeans(
    n_clusters=k,
    random_state=42,
    n_init=10
)
```

Configuration:

* Number of Clusters: 5
* Random State: 42
* Number of Initializations: 10

Purpose:

* Define the clustering model.
* Improve clustering stability by using multiple initializations.

---

# 6. Train the K-Means Model

Fit the K-Means model to the pixel data.

```python
labels = kmeans.fit_predict(pixel_values)
```

Purpose:

* Assign every pixel to the nearest cluster centroid.
* Produce cluster labels for all pixels.

---

# 7. Obtain Cluster Centers

Retrieve the representative colors for each cluster.

```python
centers = np.uint8(kmeans.cluster_centers_)
```

Purpose:

* Compute the average RGB value of each cluster.
* Represent each cluster using a dominant color.

---

# 8. Generate the Segmented Image

Replace each pixel with its corresponding cluster centroid.

```python
segmented_data = centers[labels]

segmented_image = segmented_data.reshape(image.shape)
```

Purpose:

* Reconstruct the segmented image.
* Reduce the number of colors while preserving important structures.

---

# 9. Visualize the Results

Display the original image and the segmented image.

```python
plt.subplot(1,2,1)
plt.imshow(image)

plt.subplot(1,2,2)
plt.imshow(segmented_image)
```

Purpose:

* Compare the original image with the segmented image.
* Evaluate the effectiveness of image segmentation.

---

# 10. Compare Different Numbers of Clusters

Repeat the clustering process using different values of K.

```python
Ks = [2,3,5,7]
```

Purpose:

* Observe how different cluster numbers affect segmentation quality.
* Select an appropriate value of K.

General observations:

* K = 2 produces a very simple segmentation.
* K = 3 separates major regions more clearly.
* K = 5 provides a good balance between detail and simplicity.
* K = 7 preserves more image details but increases computational complexity.

---

# 11. Save the Segmented Image

Save the segmentation result.

```python
cv2.imwrite(
    "segmented_image.jpg",
    cv2.cvtColor(segmented_image,
    cv2.COLOR_RGB2BGR)
)
```

Purpose:

* Store the segmented image for reporting or future use.

---

# 12. Results and Discussion

The K-Means clustering algorithm successfully segmented the image by grouping pixels with similar RGB values.

The segmented image contains only five representative colors, reducing image complexity while preserving the main visual structures.

The comparison using different values of K demonstrates that increasing the number of clusters results in more detailed segmentation but also increases computational complexity.

---

# Expected Outcomes

After completing the implementation stage, the following outcomes are expected:

* Successfully apply the K-Means clustering algorithm to image segmentation.
* Group pixels into clusters according to RGB color similarity.
* Generate a segmented image with reduced color complexity.
* Compare segmentation performance using different values of K.
* Visualize the original and segmented images.
* Save the final segmentation result for further analysis or reporting.