# Nvidia AI Specialist Certification Project

## Fire Hydrant Detection System for Urban Safety

---

### 📋 Background Information

Fire hydrants are critical components of urban safety systems, ensuring quick access to water during emergencies. However, locating fire hydrants quickly in densely populated urban environments can be challenging. This project leverages AI to develop a system capable of detecting and identifying fire hydrants in real time, improving response times and aiding emergency services.

---

### 🎯 Project Description

This project uses YOLOv5 (You Only Look Once, Version 5) to create an AI-based fire hydrant detection system. The system is designed to identify and classify fire hydrants in real-time, even in complex urban environments. The goal is to provide accurate, real-time fire hydrant location data, improving situational awareness and optimizing emergency response efficiency.

---

### 🚧 Current Limitations

- **Environmental Complexity:** Urban areas often have high object density, leading to potential occlusion or distraction for the detection model.
- **Variability in Appearance:** Fire hydrants vary significantly in size, shape, and color across regions, requiring extensive training data to ensure robust detection.

---

### 📹 Dataset Acquisition

- Images of fire hydrants were collected from various environments, including:
  - Urban streets
  - Residential areas
  - Industrial zones
- The dataset was augmented with scenarios including partial occlusion, varying lighting conditions, and different angles to enhance model robustness.

---

### 🛠 Project Steps

#### **1. Image Preprocessing**
- Images were resized to **640 x 640** resolution for YOLOv5 compatibility.
- Example images:
  <p align="center">
    <img src="image1.png" width="300"/> <img src="image2.png" width="300"/>
  </p>

#### **2. Annotation with DarkLabel**
- **Process:**
  - Used `DarkLabel.exe` to annotate fire hydrants in the collected images.
  - Saved the labels in `.txt` format compatible with YOLOv5 requirements.

<p align="center">
    <img src="darklabel_image.png" width="400"/>
</p>

#### **3. Model Training with YOLOv5**
- **Setup:**
  - Cloned the YOLOv5 repository in Google Colab.
  - Split the dataset into training and validation sets.

<p align="center">
    <img src="colab_setup.png" width="400"/>
</p>

- **Training Parameters:**
  - `img`: 512 (image size)
  - `batch`: 16 (batch size)
  - `epochs`: 300 (number of iterations)
  - `data.yaml`: Contains paths and class details
  - Pre-trained weights: `yolov5n.pt`

#### **4. Results**
- **Metrics:**
  - TensorBoard outputs:
    <p align="center">
      <img src="tensorboard_image.png" width="400"/>
    </p>
  - Confusion Matrix, F1-Curve, and P-Curve.

- **Sample Outputs:**
  - Predicted bounding boxes:
    <p align="center">
      <img src="val_batch0_pred.png" width="300"/> <img src="val_batch1_pred.png" width="300"/>
    </p>

---

### 🖥 Jetson Nano Deployment

- The trained model was deployed on Jetson Nano for real-time fire hydrant detection.
- Edge deployment ensures the system is portable and scalable for on-site use.

---

### 🎯 Future Work

- Collect and annotate additional datasets to include regional variations in fire hydrants.
- Improve detection performance in environments with significant occlusion or low visibility.
- Integrate the system with mapping tools for enhanced geolocation capabilities.

---

### 📂 Repository Structure

