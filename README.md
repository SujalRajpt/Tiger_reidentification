# 🐯 Tiger Re-identification using CNNs

This project focuses on **Amur tiger re-identification** using convolutional neural networks (CNNs). It builds a complete deep learning pipeline that prepares the dataset, balances class distributions, preprocesses images, trains a CNN model with skip connections, and evaluates its performance.

---

## 🧠 Problem Statement

The goal is to recognize individual Amur tigers based on their visual features using deep learning, particularly CNNs. This helps in automating wildlife monitoring tasks such as counting and tracking.

---

## 📁 Dataset

**Source**: [Amur Tiger Re-Identification dataset](https://www.kaggle.com/datasets/quadeer15sh/amur-tiger-reidentification)

Dataset structure:
```
Amur Tigers/
├── train/
├── test/
├── reid_list_train.csv
└── reid_list_test.csv
```

---

## 🧪 Workflow Summary

### 1. Data Loading & Exploration
- Loads image paths and labels from CSV.
- Displays distribution of images per class.
- Identifies underrepresented classes.

### 2. Data Balancing
- Uses `ImageDataGenerator` to augment images and balance classes to 100 samples each.
- Augmentations include: brightness, zoom, rotation, and shift.

### 3. Preprocessing
- Images resized to 100x100 using OpenCV.
- Normalized pixel values to [0, 1].

### 4. Model Architecture

CNN model includes:
- **Skip connections** for better gradient flow.
- **Batch normalization**, **dropout**, and **ReLU** activations.
- **Softmax** final layer for multi-class classification.

```
Input -> Conv2D x2 -> MaxPool -> BN
      -> Conv2D x2 + Skip -> MaxPool -> Dropout
      -> Conv2D x2 + Skip -> MaxPool -> BN -> Flatten -> Dense -> Softmax
```

### 5. Training Setup
- Optimizer: `Adam`
- Loss: `categorical_crossentropy`
- Data Augmentation: Real-time using `ImageDataGenerator`
- Learning Rate Scheduler: `ReduceLROnPlateau`

---

## 🎯 Results

Final evaluation on the test set (`n=189 samples`):

```text
              precision    recall  f1-score   support

         106       1.00      1.00      1.00         2
         ... (many classes omitted for brevity) ...
    accuracy                           0.97       189
   macro avg       0.98      0.98      0.97       189
weighted avg       0.97      0.97      0.97       189
```

✅ **Accuracy**: 97%  
✅ **Macro Average F1-score**: 0.97

---

## 🖼 Visual Outputs

- Visualized sample image after preprocessing.
- Live display of training progress with validation accuracy/loss.

---

## ⚙️ Setup Instructions
This was trained on free version of colab



---


## 👤 Author

Developed by **Sujal Rajput** as part of a deep learning project focused on wildlife conservation and re-identification tasks using computer vision.

---

## 🧾 License

This project uses open datasets and open-source tools. Free for educational and research purposes.

