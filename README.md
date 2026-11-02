# Optimized Real-Time Vehicle Detection via Transfer Learning (YOLOv5)

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white)](https://pytorch.org/)
[![YOLOv5](https://img.shields.io/badge/YOLOv5-v6.1-00FFFF)](https://github.com/ultralytics/yolov5)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

An end-to-end computer vision pipeline for multi-class vehicle detection, trained on a curated subset of MS COCO 2017 using **YOLOv5m** and **Transfer Learning**. Designed for dynamic traffic monitoring, intelligent transportation systems (ITS), and low-latency edge deployment.

---

## Key Features & Technical Highlights

- **Domain-Specific Dataset Curation:** Filtered and refined a raw 47 GB MS COCO 2017 dataset down to a highly optimized **1.2 GB vehicle subset** across 5 target classes (`Car`, `Bus`, `Truck`, `Motorcycle`, `Bicycle`).
- **Transfer Learning Optimization:** Fine-tuned pre-trained COCO weights using CSPDarknet53 backbone with FPN + PANet neck architecture to dramatically reduce convergence time and prevent overfitting.
- **Robust Field Performance:** High detection precision under real-world challenges such as partial occlusion, high-density traffic, dynamic lighting, and variable object scales.
- **Data-Centric Engineering:** Resolved background noise, erroneous ground-truth annotations, and extreme class imbalance prior to model convergence.

---

## Benchmark Performance & Key Metrics

After targeted hyperparameter tuning and manual dataset sanitation, the model achieved impressive metrics on the verification set:

| Metric | Score / Value | Description |
| :--- | :--- | :--- |
| **Precision** | **84.2%** (0.842) | Low false-positive rate; reliably isolates background noise |
| **Recall** | **79.5%** (0.795) | High sensitivity; minimizes missed vehicle detections |
| **mAP@0.5** | **83.7%** (0.837) | Outstanding overall performance at standard IoU threshold |
| **mAP@0.5:0.95** | **60.6%** (0.606) | Outperforms standard baseline YOLOv5m benchmark (~45.4%) |

---

## Tech Stack & Hardware Setup

- **Frameworks & Libraries:** PyTorch, Ultralytics YOLOv5, OpenCV, NumPy, Pandas, Matplotlib
- **Compute Infrastructure:** Google Colab Virtual Machine
- **GPU Accelerator:** NVIDIA Tesla T4 GPU (16 GB VRAM)
- **CPU:** Intel Xeon @ 2.20GHz (12.7 GB System RAM)
- **Training Config:** Input Resolution `640x640` | Epochs `50` | Batch Size `16` | Optimizer `SGD (lr=0.01)` | IoU Threshold `0.45` | Confidence Threshold `0.25`

---

## Methodology Overview
1. Preprocessing & Filtering: Extracted target vehicle instances (Car, Bus, Truck, Motorcycle, Bicycle) from .json COCO metadata and converted annotations to normalized YOLO (x_center, y_center, width, height) text files.

2. Fine-Tuning: Applied SGD optimization across pre-trained weights. Leveraging FPN (Feature Pyramid Network) and PANet allowed effective feature fusion across varying image scales.

3. Post-Processing (NMS): Utilized Non-Maximum Suppression with an IoU threshold of 0.45 to eliminate redundant bounding boxes around overlapping vehicles in congested scenes.

## 👥 Authors & Team
Vildan Yılmazer - Electrical & Electronics Engineer | Project Lead / System Architecture & Software Integration

Metehan Tırpan - Electrical & Electronics Engineer | Data Engineering & Optimization

Seher Bozbıyık - Electrical & Electronics Engineer | Data Engineering & Metric Analysis

Kırıkkale University - Department of Electrical and Electronics Engineering

📜 License
This project is open-source and available under the MIT License
