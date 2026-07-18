# DATASET

[ttps://www.kaggle.com/datasets/puneet6060/intel-image-classificationt]
The Intel Image Dataset contains natural scene images divided into six categories:
- Buildings
- Forest
- Glacier
- Mountain
- Sea
- Street
This project uses one image from the dataset to perform image segmentation using the K-Means clustering algorithm.

# 1. Dataset Overview
In this section, the dataset structure is examined before image processing.
The following tasks are performed:
- Import the required libraries.
- Verify that the dataset has been loaded successfully.
- Display the available image categories.
- Select one image for segmentation.
- Load and visualize the original image.
- Check the image dimensions.

## Import Required Libraries
Import the libraries required for image processing, numerical computation, visualization, and clustering.

## Check Dataset Structure
Verify that the Intel Image Dataset is accessible and display all available image categories.

## Select an Image
Automatically select one image from the Buildings category for the segmentation experiment.

## Load and Display the Original Image
Read the selected image using OpenCV, convert it from BGR to RGB, and display the original image.

## Image Preprocessing
Resize the image to 256 × 256 pixels to reduce computational complexity and improve processing efficiency.

## Convert Image into Pixel Features
Transform the image into a two-dimensional matrix.
Each row represents one pixel.
Each column represents one RGB color component.

# 2. K-Means Clustering
After preprocessing, the K-Means algorithm is applied to cluster pixels according to their RGB color similarity.
The clustering process includes:
- Initializing cluster centroids.
- Assigning pixels to the nearest centroid.
- Updating centroid positions.
- Repeating until convergence.

## Cluster Centers
Display the representative RGB color of each cluster.
These colors will be used to reconstruct the segmented image.

## Generate the Segmented Image
Replace each pixel with its corresponding cluster centroid color and reconstruct the segmented image.

# 3. Result Visualization
Compare the original image and the segmented image to evaluate the effectiveness of image segmentation.

## Compare Different Values of K
Repeat the segmentation process using different numbers of clusters.
The experiment uses:
- K = 2
- K = 3
- K = 5
- K = 7
This comparison helps determine an appropriate number of clusters.

## Save the Segmented Image
Save the segmentation result for reporting and future analysis.

# 4. Conclusion
The K-Means clustering algorithm successfully grouped pixels with similar RGB values into several clusters.

The segmented image preserves the main visual structures while reducing color complexity.

Different values of K produce different segmentation results.
A moderate value such as K = 5 provides a good balance between image detail and computational efficiency.
