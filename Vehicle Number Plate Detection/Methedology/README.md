# Dataset and Data Preprocessing Steps

## Dataset Details
1. **Source**: 
   - The dataset was primarily obtained from **Roboflow**, an open-access platform for labeled datasets.
   - Additional datasets were curated and combined from multiple sources to address inconsistencies and irrelevant samples in the primary dataset.

2. **Images**:
   - **Total Images**: 8,823 labeled car images.
   - **Types**:
     - **Clear plates**: Well-defined and easy to detect.
     - **Moderate plates**: Slightly blurred or partially occluded.
     - **Noisy plates**: Significant distortion or poor lighting.

3. **Labeling**:
   - Bounding box annotations were provided for number plates to guide the YOLOv8 model during training.

4. **Partitioning**:
   - The dataset was split into:
     - **70% for training** (6,176 images).
     - **10% for validation** (882 images).
     - **20% for testing** (1,765 images).
   - This split ensured the model was trained and evaluated on diverse samples.

---

## Data Preprocessing
Preprocessing was critical to improve the model’s performance and ensure consistency across images. The following techniques were applied:

1. **Resizing**:
   - All images were resized to a fixed dimension of **640x640 pixels**.
   - This standardization:
     - Enhanced computational efficiency.
     - Maintained uniformity during training and evaluation.

2. **Rotation**:
   - **4% of images** were randomly rotated by up to **25 degrees**.
   - This augmentation improved the model’s ability to recognize number plates in varied orientations.

3. **Cropping**:
   - **7% of images** underwent cropping to focus on specific regions of interest.
   - Cropping:
     - Removed irrelevant portions of the image.
     - Highlighted number plates to improve detection accuracy.

4. **Zooming**:
   - Applied to **2% of images**, zooming in on number plates or areas of interest.
   - Enhanced the visibility of fine details, aiding in precise detection.

5. **Why Preprocessing Was Important**:
   - The raw dataset contained noisy and low-quality images.
   - Preprocessing significantly reduced false positives and negatives during number plate detection.
   - Improved the clarity and relevance of training data.

---

# Methodology

## Step-by-Step Workflow

1. **Model Selection**: 
   - **YOLOv8 (You Only Look Once version 8)**:
     - Chosen for its real-time object detection capabilities.
     - Advanced architecture improves speed and accuracy compared to earlier versions (YOLOv2–YOLOv5).

2. **Training Setup**:
   - Framework: **Ultralytics YOLOv8.0.3**.
   - **Hyperparameters**:
     - Batch size: **16**.
     - Image size: **640x640 pixels**.
     - Learning rate: **0.01**.
     - Optimizer: **Stochastic Gradient Descent (SGD)** with weight decay.
   - **Epochs**: Trained for **50 epochs**.
   - Data loader workers: **6**.

3. **Detection Phase**:
   - Input images were passed through YOLOv8, which identified the number plates as bounding boxes.
   - The detection threshold was set at an **Intersection over Union (IoU) of 0.7**, ensuring high accuracy by considering overlaps between predicted and actual bounding boxes.

4. **Evaluation of Detection**:
   - Metrics used:
     - Accuracy.
     - Precision.
     - Recall.
     - F1 Score.
   - Performance improved drastically after preprocessing (Accuracy improved from **90% to 98%**).

5. **Encryption Phase**:
   - **Chaotic-Based Logistic Encryption**:
     - Secured detected number plates by converting them into encrypted formats using chaotic dynamics.
   - **Steps**:
     1. **Key Generation**:
        - Generated a secret key based on parameters like initial seed value (**0.1**) and logistic map parameter \(r = 3.9\).
     2. **Bounding Box Coordinates Processing**:
        - Identified Regions of Interest (ROIs) within bounding boxes.
        - Converted RGB pixel values to grayscale for encryption.
     3. **Chaotic Iteration**:
        - Applied logistic map equation:
          \[
          x_{n+1} = r \cdot x_n \cdot (1 - x_n)
          \]
        - Generated a chaotic sequence mapped to grayscale intensity values (0–255).
     4. **Data Encryption**:
        - Pixel values XORed with chaotic values to introduce randomness and complexity, enhancing security.

6. **Model Testing**:
   - Conducted on the **test dataset** and additional unseen images.
   - Performance metrics included detection rates, encryption success, and visual results.

---

## System Flow

1. **Input**:
   - Raw images containing vehicles with visible number plates.
   
2. **YOLOv8 Detection**:
   - Number plates detected with bounding box coordinates.

3. **Chaotic-Based Encryption**:
   - Identified regions encrypted using chaotic dynamics, masking sensitive data.

4. **Output**:
   - Two forms:
     - Images with detected number plates.
     - Images with encrypted number plates.

5. **Visualization**:
   - Examples of results included:
     - Accurate detection of multiple plates.
     - Encrypted outputs showcasing the robust encryption process.

---
