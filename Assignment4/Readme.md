# DA5401 Assignment 4 (GMM-Based Synthetic Sampling for Imbalanced Data)

## Name : Pawar Devesh Pramod
## Roll No. : ME22B176
## Date of Submission: 15/09/2025

---

### Overview
This assignment tackles the class imbalance problem in the Credit Card Fraud Detection dataset by applying probabilistic resampling techniques.

The focus is on evaluating the effectiveness of Gaussian Mixture Model (GMM)-based synthetic oversampling and a hybrid approach combining Cluster-Based Undersampling (CBU) with GMM.

The goal is to measure the impact of these approaches on the performance of a Logistic Regression classifier, and compare them against a Baseline model trained on the original imbalanced dataset.

---

### File Structure
The file ME22B176_Assignment_4.ipynb contains all the code and imports dataset via kagglehub and imports/installs all the necessary libraries.

---

### Tasks Performed
#### Part A: Data Exploration & Baseline Model

-   Loaded the creditcard.csv dataset via KaggleHub.

-   Inspected the class imbalance (fraud ≈ 0.2%).

-   Split data into training and test sets (keeping the test set imbalanced).

-   Trained a Baseline Logistic Regression model on the imbalanced data.

-   Evaluated using precision, recall, and F1-score for the minority class, highlighting why accuracy is misleading.

#### Part B: GMM-Based Oversampling

-   Fit a Gaussian Mixture Model (GMM) on minority-class training data.

-   Determined the optimal number of components (k) using AIC/BIC criteria.

-   Generated synthetic minority samples by sampling from the fitted GMM distribution.

-   Created a balanced training dataset by combining synthetic and real data.

-   Trained Logistic Regression on this GMM-balanced dataset and evaluated on the imbalanced test set.

#### Part C: Hybrid Rebalancing (CBU + GMM)

-   Applied ClusterCentroids (Clustering-Based Undersampling) on the majority class, reducing its size while preserving structural diversity.

-   Fit a GMM on the minority class and generated synthetic samples to match the reduced majority population.

-   Created a final balanced dataset combining CBU-reduced majority samples with GMM-synthesized minority samples.

-   Trained Logistic Regression on the hybrid dataset and evaluated on the same test set.

#### Part D: Model Comparison & Analysis

-   Compared the performance of:

    -   Baseline (no resampling)

    -   GMM-only Oversampling

    -   Hybrid (CBU + GMM)

-   Constructed box and spider (radar) plots comparing precision, recall, and F1-score for all three models.

-   Discussed trade-offs between recall and precision, and the implications for fraud detection.

---

### Key Insights

- Baseline Model: Achieved the best F1-score (≈0.698) with strong precision (72.5%), but missed nearly one-third of frauds (recall ≈67%).

- GMM-only Oversampling: Increased recall to ~91%, detecting almost all frauds, but precision dropped to ~5.6%, leading to many false positives.

- Hybrid (CBU + GMM): Maximized recall (~94%) but precision collapsed to less than 1%, making it impractical for deployment.

- GMM-based oversampling is theoretically superior to SMOTE as it models the underlying probability distribution of fraud cases and generates more realistic, diverse synthetic samples.

