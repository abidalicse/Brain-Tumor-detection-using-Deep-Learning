# Brain Tumor MRI Classification using StyleGAN and Hybrid CNN-ViT

## Overview

This repository presents a deep learning framework for automated brain tumor classification from MRI images using a multi-stage pipeline. The implementation uses a BraTS-based brain MRI classification dataset and integrates image preprocessing, StyleGAN2-ADA-based data augmentation, tumor-region segmentation, ResNet50 feature extraction, and hybrid CNN–Vision Transformer (CNN–ViT) classification.

## Research Pipeline

```text
BraTS MRI Dataset
        │
        ▼
Dataset Organization
        │
        ▼
Image Preprocessing
(Resize + Denoising + Normalization)
        │
        ▼
StyleGAN2-ADA Augmentation
(Class-wise Synthetic MRI Images)
        │
        ▼
Tumor Segmentation
        │
        ▼
ResNet50 Feature Extraction
        │
        ▼
Deep Feature Representation
        │
        ▼
Hybrid CNN–ViT Classification
        │
        ▼
Brain Tumor Classification
```

## Dataset

The dataset is organized into four classes:

| Label | Class | Training Images | Test Images |
|------:|-------|----------------:|------------:|
| 0 | Glioma | 1,147 | 254 |
| 1 | Meningioma | 1,329 | 306 |
| 2 | No Tumor | 1,067 | 140 |
| 3 | Pituitary | 1,457 | 300 |
| **Total** | | **5,000** | **1,000** |

### Dataset Structure

```text
classification_task/
├── train/
│   ├── glioma/
│   ├── meningioma/
│   ├── no_tumor/
│   └── pituitary/
└── test/
    ├── glioma/
    ├── meningioma/
    ├── no_tumor/
    └── pituitary/
```

## Image Preprocessing

The MRI images undergo:

- Image resizing
- Gaussian filtering for noise reduction
- Min-Max normalization
- Standardized image representation
- 224 × 224 image size for the deep learning stage

## StyleGAN2-ADA Augmentation

Class-wise StyleGAN2-ADA models are used for synthetic MRI data generation.

```text
0 → Glioma
1 → Meningioma
2 → No Tumor
3 → Pituitary
```

The class-wise training data contains:

```text
Glioma       : 1,147 images
Meningioma   : 1,329 images
No Tumor     : 1,067 images
Pituitary    : 1,457 images
```

> Note: StyleGAN2-ADA is an older NVIDIA research implementation. Its original software requirements may differ from current Google Colab Python/PyTorch versions.

## Tumor Segmentation

A segmentation stage is incorporated to emphasize relevant tumor regions in MRI images before deep feature extraction and classification.

## ResNet50 Feature Extraction

A pretrained ResNet50 model is used for deep feature extraction.

```text
Architecture       : ResNet50
Pretrained weights : ImageNet
include_top        : False
Pooling            : Global Average Pooling
Input size         : 224 × 224 × 3
Feature dimension  : 2048
```

## Hybrid CNN–ViT Classification

The classification stage combines convolutional representations with Vision Transformer representations for four-class brain tumor classification:

- Glioma
- Meningioma
- No Tumor
- Pituitary

## Evaluation Metrics

The framework can be evaluated using:

- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix
- Classification Report

## Technologies Used

- Python
- Google Colab
- PyTorch
- TensorFlow / Keras
- NumPy
- OpenCV
- Matplotlib
- scikit-learn
- scikit-image
- ResNet50
- U-Net / Segmentation
- StyleGAN2-ADA
- CNN
- Vision Transformer (ViT)

## Running the Project

### 1. Open Google Colab

Upload or open the project notebook.

### 2. Enable GPU

```text
Runtime → Change runtime type → GPU
```

A Tesla T4 GPU can be used for the experimental workflow.

### 3. Upload Dataset

Upload the dataset ZIP containing the `classification_task` directory.

### 4. Run the Pipeline

Execute the notebook stages sequentially:

```text
Dataset Loading
      ↓
Dataset Visualization
      ↓
Image Preprocessing
      ↓
StyleGAN Augmentation
      ↓
Tumor Segmentation
      ↓
ResNet50 Feature Extraction
      ↓
Hybrid CNN–ViT Classification
      ↓
Performance Evaluation
```

## Reproducibility

For reproducible experiments, report:

- Dataset source/version
- Train/test split
- Random seed
- Image size
- Preprocessing parameters
- Model architecture
- Batch size
- Learning rate
- Number of epochs
- StyleGAN configuration
- GPU configuration
- Python and framework versions

## Research Objective

The objective is to develop an automated MRI-based brain tumor classification framework by integrating synthetic data augmentation, tumor-region segmentation, deep feature extraction, and hybrid CNN–Transformer learning.

## Disclaimer

This repository is intended for academic and research purposes only. The developed models should not be considered a replacement for professional medical diagnosis or clinical decision-making.

## Citation

If you use this implementation in academic work, please cite the associated research paper and the original dataset/model sources used in the study.

## License

Add an appropriate open-source license before public distribution. Third-party libraries and research repositories should retain their respective licenses and copyright notices.
