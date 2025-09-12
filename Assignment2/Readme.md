# DA5401 Assignment 2 (PCA, Visualization, and Classification)

## Name : Pawar Devesh Pramod
## Roll No. : ME22B176
## Date of Submission: 05/09/2025


### Overview
This assignment explores **dimensionality reduction** using **Principal Component Analysis (PCA)** on the Mushroom Dataset.  
The goal is to evaluate how PCA affects the performance of a **Logistic Regression classifier** compared to using the original high-dimensional data.

---

### Tasks Performed
#### Part A: EDA & Preprocessing
- Loaded the **Mushroom dataset** (categorical features, target = edible/poisonous).
- Applied **one-hot encoding** to convert categorical variables into numerical features.
- Standardized features using **StandardScaler** to ensure equal contribution to PCA.

#### Part B: Principal Component Analysis (PCA)
- Applied PCA without specifying components initially.
- Created a **scree plot** and cumulative variance plot to determine optimal components.
- Selected the number of principal components that preserve ~95% variance.
- Visualized mushrooms in 2D using the first two principal components.

#### Part C: Logistic Regression Evaluation
- Trained and tested a Logistic Regression classifier on:
  1. **Original standardized features**  
  2. **PCA-reduced features**
- Compared performance using accuracy, precision, recall, and F1-score.
- Discussed trade-offs between dimensionality reduction and model performance.

---

###  Key Insights
- One-hot encoding was necessary since PCA requires numerical data.
- Standardization ensured no feature dominated due to frequency differences.
- PCA effectively reduced redundancy, with a small number of components explaining most of the variance.
- Logistic Regression on PCA-reduced data performed comparably to the original, while using fewer features.
- PCA improved **computational efficiency** and handled feature collinearity without major performance loss.


