---
title: "Chest X-Ray Classification with Vision Transformers"
date: 2026-05-11
description: "PyTorch deep learning pipeline for lung pathology detection using ViT and ResNet architectures."
icon: "fa-solid fa-x-ray"
accent: "purple"
status: "completed"
tags: ["python", "pytorch", "vision-transformers", "deep-learning", "medical-ai"]
draft: false
math: true
---

# Medical Image Classification with PyTorch & ViT

A computer vision project focused on the automated classification of pathological findings in chest X-rays. By leveraging attention-based deep learning architectures, this pipeline acts as an automated triage assistant to help radiologists rapidly identify critical lung conditions.

![Qualitative Error Analysis](/images/projects/vit-metrics.png)
*Qualitative model confidence analysis: Excellent predictions ($>99\%$ confidence), Intermediate cases (anatomical variations), and Errors (subtle boundary between healthy tissue and early opacity).*

---

## Problem Statement & Dataset

Fast and accurate diagnosis of pulmonary diseases is critical in clinical settings. Chest X-rays are highly accessible, but visual analysis is prone to human error when distinguishing between overlapping pathologies. 

The project utilizes the **COVID-19 Radiography Database** (21,165 images) to classify scans into four distinct categories:
* **COVID-19** (542 test samples)
* **Viral Pneumonia** (202 test samples)
* **Lung Opacity / Non-COVID** (902 test samples)
* **Normal / Healthy** (1,529 test samples)

**The core challenge:** The dataset presents a massive class imbalance, with healthy lungs outnumbering viral pneumonia cases by nearly 8 to 1. 

## Technical Implementation

To solve this multiclase problem, the project implements a complete PyTorch pipeline prioritizing a purely attention-based approach over traditional CNNs.

### Architecture: Vision Transformer (ViT-B/16)
Instead of processing the image pixel-by-pixel, the Vision Transformer divides the $224 \times 224$ X-ray into $16 \times 16$ patches. Using 12 layers of Multi-Head Self-Attention, the model evaluates the global context of the lung from the very first layer. 
* **Transfer Learning:** The model was initialized with ImageNet-1K weights.
* **Fine-Tuning:** The original classification head was replaced with a 4-neuron linear layer, and the entire network was fine-tuned end-to-end to adapt its visual sensitivity to radiological textures.

### Mitigating Data Imbalance
To prevent the model from becoming biased toward the majority "Normal" class, two key engineering decisions were made:
1. **Weighted Random Sampler:** Applied to the PyTorch DataLoader to ensure underrepresented classes were sampled more frequently during training.
2. **Focal Loss:** Replaced standard Cross-Entropy. Focal Loss dynamically scales the loss based on prediction confidence, forcing the optimizer to focus heavily on the hard-to-classify examples:
   $$\mathcal{L}_{FL} = - (1-p_t)^\gamma \log(p_t)$$

### Training Dynamics
* **Optimizer & Scheduler:** AdamW (`lr=1e-4`, `weight_decay=0.01`) paired with **OneCycleLR** to ensure stable convergence.
* **Early Stopping:** Triggered at epoch 11 (with optimal weights restored from epoch 6) to prevent overfitting on the training set.

## Results & Evaluation

The model achieves state-of-the-art performance for this specific multi-class task, demonstrating exceptional capability in isolating disease features.

| Metric | Score |
| :--- | :--- |
| **Global Accuracy** | 94.33% |
| **Macro Precision** | 95.51% |
| **Macro Recall** | 94.19% |
| **Macro F1-Score** | 94.80% |

### One-vs-Rest ROC-AUC
Because standard ROC curves are binary, a **One-vs-Rest (OvR)** strategy was implemented to evaluate the model's underlying discriminative power for each class. 
* **COVID-19:** 0.997 AUC
* **Normal:** 0.998 AUC
* **Viral Pneumonia:** 0.999 AUC
* **Lung Opacity:** 0.988 AUC

*Clinical Insight:* The Lung Opacity class presented the lowest F1-Score (0.92). The confusion matrix revealed this class heavily overlaps visually with healthy dense tissue, accurately reflecting the real-world diagnostic challenge faced by human radiologists. 

## Qualitative Error Analysis

Beyond raw metrics, model certainty was audited using Softmax probability distributions. This analysis revealed:
* **High Confidence ($>99\%$):** Flawless detection of classic "ground-glass" patterns in COVID-19.
* **Intermediate Confidence ($\sim 50\%$):** The model correctly predicted the class but hesitated due to anatomical rotations or medical artifacts (e.g., pacemaker wires).
* **Errors (False Confidence):** Misclassifications largely occurred in under-exposed X-rays where diffuse opacities mimicked normal healthy tissue.

---
**Tech Stack:** `Python`, `PyTorch`, `Torchvision`, `Scikit-learn`, `Matplotlib`, `Seaborn`.