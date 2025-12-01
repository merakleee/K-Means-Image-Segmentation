# K-Means Image Segmentation

Unsupervised image segmentation using K-Means clustering on 15 diverse images. This project segments pixels into coherent regions based on color (RGB) and spatial position (X, Y coordinates).

## Overview

The pipeline loads and downsamples images to max 500px, extracts 5D feature vectors (R, G, B, normalized X, Y) for each pixel, clusters them using MiniBatchKMeans for K ∈ {2, 3, 4, 5}, evaluates quality with Silhouette Score (sampled for speed), and saves 60 segmented images. The project also experiments with Lab color space, Gaussian blur preprocessing, and the Elbow Method for choosing K.

## Results

**Average Silhouette Score: ~0.60** (K=2 is optimal). Best performing images: image11.jpg (0.90), image15.jpg (0.95). RGB+XY features outperformed Lab+XY. K=2 provided the best trade-off between simplicity and clustering quality.

## Repository Structure

- **Images/** - Original 15 input images
- **output_segments/** - Segmented images for each K value
- **notebook.ipynb** - Full pipeline: loading, feature extraction, clustering, evaluation, visualization
- **segmentation_results.csv** - Per-image silhouette scores and metrics
- **AI Challenge 2.pdf** - Challenge description

## Key Techniques

1. **Image Preprocessing** - RGB conversion, aspect-ratio-preserving downsampling to 500px max.
2. **Feature Engineering** - 5D vectors combining color and normalized spatial coordinates.
3. **Clustering** - MiniBatchKMeans with k-means++ initialization for efficiency and reproducibility.
4. **Evaluation** - Silhouette Score computed on random 2k-10k pixel samples for speed.
5. **Experiments** - Lab vs RGB color spaces, Gaussian blur, Elbow Method validation.

## Installation & Usage
- git clone https://github.com/merakleee/K-Means-Image-Segmentation.git              
- cd K-Means-Image-Segmentation                    
- pip install numpy matplotlib scikit-learn pillow opencv-python                 
- jupyter notebook notebook.ipynb

Run all cells to generate segmented outputs in `output_segments/`.

## Technologies

Python, NumPy, scikit-learn, OpenCV, Matplotlib, Pillow

