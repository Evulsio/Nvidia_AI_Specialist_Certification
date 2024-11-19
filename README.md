# Nvidia AI Specialist Certification Project

## Fire Hydrant Detection and Classification System for Urban Safety

---

### Background Information

Fire hydrants play a critical role in urban fire response systems. However, locating hydrants quickly in complex urban environments can be challenging. Currently, manual methods are used to locate fire hydrants, which are time-consuming and prone to delays. This project aims to address these limitations by developing an AI-based system capable of detecting and classifying fire hydrants in real time.

---

### Project Description

This project aims to develop an AI-based fire hydrant detection system capable of identifying and classifying fire hydrants in real time. By accurately detecting fire hydrants' locations, the system can support emergency responses, reduce delays, and enhance urban fire safety.

---

### Current Limitations

- **Diverse Fire Hydrant Appearance:** Fire hydrants vary widely in color, size, and shape depending on the region, requiring extensive training data for accurate detection.
- **Complex Environments:** Fire hydrants are often partially obscured by vehicles, buildings, or other objects, which can impact detection performance.

---

### Video Acquisition

- Videos of indoor fire hydrants were captured in various controlled environments to create a robust dataset for training and validation. These scenarios included:
  - Fire hydrants located in corridors, parking lots, and building interiors
  - Fire hydrants observed from varying angles and distances

  Training Video
  - https://drive.google.com/drive/folders/1mJCcktAhYm8GLaX3lNCiNZZVsGtgNuev?usp=sharing
 
  Validation Video
  - https://drive.google.com/drive/folders/11LCP-HhQijT6ye0oaJKHa0C6FdKvZ-Er?usp=sharing

---

### Project Progress

#### **1. Image Preprocessing**
- Fire hydrant images were resized to **640 x 640** resolution to ensure compatibility with YOLOv5.
<p align="center">
    <img width="1263" alt="제목 없음" src="https://github.com/user-attachments/assets/17601312-27a0-41ef-bcfd-21e7d29d69d8">
    <img width="599" alt="제목 없음1" src="https://github.com/user-attachments/assets/e74f125e-c284-41b3-a345-9d3d972d34cd">
</p>


#### **2. Annotation with DarkLabel**
- **DarkLabel.exe** was used to annotate fire hydrants' positions in the dataset.
- Annotations were saved in `.txt` format following YOLOv5 requirements.

<p align="center">
    <img width="397" alt="제목 없음2" src="https://github.com/user-attachments/assets/e393a8a2-bfe7-4df5-acf3-83269648d945">
</p>

#### **3. Training Data with YOLOv5 in Colab**
- The YOLOv5 environment was set up on Google Colab, and the dataset was prepared for training.
<p align="center">
    <img width="499" alt="제목 없음3" src="https://github.com/user-attachments/assets/afa97dce-8a7a-4cef-b35c-d915cabb93e6">
</p>

- **Training Parameters:**
  - Image size: `-img 512`
  - Batch size: `-batch 16`
  - Epochs: `-epochs 300`
  - Data path: `-data /content/drive/MyDrive/yolov5/data.yaml`
  - Pre-trained weights: `-weights yolov5n.pt`

---

### 📊 Results

- **TensorBoard Visualization**
<p align="center">
    <img width="1021" alt="TensorBoard" src="https://github.com/user-attachments/assets/6bf8e38c-917d-48f2-aa70-9235c771e3b3">
</p>

- **Confusion Matrix**
<p align="center">
    <img width="1021" alt="Confusion Matrix" src="https://github.com/user-attachments/assets/95157031-186c-4d64-ae29-8ba3f515369f">
</p>

- **F1-Curve**
<p align="center">
    <img width="1021" alt="F1_curve" src="https://github.com/user-attachments/assets/acb571ca-0abe-4c1d-82ae-3a5a5247e683">
</p>

- **Sample Predictions**
<p align="center">
    <img src="https://github.com/user-attachments/assets/05554e53-2939-440c-ae01-25be157c62e6" width="300"/>
    <img src="https://github.com/user-attachments/assets/a7249530-4073-4455-a791-d390d21f437e" width="300"/>
</p>

---

### 🖥 Jetson Nano Deployment

- The trained model was deployed on Jetson Nano for real-time detection of fire hydrants.
- Jetson Nano ensures portability and efficiency in edge environments.

---

### 🎯 Future Work

- Expand the dataset to include diverse fire hydrant appearances across various regions.
- Improve detection performance in low-light or occluded scenarios.
- Integrate the system with GIS mapping to provide real-time fire hydrant locations.

---

### 🎥 Detection Videos

- [Detection Video 1](https://youtube.com/shorts/yhTtwcewjIc?si=bqMym3mMx-cj1yns)  
- [Detection Video 2](https://youtube.com/shorts/VWcLRW8vs0U?si=X9I6Jk7PkDOSeuwt)  
- [Detection Video 3](https://youtube.com/shorts/HcVqAKxXZP4?si=uQYc4MzfyEvo8hgA)
