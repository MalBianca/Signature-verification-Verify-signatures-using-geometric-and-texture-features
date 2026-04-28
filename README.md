# Signature-verification-Verify-signatures-using-geometric-and-texture-features


## Overview
Handwritten signatures are widely used for identity authentication, especially in financial and legal contexts. This project implements an offline signature verification pipeline working directly on 2D signature images using four feature extraction methods that capture distinct aspects of a signature's structure.

## Pipeline
The system follows a standard image processing workflow:
1. **Input Images** → Signature images in 2D format.
2. **Preprocessing** → Grayscale conversion, Gaussian filtering, and binarization.
3. **Feature Extraction** → Applying the four methods described below.
4. **Comparison** → Extracted features are compared against the training signature range.
5. **Classification** → Output labeled as **Authentic** or **Forged**.

## Methods Detail

### 1. Occupancy Ratio
Measures how much of the image area is covered by the signature.
$$Occupancy\ Ratio = \frac{signature\ pixels}{total\ pixels}$$

### 2. Density Ratio
Captures the left/right symmetry balance of the signature by comparing the density of the two halves.

### 3. Critical Points (Harris Corner Detector)
Detects structural corner points using the Harris algorithm:
$$R = det(M) - k \cdot trace(M)^2$$
* **R > 0**: Corner
* **R < 0**: Edge
* **R ≈ 0**: Flat region

### 4. Slope of Center of Gravities (COG)
Measures the inclination angle between the left and right centers of gravity:
$$slope = \arctan\left(\frac{dy}{dx}\right)$$

## Tech Stack
* **Language:** Python (Google Colab)
* **Libraries:** * `OpenCV`: Image manipulation and Harris detection.
    * `NumPy`: Matrix and vector operations.
    * `Skimage`: Grayscale conversion and Gaussian filtering.
    * `Matplotlib`: Visualization.

## Results & Limitations
* **Best Performer:** **Critical Points** achieved 100% accuracy, proving most robust for structural differentiation.
* **Limitations:** Performance is sensitive to parameter tuning and was tested on a small dataset (4 images). Results may vary on larger datasets.

## Future Work
* Combine all four methods into a weighted ensemble classifier.
* Integrate machine learning ( SVM, CNN) for automatic threshold tuning.
* Evaluate on larger, standardized signature datasets.
