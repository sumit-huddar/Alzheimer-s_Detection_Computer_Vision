# 3D CNN for Alzheimer’s Detection using MRI Data

## Overview
This project explores the use of **3D Convolutional Neural Networks (3D CNNs)** on volumetric MRI data to classify brain scans into:
- AD (Alzheimer’s Disease)
- CN (Cognitively Normal)
- MCI (Mild Cognitive Impairment)

---

## Dataset
- Source: ADNI MRI dataset (Kaggle)
- Format: NIfTI (`.nii`) volumetric data

## Directory structure: 
train/train/{AD, CN, MCI}
val/val/{AD, CN, MCI}
test/test/{AD, CN, MCI}


Each MRI scan is a 3D volume with approximate shape: (Depth, Height, Width) = (160, 192, 192)


---

## Preprocessing Pipeline

1. **Loading MRI Data**
   - Used `nibabel` to read `.nii` files

2. **Normalization**
   - Standardized using:
     ```
     (x - mean) / std
     ```

3. **Resizing**
   - Converted all volumes to fixed sizes:
     - 64 × 64 × 64
     - 32 × 32 × 32  
   - Used trilinear interpolation

4. **Tensor Formatting**
   - Final TensorFlow input format:
     ```
     (batch, depth, height, width, channels)
     = (1, 64, 64, 64, 1)
     ```

---

## Experiments

### Experiment 1: Baseline Model
- Large 3D CNN
- Very small dataset (~15 samples)
- Input size: 64³

**Result:**
- Validation Accuracy = **0.16**

**Observation:**
- Model performed close to random guessing
- insufficient data and high model complexity

---

### Experiment 2: Improved Model
- Increased dataset size
- Reduced input resolution (32³)
- Simpler architecture

**Result:**
- Validation Accuracy = **0.2-0.3**

**Key Improvements:**
- Better generalization
- Faster convergence

---

### Experiment 3: Regularized Model
- Added Batch Normalization
- Added Dropout
- Tuned learning rate

**Result:**
- Validation Accuracy = **0.3–0.4**

**Insights:**
- Regularization improved stability
- Balanced model complexity with dataset size

---

## Results Summary

| Model        | Validation Accuracy |
|-------------|-------------------|
| Baseline     | ~0.16             |
| Improved     | ~0.2–0.3          |
| Regularized  | ~0.3–0.4         |

---

## Visualizations

The following plots are included:
- Training vs Validation Accuracy
- Training vs Validation Loss
- Model Comparison (bar chart)
- Confusion Matrix

---

## Key Learnings

- 3D CNNs are powerful but require **large datasets**
- Reducing input size improves training efficiency
- Model complexity must match available data
- Preprocessing is critical for medical imaging tasks
- Iterative experimentation significantly improves results

---

## Limitations
- Huge size of MRI scans
- Small subset of dataset used due to memory constraints
- Limited training epochs
- No extensive hyperparameter tuning

---

## Future Work

- Train on full dataset using efficient data loaders
- Apply data augmentation to MRI volumes
- Compare 2D vs 3D CNN approaches
- Use pretrained 3D architectures and transfer learning
- Explore advanced models (ResNet3D, EfficientNet3D)

---

## Tech Stack

- Python
- TensorFlow / Keras
- PyTorch (for preprocessing)
- Nibabel
- NumPy, Matplotlib

---

## Author

**Sumit Huddar**  
IIT Kanpur — Mathematics Department




