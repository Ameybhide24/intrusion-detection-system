# CCS Intrusion Detection System

This project implements an Intrusion Detection System (IDS) using a **Stacked Sparse Autoencoder (SSAE)** followed by a **Support Vector Machine (SVM)** for classification. It is based on the NSL-KDD dataset, which is a refined version of the KDD'99 dataset, used widely for network intrusion detection research.

## Project Overview

The goal of this project is to accurately distinguish between **normal** and **attack** network traffic using deep feature extraction with SSAEs and classification using SVMs.

## Dataset

- NSL-KDD (KDDTrain+, KDDTest+)
- Preprocessing includes:
  - Removal of redundant columns
  - One-hot encoding for categorical features
  - MinMax normalization
  - Label binarization: `normal` → 0, `others` → 1

## Model Architecture

### Stacked Sparse Autoencoder (SSAE)
- **Input Layer** → 100 → 85 → 55 → 5-Dimensional Bottleneck → 55 → 85 → 100 → Output Layer
- All layers use sigmoid activation function
- Trained using Mean Squared Error (MSE) loss and Adam optimizer

### Support Vector Machine (SVM)
- Uses features from the 5-dimensional bottleneck layer
- Classifies into `normal` vs `attack` traffic

## Evaluation

- Evaluated on KDDTest+ set
- Metrics:
  - Accuracy
  - Precision, Recall, F1-score
  - Confusion Matrix


## Results

- The SSAE was able to compress high-dimensional 121 feature vectors into compact 5-D representations.
- The SVM classifier achieved good generalization on unseen test data.
- We achieved classification accuracy of 88.24%
- Confusion matrix and classification report included in the notebook.


## References

- Lavi, A., & Polak, S. (2018). Stacked sparse autoencoder for network intrusion detection. *Communications in Computer and Information Science*.
- NSL-KDD Dataset: [https://www.unb.ca/cic/datasets/nsl.html](https://www.unb.ca/cic/datasets/nsl.html)
