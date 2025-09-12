# DA5401 Assignment 2 (Addressing Class Imbalance with Clustering and Resampling)

## Name : Pawar Devesh Pramod
## Roll No. : ME22B176
## Date of Submission: 12/09/2025


### Overview
his assignment addresses the challenge of class imbalance in the Credit Card Fraud Detection dataset using resampling techniques.
The objective is to improve the performance of a Logistic Regression classifier by comparing:

1. Baseline model (imbalanced data)

2. Naive Oversampling (SMOTE)

3. Clustering-Based Oversampling (CBO)

4. Clustering-Based Undersampling (CBU)

---

### Tasks Performed
#### Part A: Data Exploration & Baseline Model
- Loaded the creditcard.csv dataset using KaggleHub.

- Analyzed the class distribution (highly imbalanced: fraud ≈ 0.2%).

- Split data into train/test sets (keeping test set imbalanced).

- Trained a baseline Logistic Regression model.

- Evaluated using precision, recall, and F1-score (since accuracy is misleading on imbalanced data).

#### Part B: Resampling Approaches

- SMOTE (Naive Oversampling):

    - Generated synthetic samples for minority class.

    - Balanced dataset, improved recall, but reduced precision.

- Clustering-Based Oversampling (CBO):

    - Applied K-Means clustering on the minority class.

    - Oversampled within clusters to ensure diversity and representativeness.

    - Achieved very high recall, but precision dropped.

- Clustering-Based Undersampling (CBU):

    - Clustered the majority class and removed redundant samples.

    - Preserved structure of majority while reducing imbalance.

    - Improved recall but lost precision due to discarded majority data.

#### Part C: Model Comparison & Analysis

- Trained Logistic Regression on all four datasets (Baseline, SMOTE, CBO, CBU).

- Evaluated performance on the same imbalanced test set.

- Created a spider (radar) plot comparing precision, recall, and F1-score.

- Discussed why accuracy is misleading, and why recall is critical in fraud detection.

---

###  Key Insights
- Baseline Logistic Regression: Best F1-score due to balanced precision & recall, but missed ~1/3 of frauds.

- SMOTE & CBO: Achieved very high recall (~93%), ensuring almost all frauds are detected, but precision dropped sharply (many false alarms).

- CBU: Balanced dataset but sacrificed too much majority information, leading to poor precision.

- Clustering-Based Oversampling (CBO) is more robust than SMOTE, since it respects the internal structure of the minority class and ensures representation of different fraud subtypes

