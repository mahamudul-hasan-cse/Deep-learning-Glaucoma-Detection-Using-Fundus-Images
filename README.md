# Deep-learning-Glaucoma-Detection-Using-Fundus-Images
Glaucoma detection using segmentation and classification


# 🧠 Explainable Glaucoma Detection Using Fundus Images

This project presents an **end-to-end, explainable deep learning pipeline** for automated **glaucoma detection** using retinal fundus images.  
The system combines **medical image segmentation**, **clinical feature extraction (CDR)**, and **deep learning classification**.

---

## 🎯 Objective

The primary objective of this project is to detect glaucoma by:
1. Segmenting the **optic disc** and **optic cup**
2. Computing clinically significant **Cup-to-Disc Ratio (CDR)**
3. Classifying eyes as **Glaucoma** or **Non-Glaucoma**

This approach closely follows **real ophthalmology practice** and improves model explainability.

---

## 🗂️ Datasets Used

### 1️⃣ REFUGE2 Dataset (Segmentation)
- Purpose: Optic Disc & Cup Segmentation
- Used for: Structural analysis and CDR computation
- Link:  
  👉 https://www.kaggle.com/datasets/victorlemosml/refuge2

**Contents:**
- Fundus images
- Pixel-level masks for optic disc and optic cup

---

### 2️⃣ ACRIMA Dataset (Classification)
- Purpose: Glaucoma / Non-Glaucoma classification
- Used for: Image-level disease prediction
- Link:  
  👉 https://www.kaggle.com/datasets/arnavjain1/glaucoma-detection

**Contents:**
- Fundus images
- Reliable glaucoma labels

⚠️ Datasets are **not included** in this repository due to size and license restrictions.

---

## 🧠 Methodology Overview

### 🔹 Step 1: Image Preprocessing
- Resize all images to **512 × 512**
- Normalize pixel values to **[0, 1]**
- Apply contrast enhancement and vessel suppression

---

### 🔹 Step 2: Optic Disc & Cup Segmentation
- Model: **U-Net**
- Encoder: Pretrained CNN backbone
- Loss: Dice Loss + Cross-Entropy
- Metrics:
  - Dice Score
  - IoU
  - Pixel Accuracy

**Why segmentation?**  
Glaucoma is a **structural disease**, and changes in the optic cup and disc are key clinical indicators.

---

### 🔹 Step 3: Cup-to-Disc Ratio (CDR) Computation
From segmentation masks, the following were computed:
- Vertical CDR
- Horizontal CDR
- Area-based CDR

A **vCDR ≥ 0.6** is used as a glaucoma risk indicator (based on clinical literature).

---

### 🔹 Step 4: Glaucoma Classification
- Model: **EfficientNet-B3**
- Pretrained on ImageNet
- Fine-tuned on ACRIMA dataset
- Input: Fundus images
- Output: Glaucoma / Non-Glaucoma

---

## 📊 Evaluation Metrics

### 🔹 Segmentation Metrics
- Dice Score
- Intersection over Union (IoU)
- Pixel Accuracy

### 🔹 Classification Metrics
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix

---

## ✅ Results Summary

### 🔹 Segmentation (REFUGE2)
- High Dice score for optic disc and cup
- Accurate boundary detection
- Reliable CDR computation

### 🔹 Classification (ACRIMA)
- Accuracy: **~96%**
- F1-score: **~0.96**
- ROC-AUC: **~0.99**

These results indicate strong generalization while avoiding unrealistic overfitting.

---

## 🧪 Implementation

All implementation is provided in a **single Jupyter Notebook**:

