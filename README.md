# Real-Time UAV Traffic Analysis and Detection Using YOLOv11

A deep learning-based UAV traffic monitoring system developed using **YOLOv11** for detecting and classifying vehicles, pedestrians, and other road users in aerial imagery. The project provides a modular framework for object detection, model training, performance evaluation, video processing, and traffic scene analysis.

The project focuses on high-accuracy traffic detection, with a research goal of achieving **85%+ detection performance** through optimized training, improved image processing, and small-object detection techniques.

## Project Overview

UAV-based traffic monitoring has become an important area of research in intelligent transportation systems, urban traffic management, and road safety. Detecting objects from aerial imagery remains challenging because of small object sizes, crowded roads, complex backgrounds, and changing camera perspectives.

This project uses YOLOv11 to detect and classify 10 traffic-related categories: pedestrians, people, bicycles, cars, vans, trucks, tricycles, awning-tricycles, buses, and motorcycles.

The system supports image and video inference, traffic object counting, detection visualization, and model evaluation. Its modular design allows researchers and developers to extend the framework for additional traffic analysis applications.

## Key Features

- **YOLOv11 Object Detection:** Detects and classifies 10 traffic-related object categories.
- **UAV Traffic Monitoring:** Supports aerial image and video analysis.
- **High-Accuracy Detection:** Designed with an 85%+ mAP@50 research target.
- **Small-Object Detection:** Focuses on improving detection of distant vehicles, pedestrians, and bicycles.
- **Detection Visualization:** Displays bounding boxes, object labels, and confidence scores.
- **Traffic Analytics:** Provides frame-level object counting and traffic scene information.
- **GPU Acceleration:** Supports CUDA-enabled model training and inference.
- **Modular Architecture:** Separates training, evaluation, inference, and traffic analytics.

## Model Performance

### Performance Objectives

The project aims to improve detection accuracy across all 10 traffic-related classes.

| Evaluation Metric | Performance Target |
|---|---:|
| Precision | 90.2% |
| Recall | 87.5% |
| mAP@50 | 89.3% |
| mAP@50–95 | 85.1% |
| Detection Classes | 10 |

**Performance note:** These values are proposed targets for future experiments, not measured results. Actual performance will be reported after model training and independent validation.

### Detection Categories

| Class ID | Object Class |
|---|---|
| 0 | Pedestrian |
| 1 | People |
| 2 | Bicycle |
| 3 | Car |
| 4 | Van |
| 5 | Truck |
| 6 | Tricycle |
| 7 | Awning-tricycle |
| 8 | Bus |
| 9 | Motor |

## Results

<img width="256" height="256" alt="F1_curve" src="https://github.com/user-attachments/assets/9100d5b7-e8c4-40ed-8928-3c17b194be4e" /> <img width="256" height="256" alt="PR_curve" src="https://github.com/user-attachments/assets/20d3d0c5-a0a5-48e6-950c-acdc01179f37" />






## Project Architecture

The system follows a modular workflow:

**UAV Dataset → Data Preparation → YOLOv11 Training → Model Evaluation → Image/Video Detection → Traffic Analytics → Visualization**

| Module | Description |
|---|---|
| Training Module | Train and fine-tune YOLOv11 models |
| Evaluation Module | Evaluate object detection performance |
| Detection Module | Detect objects in images and videos |
| Video Processing Module | Process and annotate video frames |
| Traffic Analytics Module | Generate class-wise detection counts |
| Configuration Module | Manage dataset and model settings |
| Testing Module | Validate core software functionality |

## Technologies Used

- **Python:** Main programming language
- **Ultralytics YOLOv11:** Object detection framework
- **PyTorch:** Deep learning backend
- **OpenCV:** Image and video processing
- **CUDA:** GPU acceleration
- **NumPy:** Numerical computation
- **Matplotlib:** Visualization and performance analysis

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/Real-Time-UAV-Traffic-Detection-YOLOv11.git
cd Real-Time-UAV-Traffic-Detection-YOLOv11
```

Replace `YOUR_USERNAME` with your GitHub username.

### 2. Install Dependencies

```bash
pip install -e .
```

### 3. Prepare the Dataset

Organize the dataset using the YOLO object detection format, with separate directories for training and validation images and labels.

Update the dataset configuration in:

```text
configs/data.yaml
```

Ensure the class indices match the annotation labels.

## Model Training

Train the YOLOv11 model using:

```bash
uav-traffic train \
  --data configs/data.yaml \
  --model yolo11s.pt \
  --epochs 100 \
  --device 0
```

Training parameters can be adjusted according to the available computational resources and dataset characteristics.

## Model Evaluation

Evaluate the trained model using:

```bash
uav-traffic validate \
  --weights runs/detect/train/weights/best.pt \
  --data configs/data.yaml \
  --device 0
```

The evaluation process calculates precision, recall, mAP@50, and mAP@50–95.

## Performance Optimization

The project investigates several approaches to improving detection accuracy.

### Higher-Resolution Training

Evaluate input resolutions of 960 × 960 and 1280 × 1280 to preserve more visual details of small objects.

### Data Augmentation

Explore:

- Mosaic augmentation
- Multi-scale training
- Random cropping and scaling
- Brightness and contrast adjustment
- Horizontal flipping

### Model Optimization

Compare different YOLOv11 configurations and optimize training hyperparameters to improve detection performance.

### Small-Object Detection

Investigate detection challenges involving distant vehicles, bicycles, pedestrians, and other small objects commonly found in UAV imagery.

### Real-Time Inference

Evaluate inference latency and processing speed to assess suitability for UAV traffic monitoring applications.

## Object Detection and Traffic Analysis

The system supports:

- Vehicle and pedestrian detection.
- Object classification.
- Bounding-box visualization.
- Detection confidence scores.
- Frame-level traffic object counting.
- Annotated image and video generation.

Traffic object counts are calculated per frame. Unique vehicle counting across frames requires an additional object-tracking component.

## Applications

- UAV-based traffic surveillance.
- Intelligent transportation systems.
- Smart city traffic monitoring.
- Vehicle and pedestrian detection.
- Urban traffic scene analysis.
- Road safety monitoring.
- Aerial object detection research.

## Future Improvements

Planned improvements include:

- Improving overall object detection accuracy.
- Enhancing detection of small and distant objects.
- Optimizing YOLOv11 training configurations.
- Introducing multi-object tracking.
- Developing traffic density estimation.
- Improving real-time inference performance.
- Testing model robustness under different aerial conditions.
- Evaluating performance on additional UAV traffic datasets.

## Documentation

Detailed documentation is available in the `docs/` directory:

- `SETUP.md` — Installation and environment setup.
- `DATASET.md` — Dataset preparation and configuration.
- `USAGE.md` — Training, evaluation, and inference instructions.
- `EVALUATION.md` — Performance evaluation procedures.
- `LIMITATIONS.md` — Known limitations and future development.

## Contributing

Contributions, suggestions, and improvements are welcome. Please refer to `CONTRIBUTING.md` for contribution guidelines.

## Acknowledgments

This project uses the Ultralytics YOLO framework and open-source computer vision libraries. Their contributions support research and development in UAV-based intelligent traffic monitoring and object detection.
