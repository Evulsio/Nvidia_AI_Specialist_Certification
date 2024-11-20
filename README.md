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


#### **2. DarkLabel (labels)**
- **Go to the DarkLabel.exe file**

<p align="center"><img src="https://github.com/user-attachments/assets/19032ef7-210f-4e48-abe7-ab7788357ac0">

- Click on "Open Video" to select the video for training.

<p align="center"><img src="https://github.com/user-attachments/assets/b6b8ce28-e856-4a14-9b26-377f005ba50e">

<p align="center"><img src="https://github.com/user-attachments/assets/4b59e95f-5828-4e65-abb5-bbcadb55a927"><img src="https://github.com/user-attachments/assets/a053fa82-d413-4acb-b6cf-d9ed39db2063">

- Ensure that it is set to "fireplug," then set it to "box + Label," uncheck "labeled frames only," and proceed with labeling
<p align="center"><img src="https://github.com/user-attachments/assets/24b5e6d7-f9f9-461b-8cfa-aef7c73a49b9"width="500" height="600"/>

- After completing the labeling, click the "GT SAVE AS" button, select a folder, and save. You can then confirm that the labels are saved in a .txt file format.
<p align="center"><img src="https://github.com/user-attachments/assets/3f482bc7-6c48-437b-9084-a6498170f543"><img src="https://github.com/user-attachments/assets/796fa33c-cb43-431b-9399-0812aaa06647">

- Check extracted labeling
<p align="center"><img src="https://github.com/user-attachments/assets/6583e5f3-1b8c-41bf-b6c6-9b43eb8c2651">
  
#### **3. Training Data with YOLOv5 in Colab**
- Link your Google Drive to Colab

<img width="620" alt="제목 없음1" src="https://github.com/user-attachments/assets/e89b00e9-ebb4-475c-ac82-e282ad3628d4">

- Clone and install the yolov5 repertoire.

<img width="606" alt="제목 없음2" src="https://github.com/user-attachments/assets/6f25fe90-c2c5-4e99-84ca-2bb9db31728d">

- Creating Validation Data

<img width="586" alt="제목 없음3" src="https://github.com/user-attachments/assets/ef010046-6381-4d7a-a5af-8db2fda11045">


Creates `images` and `labels` directories inside `val_path`.

With `exist_ok=True`, no error is raised if the directories already exist.

Fetches the list of image files from `train_path/images`.

Uses `train_test_split` to divide the data into Validation data at a specified ratio (`split_ratio`).

**Image file copying**: Copies the selected Validation image files to `val_path/images`.

**Label file copying**: Copies the corresponding `.txt` label files to `val_path/labels`.

Only copies label files if they exist (`if os.path.exists`).


- **Training Parameters:**
- **`train.py`**
    
    The training script for YOLOv5. It is used to train the model.
- **`-img 512`**
    
    Specifies the input image size.
    
    The training data is resized to 512x512 pixels before being fed into the model.
    
    Smaller sizes increase training speed but may reduce performance, while larger sizes require more computational resources.
- **`-batch 16`**
    
    Sets the batch size.
    
    It determines the number of images input into the model at one time.
    
    Larger batch sizes can speed up training but require more memory.
- **`-epochs 300`**
    
    Specifies the number of training iterations (epochs).
    
    The model will train on the entire dataset 300 times.
    
    A higher number of epochs increases training time but can improve model performance.
- **`-data /content/drive/MyDrive/yolov5/data.yaml`**
    
    Path to the dataset configuration file.
    
    The `data.yaml` file contains:
    
    - Dataset paths (train/val images and labels)
    - Number of classes
    - Class names
- **`-weights yolov5n.pt`**
    
    Specifies the pre-trained YOLOv5 model weights.
    
    `yolov5n.pt` refers to the Nano version of YOLOv5, which is lightweight and fast but may have relatively lower performance.
    
    Other options include: `yolov5s.pt`, `yolov5m.pt`, `yolov5l.pt`, `yolov5x.pt`.
- **`-cache`**
    
    Caches the dataset into memory to speed up training.
    
    When enabled, it reduces I/O time (file reading/writing) during training.

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
