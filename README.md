# 🌱 Bean Leaf Classification using CNN

## 📌 Project Overview

This project focuses on developing a **Convolutional Neural Network (CNN)** to classify bean leaf images into three different categories based on their condition.

The model classifies bean leaves into:

1. **Angular Leaf Spot**
2. **Bean Rust**
3. **Healthy**

The objective is to build an image classification model that can automatically distinguish between healthy bean leaves and leaves affected by different diseases.

---

## 🗂️ Dataset

The dataset is already divided into **training, validation, and testing sets**.

### Dataset Structure

```text
Data/
├── train/
│   ├── angular_leaf_spot/
│   ├── bean_rust/
│   └── healthy/
│
├── validation/
│   ├── angular_leaf_spot/
│   ├── bean_rust/
│   └── healthy/
│
└── test/
    ├── angular_leaf_spot/
    ├── bean_rust/
    └── healthy/
```

| Class | Description |
|---|---|
| Angular Leaf Spot | Bean leaf affected by angular leaf spot disease |
| Bean Rust | Bean leaf affected by bean rust disease |
| Healthy | Healthy bean leaf |

---

## 🧠 Model Approach

A **Convolutional Neural Network (CNN)** was developed for this three-class image classification problem.

The overall workflow consists of:

1. Loading the image dataset
2. Image preprocessing
3. Image resizing
4. Pixel-value normalization
5. Building the CNN architecture
6. Training the model
7. Monitoring training and validation performance
8. Applying EarlyStopping
9. Restoring the best model weights
10. Evaluating the model on unseen test data
11. Generating predictions
12. Evaluating the predictions using a confusion matrix and classification report

CNNs are particularly suitable for image classification because they can automatically learn important visual features such as edges, textures, shapes, and patterns from images.

---

## 🎯 Model Training

The model was trained for a maximum of **20 epochs**.

**EarlyStopping** was used by monitoring the validation loss to prevent unnecessary training and reduce the possibility of overfitting.

During training, both training and validation performance improved overall.

The **best validation performance was achieved at Epoch 11**, where:

- **Training Accuracy:** 89.46%
- **Validation Accuracy:** 93.23%
- **Validation Loss:** 0.2211

After Epoch 11, the validation loss increased:

- Epoch 11 → **0.2211**
- Epoch 12 → **0.3071**

The validation loss remained higher in the following epochs, indicating that the model had reached its best generalization point and further training was no longer improving validation performance.

Because `restore_best_weights=True` was used, the model retained the weights from the epoch with the **lowest validation loss**, which was Epoch 11.

### Training Insight

The training results indicate that the model achieved strong validation performance while maintaining a relatively small difference between training and validation accuracy. This suggests **reduced overfitting and good generalization**.

---

## 📊 Final Test Results

After training, the model was evaluated on the unseen **test dataset containing 128 images**.

### Test Performance

- **Test Loss:** 0.2327
- **Test Accuracy:** 92.19%

The model achieved an overall test accuracy of approximately **92%**, demonstrating strong performance on unseen bean leaf images.

---

## Confusion Matrix

```
[[41  2  0]
 [ 6 36  1]
 [ 0  1 41]]
```

 The rows represent the actual classes and the columns represent the predicted classes.

| Actual Class | Predicted Angular Leaf Spot | Predicted Bean Rust | Predicted Healthy |
|---|---:|---:|---:|
| Angular Leaf Spot | 41 | 2 | 0 |
| Bean Rust | 6 | 36 | 1 |
| Healthy | 0 | 1 | 41 |

 ### Confusion Matrix Insight

- **Angular Leaf Spot:** 41 out of 43 images were correctly classified, achieving approximately **95% recall**.
- **Bean Rust:** 36 out of 43 images were correctly classified, achieving approximately **84% recall**.
- **Healthy:** 41 out of 42 images were correctly classified, achieving approximately **98% recall**.
- The largest confusion occurred between **Angular Leaf Spot and Bean Rust**, indicating that the model found it relatively difficult to distinguish between these two diseased leaf conditions.
- The model performed particularly well in identifying **Healthy** leaves, with only **1 misclassification out of 42 images**.
- Overall, the confusion matrix shows that the model was able to distinguish the three bean leaf categories effectively, with most predictions falling along the diagonal.

| Class | Precision | Recall | F1-Score | Support |
|---|---:|---:|---:|---:|
| Angular Leaf Spot | 0.87 | 0.95 | 0.91 | 43 |
| Bean Rust | 0.92 | 0.84 | 0.88 | 43 |
| Healthy | 0.98 | 0.98 | 0.98 | 42 |
| **Accuracy** | | | **0.92** | **128** |
| **Macro Average** | **0.92** | **0.92** | **0.92** | **128** |
| **Weighted Average** | **0.92** | **0.92** | **0.92** | **128** |

---

### Classification Report Insight

- **Healthy** achieved the best overall performance with an **F1-score of 0.98**, showing that the model was highly effective at identifying healthy bean leaves.
- **Angular Leaf Spot** achieved a **recall of 0.95**, meaning that the model correctly detected most of the actual Angular Leaf Spot images.
- **Bean Rust** achieved a **precision of 0.92**, meaning most images predicted as Bean Rust were actually Bean Rust.
- However, Bean Rust had a comparatively lower **recall of 0.84**, indicating that some actual Bean Rust images were misclassified as other classes.
- The **macro average F1-score of 0.92** indicates that the model maintained strong and relatively balanced performance across all three classes.
- The **weighted average F1-score of 0.92** further confirms the model's strong overall classification performance on the test dataset.

---

## 📈 Overall Results & Insights

The CNN model achieved a **92.19% test accuracy** on 128 unseen images.

The model achieved its best validation performance at **Epoch 11**, with:

- **89.46% Training Accuracy**
- **93.23% Validation Accuracy**
- **0.2211 Validation Loss**

The use of **EarlyStopping** prevented unnecessary training after validation performance stopped improving, while `restore_best_weights=True` ensured that the best-performing model weights were retained.

The relatively small difference between training and validation performance suggests that the model was able to generalize well without significant overfitting.

The confusion matrix and classification report show that the model performed particularly well on **Healthy** leaves, while the main challenge was distinguishing between the two diseased categories: **Angular Leaf Spot** and **Bean Rust**.

Overall, the model demonstrates strong performance for three-class bean leaf classification.

---

## 🛠️ Technologies Used

- **Python**
- **TensorFlow**
- **Keras**
- **NumPy**
- **Pandas**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **Jupyter Notebook**

---

## 📁 Project Structure

```text
BeanLeafClassifier-cnn/
│
├── BeanLeafClassifier.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## 👨‍💻 Author

**Ankush Thakur**

**Aspiring Data Scientist & AI Engineer**

- GitHub: [thakurankush1213-dot](https://github.com/thakurankush1213-dot)
- LinkedIn: [ankush-thakur](https://www.linkedin.com/in/ankush-thakur-3315a315b/)
