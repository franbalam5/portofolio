---
title: "Chest X-Ray Classification with Vision Transformers"
date: 2024-05-18
description: "PyTorch deep learning pipeline for lung pathology detection using ViT and ResNet architectures."
icon: "fa-solid fa-x-ray"
accent: "purple"
status: "completed"
tags: ["python", "pytorch", "vision-transformers", "deep-learning", "medical-ai"]
draft: false
---

# Medical Image Classification with PyTorch & ViT

A computer vision project focused on automated classification of pathological findings in chest X-rays from public biomedical datasets.

![Training metrics and results](/images/projects/vit-metrics.png)
*Confusion matrix and loss curve comparison between convolutional and Transformer models.*

---

### Pipeline details

- **Architectures evaluated:** Direct comparison between standard convolutional models (**ResNet-50**) and pure attention-based models (**Vision Transformer / ViT-B/16**).
- **Class imbalance:** Implementation of weighted loss functions (*Focal Loss*) and data augmentation techniques specific to radiological images (bounded rotations, local contrast adjustments).
- **Evaluation:** Performance measured via ROC-AUC, macro-F1, and per-pathology accuracy.
