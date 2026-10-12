# Pothole-Detector
A computer vision project using YOLOv8 to detect road potholes in images with bounding boxes and confidence scores. Built with Python, Roboflow, and Google Colab.
# 🛣️ Road Pothole Detection Using YOLOv8

## 📌 Project Overview

Road Pothole Detection is a Computer Vision project that uses the YOLOv8 object detection model to identify potholes in road images. The system highlights detected potholes with bounding boxes and confidence scores.

## 🎯 Problem Statement

Road potholes can create safety risks for drivers and other road users. Manually inspecting roads takes time and effort. This project explores how computer vision can help identify potholes from road images.

## 💡 Proposed Solution

A YOLOv8 model is trained on an annotated pothole dataset obtained through Roboflow. The trained model processes road images and predicts pothole locations.

## ✨ Features

- Detect potholes in road images.
- Display bounding boxes around detected potholes.
- Show model confidence scores.
- Test the model on new road images.
- Save detection results for review.

## 🛠️ Technologies Used

- Python
- YOLOv8
- Ultralytics
- Roboflow
- PyTorch
- Google Colab
- OpenCV

## ⚙️ Project Workflow

1. Obtain an annotated pothole dataset.
2. Prepare the dataset in YOLO format.
3. Load the pretrained YOLOv8n model.
4. Train the model using the pothole dataset.
5. Evaluate the model on validation images.
6. Run inference on new road images.
7. Visualize and save the detection results.

## 📊 Initial Model Results

The initial 10-epoch training experiment produced these validation metrics:

| Metric | Result |
|---|---:|
| Precision | 65.8% |
| Recall | 53.0% |
| mAP@50 | 56.5% |
| mAP@50–95 | 20.8% |
| Validation images | 120 |

These are initial validation results, not a guarantee of performance on every road image.

## 🚀 How to Run

### Step 1: Open Google Colab

Open the project notebook in Google Colab.

### Step 2: Install dependencies

```bash
pip install ultralytics roboflow
```

### Step 3: Prepare the dataset

Download an annotated pothole dataset in YOLO format. Configure the dataset paths in `data.yaml`.

### Step 4: Train the model

```python
from ultralytics import YOLO

model = YOLO("yolov8n.pt")

model.train(
    data="/content/dataset/data.yaml",
    epochs=10,
    imgsz=640,
    batch=8
)
```

Update the dataset path to match your Colab environment.

### Step 5: Detect potholes

```python
from ultralytics import YOLO

model = YOLO(
    "/content/runs/detect/train/weights/best.pt"
)

results = model.predict(
    source="/content/road_image.jpg",
    conf=0.25,
    save=True
)
```

Replace the image path with the path of your test image. If your training run uses a different output directory, update the model path accordingly.

## ⚠️ Limitations

- Some small or distant potholes may not be detected.
- False detections and overlapping bounding boxes may occur.
- Detection performance can vary with lighting, water, road texture and image quality.
- Further training and evaluation are needed to improve reliability.

## 🔮 Future Enhancements

- Improve detection of small and distant potholes.
- Reduce duplicate and false detections.
- Add road video detection.
- Develop a simple web interface for image uploads.
- Explore pothole location reporting for road maintenance.

## 📁 Repository Contents

- `pothole_detection.ipynb` — project notebook.
- `README.md` — project documentation.
- `requirements.txt` — Python dependencies.
- `demo_result.jpg` — example detection output, if included.

## 👨‍💻 Project Purpose

Developed as a practical Computer Vision project for the HackZen 2.0 learning track.

## 📜 Acknowledgements

- Ultralytics for the YOLO framework.
- Roboflow for dataset management and annotation tools.

