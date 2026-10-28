# LIFT: A Lightweight Image Forensics Framework for Tampering Detection and Localization

**LIFT** is a lightweight deep learning framework for detecting and localizing image tampering. It combines complementary forensic representations with a U-Net-based localization network and a CNN-based classifier to perform both pixel-level tampering localization and image-level detection.

## Overview

Image manipulation can undermine the authenticity of digital media and enable document fraud. LIFT investigates whether a compact deep learning architecture can identify manipulated regions without relying on camera-specific reference information. It also explores the relevance of various forensic cues in Image tampering detection.

The framework combines three input representations:

- **RGB images** 
- **Error Level Analysis (ELA)** 
- **Noise residuals** 

## Overall Architecture

<img width="1432" height="548" alt="Overall" src="https://github.com/user-attachments/assets/28e6dfa6-c6c2-41e7-a7fe-16893ce25dd4" />

## Key Features

- **Joint detection and localization:** Produces pixel-level tampering maps and image-level predictions.
- **Multi-representation analysis:** Combines RGB, ELA, and noise residuals to exploit complementary forensic information.
- **Compact architecture:** Contains approximately **2.49 million trainable parameters** with a reported model size of **9.50 MB**.


## Experimental Results

LIFT was evaluated on four image-forensics datasets: **CASIA 1.0, CASIA 2.0, Columbia, and In-The-Wild**. Image-level metrics evaluate the binary classifier, while Pixel AUC evaluates the localization network.

### Quantitative Results

| Dataset | Accuracy (%) | F1 Score (%) | Image-level AUC (%) | Pixel AUC (%) |
|:--|--:|--:|--:|--:|
| CASIA 1.0 | 81.40 | 81.82 | 88.26 | 85.27 |
| CASIA 2.0 | 91.83 | 89.95 | 96.87 | 93.51 |
| Columbia | 89.04 | 89.19 | 90.83 | 89.05 |
| In-The-Wild | — | — | — | 71.82 |

*Note: Image-level detection metrics are not reported for In-The-Wild because the evaluated dataset contains only tampered images.*

### Qualitative Results

#### CASIA

<img width="1684" height="1694" alt="CASIA-Results" src="https://github.com/user-attachments/assets/5c0f7759-5613-41de-8776-cb4211bea043" />

#### Columbia

<img width="1313" height="1330" alt="Columbia_Results" src="https://github.com/user-attachments/assets/3f88e96d-75c5-44d4-9ec2-9b1f20fa72aa" />

#### In-The-Wild

<img width="1233" height="1253" alt="ITW_Results" src="https://github.com/user-attachments/assets/9f93d376-d8b2-4ec5-8f4c-aabcdbaa64dd" />

### Ablation Study

The ablation study examines the contributions of RGB, ELA, and noise residual representations.

| Configuration | F1 Score (%) | Pixel AUC (%) |
|:--|--:|--:|
| RGB only | 45.32 | 72.49 |
| ELA only | 89.13 | 92.31 |
| Noise residual only | 83.10 | 84.05 |
| All representations | 89.95 | 93.51 |

The results show that ELA is the strongest individual representation in the evaluated configuration, while combining all three representations achieves the highest Pixel AUC among these configurations.

## Model Complexity

| Component | Trainable Parameters | Model Size |
|:--|--:|--:|
| U-Net localization network | 483,601 | 1.84 MB |
| CNN classifier | 2,005,889 | 7.65 MB |
| **Combined framework** | **2,489,490** | **9.50 MB** |

The combined model requires approximately **3.21 GFLOPs per inference**, based on the experimental evidence.

## Repository Contents

This repository accompanies the LIFT research project on image tampering detection and localization.

The repository is intended to contain the model implementations, preprocessing procedures, evaluation scripts, and experimental configurations used in the study.

## Acknowledgements

This work was conducted at the Indian Institute of Technology Patna.
