
**Kidney CT Image Classification using PyTorch**

Project Overview: This project focuses on classifying kidney CT scan images into four medical conditions:

Normal

Cyst

Stone

Tumor

The goal is to build a robust and clinically meaningful image classification model using transfer learning while handling class imbalance and ensuring proper evaluation.


**Dataset Description**

Data Type: Kidney CT scan images

Classes: Normal, Cyst, Stone, Tumor

Structure: Folder-based class organization

Challenge: Class imbalance (Stone class has fewer samples)


**Approach & Methodology**

1. Data Preprocessing

Images resized to 224×224 for compatibility with pretrained models

Normalization applied using ImageNet mean and standard deviation

Data augmentation (rotation, affine transforms) applied only to training data to improve generalization

2️. Train / Validation / Test Split

Train: 70%

Validation: 15%

Test: 15%

Validation and test sets were not augmented to ensure unbiased evaluation.

3️. Model Architecture

Backbone: EfficientNet (pretrained on ImageNet)

Head: Custom classification layer for 4 kidney conditions

Why EfficientNet?

Strong performance with fewer parameters

Lower risk of overfitting on medical datasets

Computationally efficient

4️. Two-Phase Training Strategy
Phase 1 – Train Classifier Head

Backbone frozen

Only classifier head trained

Stabilizes training and preserves pretrained features

Phase 2 – Fine-Tuning

Last backbone layers unfrozen

Lower learning rate used

Allows adaptation to medical-specific patterns

5️. Handling Class Imbalance

Used class-weighted CrossEntropyLoss

Preserves real data distribution

Improves minority-class (Stone) recall without oversampling

**Evaluation Metrics**

Given the medical nature and class imbalance, evaluation focused on:

Per-class Recall (especially Tumor)

Macro F1-score

Precision

Accuracy (used as a secondary metric)

Confusion Matrix

Accuracy alone was not relied upon, as it can be misleading in imbalanced medical datasets.

**Results Summary**

Overall Accuracy: ~97%

Tumor Recall: ~96%

Macro F1-score: ~96%

Errors observed were clinically plausible, with most confusion occurring between visually similar classes.


**Tech Stack:** Python, PyTorch, Torchvision, EfficientNet, NumPy, Pandas, Matplotlib
