# Real-Time UAV Traffic Analysis and Detection Using YOLOv11

A deep learning-based traffic detection system that uses **YOLOv11** to identify and classify vehicles, pedestrians, and other road users in UAV aerial imagery. The project provides a modular framework for model training, evaluation, image and video inference, and traffic scene analysis.

## Project Overview

Traffic monitoring from UAV imagery can be challenging because of small objects, crowded roads, different viewing angles, and changing environmental conditions. This project explores the use of YOLOv11 for detecting multiple road-user categories from aerial traffic scenes.

The system supports 10 object classes: pedestrian, people, bicycle, car, van, truck, tricycle, awning-tricycle, bus, and motor.

The project is organized into separate modules, making it easier to train models, evaluate detection performance, process videos, and extend the system for future research.

## Key Features

- **YOLOv11 Object Detection:** Detects and classifies 10 traffic-related object categories.
- **UAV Traffic Monitoring:** Supports object detection from aerial images and recorded videos.
- **Modular Architecture:** Separates training, validation, inference, and traffic analytics.
- **Detection Visualization:** Displays bounding boxes, class labels, and confidence scores.
- **Traffic Object Counting:** Provides class-wise detection counts for traffic scene analysis.
- **Model Evaluation:** Measures precision, recall, mAP@50, and mAP@50–95.
- **GPU Support:** Supports CUDA acceleration for training and inference on compatible hardware.
- **Research-Friendly Structure:** Includes configuration files, unit tests, and technical documentation.

## Model Performance

The trained model was evaluated on **548 validation images containing 38,759 annotated objects**.

| Evaluation Metric | Result |
|---|---|
| Precision | 55.0% |
| Recall | 42.8% |
| mAP@50 | 44.1% |
| mAP@50–95 | 26.7% |
| Validation Images | 548 |
| Total Instances | 38,759 |
| Detection Classes | 10 |

### Class-Wise Detection Results

| Object Class | Precision | Recall | mAP@50 | mAP@50–95 |
|---|---:|---:|---:|---:|
| Pedestrian | 57.5% | 44.9% | 48.7% | 22.9% |
| People | 61.3% | 32.7% | 38.1% | 15.4% |
| Bicycle | 33.8% | 20.2% | 18.3% | 8.25% |
| Car | 76.1% | 79.0% | 81.5% | 59.0% |
| Van | 54.7% | 46.5% | 45.9% | 32.5% |
| Truck | 56.2% | 38.1% | 41.1% | 27.9% |
| Tricycle | 44.5% | 37.7% | 33.6% | 18.9% |
| Awning-tricycle | 36.0% | 21.2% | 18.8% | 11.7% |
| Bus | 75.2% | 57.9% | 65.1% | 47.5% |
| Motor | 54.9% | 49.8% | 49.7% | 23.2% |

The model performs particularly well on cars and buses, while smaller objects such as bicycles and awning-tricycles remain challenging. These results highlight opportunities for improving small-object detection and recall in complex UAV traffic scenes.

## Project Architecture

The project follows a modular workflow:

**Dataset Preparation → YOLOv11 Training → Model Validation → Image/Video Detection → Traffic Analysis → Result Visualization**

The main components include:

| Component | Purpose |
|---|---|
| Training Module | Train and fine-tune YOLOv11 |
| Evaluation Module | Evaluate detection accuracy |
| Detection Module | Run inference on images and videos |
| Video Processing Module | Process and annotate video frames |
| Traffic Analytics Module | Generate class-wise object counts |
| Configuration Module | Manage dataset and model settings |
| Testing Module | Validate core functionality |

## Technologies Used

- **Python:** Main programming language
- **YOLOv11 / Ultralytics:** Object detection framework
- **PyTorch:** Deep learning backend
- **OpenCV:** Image and video processing
- **CUDA:** GPU acceleration
- **NumPy:** Numerical processing
- **Matplotlib:** Performance visualization

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/Real-Time-UAV-Traffic-Detection-YOLOv11.git
cd Real-Time-UAV-Traffic-Detection-YOLOv11
```

Replace `YOUR_USERNAME` with your GitHub username.

### 2. Install Dependencies

Make sure Python and the required dependencies are installed.

```bash
pip install -e .
```

### 3. Prepare the Dataset

Organize the dataset using the YOLO detection format, with separate image and annotation directories for training and validation.

Update the dataset paths in:

```text
configs/data.yaml
```

The dataset configuration must define the 10 object categories in the correct class order.

## Model Training

Train YOLOv11 using the configured dataset:

```bash
uav-traffic train \
  --data configs/data.yaml \
  --model yolo11s.pt \
  --epochs 100 \
  --device 0
```

Training parameters can be adjusted according to the dataset size, GPU resources, and experimental requirements.

## Model Evaluation

Evaluate the trained model using the validation dataset:

```bash
uav-traffic validate \
  --weights runs/detect/train/weights/best.pt \
  --data configs/data.yaml \
  --device 0
```

The evaluation reports precision, recall, mAP@50, and mAP@50–95 for the overall dataset and individual classes.

## Object Detection and Traffic Analysis

The project includes modules for image inference, video processing, and traffic object counting.

The detection pipeline can generate:

- Bounding boxes around detected road users.
- Predicted object categories.
- Confidence scores for individual detections.
- Class-wise object counts.
- Annotated frames for traffic scene visualization.

Object counts are based on detections within individual frames and should not be interpreted as unique vehicle counts across an entire video without an additional tracking mechanism.

## Applications

The project can be used as a research foundation for:

- UAV-based road traffic monitoring.
- Vehicle and pedestrian detection.
- Urban traffic scene analysis.
- Intelligent transportation systems.
- Road safety and traffic surveillance research.
- Aerial object detection benchmarking.

## Current Limitations

The current validation results indicate that some classes, particularly bicycles and awning-tricycles, are difficult to detect reliably.

Performance can also vary with UAV altitude, camera angle, image resolution, traffic density, and lighting conditions.

Although the system supports video inference, real-time deployment performance has not yet been established through a documented FPS or latency benchmark.

## Future Improvements

Planned improvements include:

- Improving detection of small and distant traffic objects.
- Evaluating different YOLOv11 model sizes.
- Introducing object tracking for unique vehicle counting.
- Exploring traffic density estimation.
- Optimizing inference latency for real-time UAV deployment.
- Testing model robustness under different aerial viewing conditions.
- Expanding evaluation to additional UAV traffic datasets.

## Documentation

Additional documentation is available in the `docs/` directory:

- `SETUP.md` — Installation and environment configuration.
- `DATASET.md` — Dataset preparation and class definitions.
- `USAGE.md` — Training, evaluation, and inference instructions.
- `EVALUATION.md` — Evaluation metrics and experimental reporting.
- `LIMITATIONS.md` — Current limitations and future development.

## Contributing

Contributions, suggestions, and improvements are welcome. Please refer to `CONTRIBUTING.md` for contribution guidelines.

## Acknowledgments

This project uses the Ultralytics YOLO framework and open-source Python libraries for object detection, deep learning, and computer vision. Their contributions support research and development in UAV-based intelligent traffic monitoring.
