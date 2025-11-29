# Automatic Number Plate Detection System using YOLO v11

<p align="center">
  <img src="https://github.com/Tanomichikki/Vehicle-Number-Plate-Detection-System/blob/main/license-plate.jpg" width="60%" />
</p>



### 1. Overview

This project is an Automatic Number Plate Detection and OCR System designed for real-time applications such as traffic surveillance, law enforcement, tolling, and parking automation.
It uses YOLO v11 (Ultralytics) for number plate detection and PaddleOCR for extracting alphanumeric text from the detected plates.
The processed data is stored in a MySQL database (XAMPP) for retrieval, analytics, or system integration.



### 2. Key Features

- Real-time number plate detection using YOLO v11

- High-accuracy OCR using PaddleOCR (PaddlePaddle)

- Built with Python, OpenCV, and Ultralytics

- Processes frames/images from webcam or uploaded files

- Stores recognized plates and timestamps in MySQL

- Supports custom datasets trained with COCO augmentation

- Scalable for smart-city and security applications



### 3. Architecture

<p align="center">
  <img src="https://github.com/Tanomichikki/Vehicle-Number-Plate-Detection-System/blob/main/Architecture-Design.png" width="70%" />
</p>



### 4. Tech Stack

- Machine Learning & Vision

- YOLO v11 (Ultralytics)

- PaddleOCR (PaddlePaddle)

- OpenCV

- Python

**Backend**

- XAMPP (MySQL Database)

- Flask/FastAPI (optional for API integration)

**Dataset**

- Custom dataset enhanced with COCO images

- Annotated number plates in YOLO format

<p align="center">
  <img src="https://github.com/Tanomichikki/Vehicle-Number-Plate-Detection-System/blob/main/coco-model-dataset.jpg" width="70%" />
</p>



### 5. Installation & Setup

**1. Clone this repository**
```bash
git clone https://github.com/your-username/ANPR-YOLOv11.git
```
```bash
cd ANPR-YOLOv11
```

**2. Install Python dependencies**
pip install ultralytics paddlepaddle paddleocr opencv-python mysql-connector-python numpy


**⚠️ For GPU acceleration, install the CUDA version of PaddlePaddle.**



### 6. Model Setup

**1. YOLO v11 Model**

Place your trained YOLO v11 model in:
```bash
/models/yolov11-licenseplate.pt
```

**2. PaddleOCR**

No extra setup needed — PaddleOCR downloads its model automatically.


**Database Setup (XAMPP MySQL)**

Create a database:

```sql
CREATE DATABASE anpr_system;
```

**Create a table:**

```sql
CREATE TABLE plates (
    id INT AUTO_INCREMENT PRIMARY KEY,
    plate_number VARCHAR(20),
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

**Update database credentials in:**
```bash
config/db_config.py
```



### 7. Usage

**Run detection on images**

```bash
python detect.py --image sample.jpg
```

**Run real-time detection (webcam)**

```bash
python detect.py --realtime
```
**Detection Script Flow**

- YOLO v11 detects plate region

- PaddleOCR extracts text

- Plate number is inserted into MySQL

- Outputs are saved under /output/



### 8. Dataset

- Custom dataset manually annotated for number plates

- Additional images taken from COCO dataset

- Annotated using LabelImg / Roboflow in YOLO format

- Trained using Ultralytics YOLO training pipeline

**Training example:**
```bash
yolo train model=yolov11n.pt data=data.yaml epochs=100 imgsz=640
```



### 9. Results

- Achieved high accuracy on plate localization in various lighting and environmental conditions

- Reliable OCR extraction using PaddleOCR

- Real-time performance with GPU acceleration


```bash
/results/detection_sample_1.jpg
```
```bash
/results/detection_sample_2.jpg
```

<p align="center">
  <img src="https://github.com/Tanomichikki/Vehicle-Number-Plate-Detection-System/blob/main/number-plate-dataset-.png" width="70%" />
</p>



### 10. Future Enhancements

- Deploy as a cloud API (AWS Lambda + API Gateway)

- Integrate with IoT cameras for smart parking

- Add vehicle detection + plate matching

- Dashboard for analytics (Streamlit / React)
