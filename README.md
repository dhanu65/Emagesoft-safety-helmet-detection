# Safety Helmet Object Detection using YOLO11n

## Project Overview

This project implements an object detection system for detecting safety-related objects in construction-site images using YOLO11n.

The model detects three classes:

- Helmet
- Head
- Person

The project was completed as a technical assignment for an ML/DL Engineer (Computer Vision) role.

## Dataset

The project uses the Safety Helmet Detection (Hard Hat Detection) dataset from Kaggle.

Dataset source: https://www.kaggle.com/datasets/andrewmvd/hard-hat-detection

The dataset contains 5,000 construction-site images with PASCAL VOC XML bounding-box annotations.

## Methodology

The project follows these steps:

- Dataset exploration and class distribution analysis
- Bounding-box size analysis
- PASCAL VOC XML annotation parsing
- Conversion of PASCAL VOC annotations to YOLO format
- Reproducible 80:20 train/validation split
- YOLO11n transfer learning using pretrained weights
- Model training on a Tesla T4 GPU
- Evaluation using precision, recall, mAP@0.5 and mAP@0.5:0.95
- Confusion matrix and training/validation loss analysis
- Inference on unseen validation images
- Failure-case analysis

## Model and Training Configuration

| Parameter | Value |
|---|---|
| Model | YOLO11n |
| Pretrained weights | COCO pretrained |
| Image size | 640 × 640 |
| Batch size | 16 |
| Epochs | 30 |
| Train/Validation split | 80:20 |
| Random seed | 42 |
| GPU | NVIDIA Tesla T4 |
| Augmentation | Default Ultralytics YOLO augmentations |

## Results

The trained model achieved:

- **Precision:** 0.943
- **Recall:** 0.594
- **mAP@0.5:** 0.635
- **mAP@0.5:0.95:** 0.418

### Per-class performance

| Class | Precision | Recall | mAP@0.5 | mAP@0.5:0.95 |
|---|---:|---:|---:|---:|
| Helmet | 0.957 | 0.899 | 0.967 | 0.643 |
| Head | 0.872 | 0.883 | 0.917 | 0.601 |
| Person | 1.000 | 0.000 | 0.021 | 0.009 |

The helmet and head classes were detected considerably better than the person class. The person class had substantially fewer annotated instances than the helmet and head classes, which likely contributed to its poor recall.

## Failure Analysis

The model performed well on many unseen validation images but also showed several failure cases.

Examples include:

- Missing some helmet detections in crowded or complex scenes.
- Producing an additional head prediction in some images.
- Missing person detections in an image containing multiple annotated persons.

These failures are discussed and visualized in the Jupyter Notebook.

## Repository Contents

```text
Emagesoft-safety-helmet-detection/
├── Emagesoft_safety_helmet_detection.ipynb
├── requirements.txt
├── best.pt
└── README.md
