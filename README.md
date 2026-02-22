# Semiconductor Yield Intelligence  
### AAI-540 – Machine Learning Systems Final Project  

---

## 👥 Authors

- Rishabh Pathak  
- Arunkumar Rajaganapathy  

---

# 📌 Project Overview

Semiconductor wafer fabrication is a highly sensitive manufacturing process where spatial defect patterns significantly impact yield and production cost.

Manual inspection of wafer maps is:

- Time-consuming  
- Subject to inconsistency  
- Difficult to scale  

This project builds a **Convolutional Neural Network (CNN)-based classification system** that automatically detects wafer defect patterns from 2D wafer maps.

The system demonstrates a complete ML lifecycle:

- Data Engineering  
- Feature Engineering  
- Model Training  
- Model Evaluation  
- Batch Inference  
- Model Artifact Versioning  
- Cloud Storage Integration (Amazon S3)  

---

# 🎯 Problem Statement

Design a supervised multi-class classification system capable of identifying wafer defect patterns from spatial wafer maps.

Key objective:

> Improve defect detection efficiency while maintaining strong recall performance for defect classes.

---

# 🏗 System Architecture

Raw Dataset (S3)  
↓  
Data Cleaning & Subset Sampling  
↓  
Stratified Train/Validation/Test Split  
↓  
CNN Model Training  
↓  
Model Artifact Storage (S3)  
↓  
Evaluation & Monitoring  
↓  
Batch Inference Demonstration  

---

# 📂 Project Structure
MLops-Project-AAI-540/
│
├── data/
│ ├── LSWMD.pkl
│ ├── X_train.npy
│ ├── y_train.npy
│ ├── X_val.npy
│ ├── y_val.npy
│ ├── X_test.npy
│ ├── y_test.npy
│ └── model.pt
│
├── notebooks/
│ ├── 01_Data_Preparation.ipynb
│ ├── 02_EDA.ipynb
│ ├── 03_Model_Training.ipynb
│ ├── 04_Model_Evaluation.ipynb
│ └── 05_Batch_Inference.ipynb
│
└── README.md



---

# 📊 Dataset

Dataset: WM-811K Wafer Map Dataset  

Due to compute and AWS credit constraints:

- A stratified subset (~2000 samples) is used  
- Images resized to 32x32  
- Dataset stored and versioned in Amazon S3  

---

# ⚙️ Modeling Approach

Primary Model: Lightweight CNN  

Architecture:

- 1 Convolution layer  
- MaxPooling  
- Fully Connected Layer  
- Softmax Output  

Training Configuration:

- Optimizer: Adam  
- Loss: CrossEntropyLoss  
- Epochs: 5 (cost-efficient training)  
- Batch Size: 32  

---

# 📈 Evaluation Metrics

- Accuracy  
- Precision  
- Recall (Primary Metric)  
- F1 Score  
- Confusion Matrix  

Recall is emphasized due to manufacturing yield implications.

---

# ☁️ Cloud Integration

Data and model artifacts are stored in Amazon S3:
s3://<sagemaker-us-east-1-702452513784>/wafer-project/
