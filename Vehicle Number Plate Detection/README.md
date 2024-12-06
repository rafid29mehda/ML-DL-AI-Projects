## Paper Details

---

## Key Contributions
- **Problem Addressed**: Protecting sensitive vehicle number plate data using a robust detection and encryption system, essential for privacy and security in smart cities.
- **Solution**: Combined YOLOv8 for real-time number plate detection and a chaotic-based logistic map encryption scheme for secure data encryption.
- **Innovation**: Integration of detection and encryption in a sequential pipeline for efficient and secure processing, unlike previous studies that focused solely on one aspect.

---

## Research Methodology
1. **Dataset**:
   - Sourced from Roboflow.
   - Total: 8,823 images with labeled number plates.
   - Preprocessed and partitioned: 70% training, 10% validation, 20% testing.
   - Techniques included resizing, rotation, cropping, and zooming.

2. **Detection**:
   - Utilized YOLOv8 for its speed and accuracy in real-time object detection.
   - Training involved 50 epochs with an SGD optimizer.

3. **Encryption**:
   - Chaotic-based logistic encryption method with parameters \(r = 3.9\) and a seed value of 0.1.
   - Key steps: key generation, bounding box coordinate processing, chaotic iteration, and encryption using XOR operations.

4. **Evaluation**:
   - Metrics before preprocessing: Accuracy: 90%, Precision: 94%, Recall: 95%.
   - Metrics after preprocessing: Accuracy: 98%, Precision: 98%, Recall: 99%.
   - K-Fold cross-validation ensured robust evaluation (Test accuracy: 98.06%).

---

## Results
- Significant improvement after preprocessing.
- Model effectively detects and encrypts multiple number plates even in noisy images.
- Outperformed other YOLO versions (YOLOv2-v5) in accuracy and efficiency.

---

## Applications
- **Privacy**: Prevents unauthorized access to vehicle data, reducing privacy risks.
- **Security**: Protects against identity theft and fraudulent activities like vehicle cloning.
- **Real-Time Use**: Ideal for traffic surveillance, parking management, and law enforcement.

---

## Limitations & Future Work
- **Challenges**: Initial model struggled with noisy data and multiple detections before preprocessing.
- **Future Goals**: Enhance encryption methods and adapt system to diverse environments in smart cities.

---

## Common Questions
1. **Why YOLOv8?**
   - Chosen for its real-time detection capabilities and improved accuracy compared to earlier versions.
2. **What is the chaotic-based encryption scheme?**
   - A method leveraging chaotic behavior for secure and unpredictable encryption of sensitive data.
3. **How does this research improve upon existing systems?**
   - Combines detection and encryption, offering a streamlined, secure, and efficient solution.
4. **What is the significance of preprocessing?**
   - Enhanced the quality of data, resulting in improved detection and encryption accuracy.
5. **Applications of this system?**
   - Addresses privacy concerns in intelligent transportation systems, aids law enforcement, and secures vehicle-related data.

---
