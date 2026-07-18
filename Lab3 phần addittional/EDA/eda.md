# K-Means Image Segmentation

# Exploratory Data Analysis (EDA)

Exploratory Data Analysis (EDA) is the first step before applying the K-Means clustering algorithm. In image segmentation, EDA helps understand the characteristics of the image, verify that it has been loaded correctly, and prepare it for clustering.

The objectives of this stage are:

- Load the image successfully.
- Explore the image dimensions and color channels.
- Visualize the original image.
- Resize the image for faster computation.
- Convert the image into pixel features.
- Prepare the dataset for K-Means clustering.

---

# 1. Image Overview

### Import Required Libraries

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
- Display images.
- Apply the K-Means clustering algorithm.

---

### Check Dataset Structure

```python
dataset_path = "Intel Image Dataset"

print(os.listdir(dataset_path))
```

Purpose:

- Verify that the dataset has been loaded successfully.
- Display all image categories available in the dataset.

Expected Output

```
['buildings',
 'forest',
 'glacier',
 'mountain',
 'sea',
 'street']
```

---

# 2. Image Selection

### Select an Image

```python
folder = os.path.join(dataset_path, "buildings")

image_name = os.listdir(folder)[0]

image_path = os.path.join(folder, image_name)
```

Purpose:

- Automatically select one image from the Buildings category.
- Avoid manually specifying the image name.

---

# 3. Image Loading

### Read Image

```python
image = cv2.imread(image_path)

image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
```

Purpose:

- Read the selected image.
- Convert the image from BGR to RGB for correct visualization.

---

### Display Original Image

```python
plt.imshow(image)

plt.axis("off")

plt.show()
```

Purpose:

- Display the original image.
- Verify that the image is loaded correctly.

---

### Image Shape

```python
print(image.shape)
```

Purpose:

- Display image dimensions.

Example Output

```
(150, 150, 3)
```

where

- Height = 150 pixels
- Width = 150 pixels
- RGB Channels = 3

---

# 4. Image Preprocessing

### Resize Image

```python
image = cv2.resize(image,(256,256))
```

Purpose

- Standardize image size.
- Reduce computational complexity.
- Improve K-Means processing speed.

---

### Display Resized Image

```python
plt.imshow(image)

plt.axis("off")
```

Purpose

- Verify that resizing was successful.

---

# 5. Pixel Feature Extraction

### Convert Image into Pixel Matrix

```python
pixel_values = image.reshape((-1,3))

pixel_values = np.float32(pixel_values)
```

Purpose

- Transform the image into a two-dimensional matrix.
- Each row represents one pixel.
- Each column represents an RGB color value.

---

### Pixel Matrix Shape

```python
print(pixel_values.shape)
```

Example Output

```
(65536,3)
```

Meaning

- 65,536 pixels
- 3 color features (Red, Green, Blue)

---

# Expected Insights

After completing Exploratory Data Analysis, the following insights are expected:

- Verify that the Intel Image Dataset has been loaded successfully.
- Understand the image dimensions.
- Confirm that the image contains three RGB color channels.
- Prepare the image for clustering.
- Convert image data into numerical pixel features.
- Produce a pixel matrix suitable for K-Means clustering.
- Reduce computational cost through image resizing.
- Ensure the image is ready for the Image Segmentation stage.