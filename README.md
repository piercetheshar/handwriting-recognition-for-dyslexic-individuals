# 🖋️ Handwriting Recognition for Dyslexic Individuals  
Deep Learning Project — CSE 676B  

---

## 📌 Overview

This project develops a deep-learning OCR system specifically designed to recognize **handwriting from dyslexic individuals**.  
Traditional OCR systems struggle because dyslexic handwriting often includes atypical shapes, spacing, inconsistencies, and reversed or distorted letters.

Our goal is to build an **inclusive, robust, and high-accuracy handwriting recognition pipeline** using CNN-based architectures, augmentation, and optimized training loops.

---

## 📊 Dataset

**Source:** Roboflow Dyslexic Handwriting Dataset  
**Classes:** 26 letters (A–Z)  
**Train:** 17,376 images  
**Validation:** 1,658 images  
**Test:** 828 images  

Characteristics:

- Grayscale images (28×28)
- High variation in shapes & writing styles
- Designed specifically for dyslexic children’s handwriting
- Balanced splits ensure strong generalization

---

## 🧠 Methodology

### **Preprocessing**
- Convert to grayscale  
- Resize to 28×28  
- Apply augmentations:
  - Random rotations  
  - Affine transforms  
  - Horizontal flips  
- Normalize pixel values  
- Dataset organized into train/val/test loaders

---

### **Model Architecture: Alphabet CNN**

A custom CNN architecture designed for letter-level dyslexic handwriting detection:

- **Conv Block 1:**  
  1 → 64 channels, BatchNorm, ReLU  
- **Conv Block 2:**  
  64 → 128 channels  
- **Conv Block 3:**  
  128 → 256 channels  
- MaxPooling after each block  
- Fully Connected Layer: 512 neurons  
- Dropout 0.5  
- Output Layer: 26 classes (A–Z)  

---

### **Training Setup**

- **Epochs:** 20  
- **Loss Function:** Cross-Entropy Loss (Label Smoothing = 0.1)  
- **Optimizer:** AdamW (lr = 0.001, weight decay = 1e-4)  
- **Scheduler:** OneCycleLR (max_lr = 0.01)  
- **Early stopping** after 5 epochs with no improvement  

---

## 📈 Results

### Highlights:
- Validation accuracy reached **~91%**  
- Test accuracy reached **~90.7%**  
- Loss steadily decreased with minimal overfitting  
- Harder classes corresponded to less frequent letters  
- Strong generalization to unseen handwriting styles  

The model learns rapidly:
- ~80% validation accuracy by epoch 5  
- ~91% validation accuracy by final epochs  

---

## 🗂️ Repository Structure

