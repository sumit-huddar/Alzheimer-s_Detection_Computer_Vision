# Medical Imaging Pipeline & 3D CNN Experiments on MRI Data

This repository contains my exploration of medical image analysis using MRI data, focusing on the complete pipeline from classical image processing techniques to deep learning-based models.

The work progresses from understanding raw medical imaging data to building and analyzing 3D convolutional neural networks.

---

## Overview

The goal of this project was to understand how different approaches — from basic image processing to deep learning — can be applied to **3D MRI data**, and how design choices impact performance.

Key aspects explored:
- Handling MRI data in NIfTI format  
- Visualizing 3D brain volumes  
- Applying classical techniques like edge detection  
- Preprocessing volumetric data  
- Implementing and experimenting with 3D CNN models  

---

## Project Breakdown

### Medical Image Loading & Visualization
- Loaded MRI data using nibabel
- Worked with NIfTI (.nii) format
- Visualized slices across:
  - Axial
  - Coronal
  - Sagittal planes  

Focus: Building intuition for 3D medical data

---

### Classical Processing & Preprocessing

#### Edge Detection
- Implemented edge detection using convolutional kernels  
- Applied filters to highlight structural boundaries in MRI slices  
- Built intuition for how spatial features are extracted  

#### Preprocessing Pipeline
##### 3D
- Normalized MRI volumes  
- Resized 3D scans (e.g., 64³ to 32³)  
- Converted data into model-compatible formats
##### 2D
- Implemented techniques like skull-stripping and bias field correction.

Focus: Understanding feature extraction before deep learning

---

### Deep Learning & 3D CNN Experiments

#### 3D CNN Implementation
- Built 3D convolutional neural networks for MRI classification  
- Trained on Alzheimer’s dataset  

#### Experimentation
- Compared different architectures  
- Tested input resolutions (64³ vs 32³)  
- Introduced regularization (Dropout, BatchNorm)  

Focus: Studying how architectural and preprocessing choices affect performance

---

## Results & Observations

| Experiment | Setup | Observation |
|----------|------|------------|
| Baseline | Large 3D CNN + small dataset | Poor performance (~0.16 accuracy) |
| Improved | More data + smaller model | Noticeable improvement |
| Regularized | BatchNorm + Dropout | Better generalization |

---

## Tech Stack

- Python  
- TensorFlow / Keras  
- PyTorch (for 3D interpolation)  
- Nibabel  
- NumPy, Matplotlib  

---

## Key Learnings

- Classical image processing (like edge detection) helps build intuition for feature extraction  
- MRI data requires fundamentally different handling than standard images  
- 3D CNNs are computationally expensive and sensitive to input size  
- Model complexity must match dataset size  
- Iterative experimentation is essential for improving results  

---

## Limitations

- Used a subset of dataset due to memory constraints  
- Limited training time and hyperparameter tuning  
- No advanced architectures explored  

---

## Future Work

- Train on larger datasets with efficient data loaders  
- Compare classical methods vs deep learning approaches  
- Explore lightweight architectures  
- Apply advanced models (e.g., transformers, hybrid models)  

---

## Author

**Sumit Huddar**  
Undergraduate, Mathematics  
IIT Kanpur

---


