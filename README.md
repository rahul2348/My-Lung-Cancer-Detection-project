

## **Lung Cancer Detection Using Deep Learning**

### **Project Objective**
Develop a robust Convolutional Neural Network (CNN) to automatically detect and classify lung cancer types from CT scan images, enabling faster and more accurate diagnosis.

### **Dataset Overview**
- **Training Set:** 612 images  
- **Validation Set:** 72 images  

**Class Distribution:**
- **Adenocarcinoma:** 194 images
- **Large Cell Carcinoma:** 115 images
- **Normal (Non-cancerous):** 148 images
- **Squamous Cell Carcinoma:** 155 images

### **Preprocessing Workflow**
- **Label Encoding:**  
  Assigns a unique integer to each class (0: Adenocarcinoma, 1: Large Cell Carcinoma, 2: Normal, 3: Squamous Cell Carcinoma) for model compatibility.

- **Image Standardization:**  
  Resizes all images to 256×256 pixels and converts them to grayscale for consistency.

- **Normalization:**  
  Scales pixel values to the [1] range for stable and efficient model training.

- **Data Augmentation:**  
  Applies random horizontal flips, rotations, zooms, and contrast adjustments to enrich the dataset and reduce overfitting.

- **Handling Class Imbalance:**  
  Utilizes class weights to ensure balanced learning across underrepresented classes.

### **Model Architecture**
- **Framework:** TensorFlow/Keras Sequential model
- **Convolutional Blocks:**  
  - Three Conv2D layers with increasing filters (32, 64, 128) and 3×3 kernels  
  - Each followed by MaxPooling for spatial reduction and feature abstraction

- **Dense Layers:**  
  - Flatten layer to convert feature maps to a vector  
  - Dense layer with 128 neurons (ReLU activation)  
  - Dropout (rate = 0.3) to prevent overfitting

- **Output Layer:**  
  - Dense layer with 4 neurons (softmax activation) for multi-class classification

- **Compilation:**  
  - Optimizer: Adam (learning rate = 0.0003)  
  - Loss: Sparse categorical crossentropy

### **Training Strategy**
- **Cross-Validation:**  
  5-fold KFold cross-validation for robust hyperparameter tuning and model validation.

- **Final Training:**  
  After tuning, the best model is retrained on the full training set for 60 epochs with augmentation.

- **Performance Monitoring:**  
  - Continuous tracking of training/validation loss and accuracy  
  - Visualization of loss curves for progress assessment

### **Challenges & Solutions**
- **Data Imbalance:**  
  *Challenge:* Unequal class representation could bias the model.  
  *Solution:* Applied class weights for balanced learning.

- **Overfitting:**  
  *Challenge:* Limited data and complex model risked overfitting.  
  *Solution:* Used data augmentation, dropout, and early stopping.

- **Model Convergence:**  
  *Challenge:* Ensuring stable convergence with imbalanced and augmented data.  
  *Solution:* Used learning rate reduction on plateau and normalization.

### **Evaluation Summary**
- **Overall Metrics:**  
  - Accuracy: **88.89%**  
  - Precision: **88.98%**  
  - Recall: **88.89%**  
  - F1 Score: **88.81%**

- **Class-wise Performance:**  
  - Adenocarcinoma: Precision 0.86, Recall 0.78, F1 0.82  
  - Large Cell Carcinoma: Precision 0.90, Recall 0.90, F1 0.90  
  - Normal: Precision/Recall/F1 1.00 (Perfect classification)  
  - Squamous Cell Carcinoma: Precision 0.82, Recall 0.93, F1 0.88  

**Insights:**  
The model demonstrates robust performance across all metrics, with reliable differentiation among cancer types. Some variance in class-wise results highlights opportunities for further tuning, especially for adenocarcinoma.

### **Future Directions**
- **Model Optimization:**  
  Further refine the architecture and hyperparameters for higher precision.

- **Data Expansion:**  
  Integrate larger and more diverse datasets for improved generalization.


