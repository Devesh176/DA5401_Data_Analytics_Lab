# DA5401 A7: Multi-Class Model Selection using ROC and Precision-Recall Curves


## Name : Pawar Devesh Pramod
## Roll No. : ME22B176
## Date of Submission: 31/10/2025

---

### Overview
This project tackles the challenge of robust model selection in a multi-class classification environment using the UCI Landsat Satellite dataset. The primary objective is to implement and critically compare a diverse set of six classifiers, ranging from high-performance models to a baseline dummy model.

The effectiveness of each classifier is measured not by simple accuracy, but by a deep analysis of **Receiver Operating Characteristic (ROC)** curves and **Precision-Recall Curves (PRC)**. The goal is to determine the best- and worst-performing models by evaluating their performance across all decision thresholds, rather than relying on a single, default metric.

---
### File Structure
    - Dataset files: `sat.trn` & `sat.tst`.
    - The file ME22B176_Assignment_7.ipynb contains all the code and imports the dataset, libraries and perform the tasks.
    

---

### Tasks Performed
#### Part A: Data Preparation and Baseline
- **Loaded and Prepared Data:** Loaded the Landsat training and testing datasets.
- **Standardized Features:** Applied `StandardScaler` to the feature sets (X) of both training and testing data to normalize them for the models.
- **Trained All Models:** Trained all six specified model classes (Dummy Classifier, Naive Bayes, Decision Tree, KNN, Logistic Regression, and SVC with `probability=True`) on the training data.
- **Baseline Evaluation:** Calculated the **Overall Accuracy** and **Weighted F1-Score** for all six models on the test set to establish an initial performance baseline.

#### Part B: ROC Analysis for Model Selection
- **Multi-Class ROC Calculation:** Implemented the **One-vs-Rest (OvR)** approach to generate ROC curves for the multi-class problem.
- **Plotted ROC Curves:** Generated a single, combined plot displaying the **Macro-Averaged OvR ROC curves** for all six models, allowing for a direct comparison of their ability to separate classes.
- **ROC Interpretation:** Identified the model with the highest **Macro-Averaged AUC** and analyzed the performance of the `DummyClassifier` (AUC = 0.5) to understand what "random chance" performance looks like.

#### Part C: Precision-Recall Curve (PRC) Analysis
- **PRC Calculation:** Explained the theoretical importance of PRCs over ROCs, especially in scenarios with class imbalance.
- **Plotted PRC Curves:** Generated a single, combined plot displaying the **Macro-Averaged OvR PRC curves** for all models.
- **PRC Interpretation:** Identified the model with the highest **Macro-Averaged Average Precision (AP)** and analyzed the sharp performance drop-off of the worst-performing models, explaining *why* their precision collapses as recall increases.

#### Part D: Final Recommendation
- **Comparative Analysis:** Created a final summary table to directly compare the model rankings across all three metrics: **Weighted F1-Score**, **Macro-ROC-AUC**, and **Macro-PRC-AP**.
- **Synthesized Findings:** Analyzed the discrepancies in rankings, noting why a model with a high F1-score (like KNN) might not be the best model when analyzing its full performance spectrum.
- **Final Recommendation:** Concluded with a final recommendation for the best model from the required list, justifying the choice based on its superior, balanced performance across the curve-based metrics.

---

### Key Insights

- **F1-Score Can Be Misleading:** The initial baseline metrics were deceptive. **KNN** had the highest **Weighted F1-Score (0.897)**, suggesting it was the best model. However, the curve-based analyses revealed this was not the case.

- **Curve Metrics Reveal Robustness:** **SVC (Prob)**, which was #2 in F1-score, was the clear winner on the more comprehensive metrics. It achieved the highest **Macro-ROC-AUC (0.982)** and the highest **Macro-PRC-AP (0.925)**, proving it is the most robust and well-calibrated model across all possible decision thresholds.

- **Ensemble Models Dominate:** The "Brownie Points" task, which added `Random Forest` and `XGBoost`, demonstrated that ensemble methods are a clear step above the individual classifiers. **XGBoost** (Macro-AUC: 0.991, Macro-AP: 0.962) and **Random Forest** (Macro-AUC: 0.990, Macro-AP: 0.954) both outperformed the SVC.

- **Recommended Strategy (from required list):** For the required models, the **SVC (Prob)** is the recommended strategy. While KNN performed well at the default 0.5 threshold, the SVC's superior AUC and AP scores show it provides a more reliable balance of precision and recall, making it the most robust and trustworthy choice for this classification task.