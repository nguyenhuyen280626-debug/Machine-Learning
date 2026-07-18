# K-Means Image Segmentation

## 1. Introduction

Image Segmentation is a computer vision technique used to divide an image into multiple meaningful regions. It helps simplify image analysis by grouping pixels with similar characteristics.

In this project, the K-Means clustering algorithm is applied to segment an image based on pixel color values (RGB). Each pixel is assigned to one of K clusters, and the segmented image is reconstructed using the cluster centroids.

---

## 2. Problem Statement

The objective of this project is to segment a given image into K clusters using the K-Means clustering algorithm.

The main tasks include:

- Load an image from the dataset.
- Preprocess the image.
- Convert the image into pixel features.
- Apply K-Means clustering.
- Generate the segmented image.
- Compare the original and segmented images.

---

## 3. Dataset Description

This project uses the **Intel Image Dataset**, which contains natural scene images divided into six categories.

| Category | Description |
|----------|-------------|
| Buildings | Urban buildings and architecture |
| Forest | Forest landscapes |
| Glacier | Ice and snow landscapes |
| Mountain | Mountain scenery |
| Sea | Ocean and beach scenes |
| Street | Urban street environments |

In this project, one image from the **Buildings** category is selected for segmentation.

---

## 4. Image Loading and Preprocessing

### Import Libraries

```python
import os
import cv2
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
```

Purpose:

- Import libraries for image processing.
- Perform numerical computation.
- Visualize images.
- Apply the K-Means clustering algorithm.

---

### Load Image

```python
image = cv2.imread(image_path)
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
```

Purpose:

- Read the selected image.
- Convert the color space from BGR to RGB for correct visualization.

---

### Resize Image

```python
image = cv2.resize(image, (256,256))
```

Purpose:

- Reduce image size.
- Improve computational efficiency.
- Speed up K-Means clustering.

---

## 5. Feature Extraction

Each pixel is treated as one data sample with three features:

- Red (R)
- Green (G)
- Blue (B)

Convert the image into a two-dimensional matrix.

```python
pixel_values = image.reshape((-1,3))
pixel_values = np.float32(pixel_values)
```

Purpose:

- Transform image data into the format required by K-Means.
- Each row represents one pixel.

---

## 6. K-Means Clustering

The K-Means algorithm groups pixels with similar colors into K clusters.

```python
k = 5

kmeans = KMeans(
    n_clusters=k,
    random_state=42,
    n_init=10
)

labels = kmeans.fit_predict(pixel_values)
```

### K-Means Process

1. Initialize K cluster centroids.
2. Calculate the distance from each pixel to every centroid.
3. Assign each pixel to the nearest centroid.
4. Update the centroid positions.
5. Repeat until convergence.

In this project:

- Number of clusters: **K = 5**
- Distance metric: Euclidean Distance

---

## 7. Image Segmentation

After clustering, each pixel is replaced by its cluster centroid color.

```python
centers = np.uint8(kmeans.cluster_centers_)

segmented_data = centers[labels]

segmented_image = segmented_data.reshape(image.shape)
```

Purpose:

- Reduce the number of colors.
- Produce the segmented image.
- Preserve the major visual structures.

---

## 8. Result Visualization

### Original Image

Display the original image before segmentation.

```python
plt.imshow(image)
```

### Segmented Image

Display the segmented image after K-Means clustering.

```python
plt.imshow(segmented_image)
```

Purpose:

- Compare the original image and segmented image.
- Observe the effectiveness of color-based segmentation.

---

## 9. Comparison of Different K Values

Different values of K are tested.

```python
Ks = [2,3,5,7]
```

Purpose:

- Compare segmentation quality.
- Observe how the number of clusters affects the final image.

General observations:

| K | Result |
|---|--------|
| 2 | Very simple segmentation with only a few colors |
| 3 | Better separation of major regions |
| 5 | Good balance between detail and simplicity |
| 7 | More image details are preserved |

---

## 10. Results and Discussion

The K-Means algorithm successfully grouped pixels with similar RGB values into clusters.

The segmented image contains only five representative colors while maintaining the main structures of the original image.

The experiment also shows that increasing the value of K produces more detailed segmentation but increases computational complexity.

---

## 11. Conclusion

This project successfully applied the K-Means clustering algorithm to image segmentation.

Key findings:

- Images can be represented as pixel feature vectors.
- K-Means effectively groups pixels with similar colors.
- Image segmentation reduces color complexity while preserving important visual information.
- Different values of K produce different segmentation results.
- K = 5 provides a good balance between image quality and computational efficiency.

---

## References

- Intel Image Dataset
- Scikit-Learn Documentation
- OpenCV Documentation
- K-Means Clustering Algorithm Documentation