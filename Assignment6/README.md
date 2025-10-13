# DA5401 A6: Imputation via Regression for Missing Data

## Name : Pawar Devesh Pramod
## Roll No. : ME22B176
## Date of Submission: 17/10/2025

---

### Overview
This project tackles the common challenge of missing data in a real-world credit risk assessment scenario using the UCI Credit Card Default Clients Dataset. The primary objective is to implement and evaluate four different strategies for handling missing data.

The effectiveness of each strategy—simple imputation (median), linear regression imputation, non-linear regression imputation (KNN), and listwise deletion—is measured by training a Logistic Regression classifier on the resulting datasets and comparing their predictive performance. The goal is to determine how the choice of a missing data technique impacts a model's ability to accurately predict credit card default.



---

### File Structure
    - Dataset file: `UCI_Credit_Cart.csv` .
    - The file ME22B176_Assignment_6.ipynb contains all the code and imports the dataset, libraries and perform the tasks.
    

---

### Tasks Performed
#### Part A: Data Preprocessing and Imputation
- Loaded the UCI Credit Card Default dataset and artificially introduced Missing At Random (MAR) values into 2-3 numerical feature columns to simulate a realistic data quality problem.

- Strategy 1 (Median Imputation): Created "Dataset A" by filling missing values with the median of their respective columns, a robust baseline method.

- Strategy 2 (Linear Regression Imputation): Created "Dataset B" by training a LinearRegression model on other features to predict and fill in the missing values in a chosen column.

- Strategy 3 (Non-Linear Regression Imputation): Created "Dataset C" using a KNeighborsRegressor model to impute the same column, capturing more complex relationships between features.

#### Part B: Model Training and Performance Assessment

- Strategy 4 (Listwise Deletion): Created "Dataset D" by removing all rows containing any missing values.

- Split each of the four imputed datasets (A, B, C, D) into training and testing sets.

- Applied StandardScaler to the features of all four datasets to normalize them for the classification model.

- Trained a LogisticRegression classifier on each of the four training sets and evaluated its performance on the corresponding test set using a full Classification Report (Accuracy, Precision, Recall, F1-score).

#### Part C: Comparative Analysis

- Generated a summary table to directly compare the performance metrics, especially the F1-score, across the four models.

- Analyzed the trade-offs between listwise deletion and imputation, discussing why discarding data can be problematic even if it yields decent metrics.

- Compared the efficacy of the linear vs. non-linear regression imputation methods based on the final classification results.

- Concluded with a final recommendation on the best strategy for this scenario, justified by both the performance metrics and the conceptual strengths of the method.

---

### Key Insights

- **Listwise Deletion Risk:** Although listwise deletion performed marginally best in this specific experiment, it's generally a risky approach. It significantly reduces sample size and can introduce bias if the missing data is not completely random, potentially creating a model that doesn't generalize well.

- **Imputation Stability:** All three imputation methods (median, linear regression, and non-linear regression) resulted in identical performance for the downstream classification model. This suggests the classifier was not sensitive to the subtle differences in the imputed values for the chosen features in this dataset.

- **Simplicity Wins:** The more complex and computationally expensive regression-based imputation techniques offered no performance advantage over simple median imputation. This highlights that a more complex solution is not always better and that a simple, robust baseline can be highly effective.

- **Recommended Strategy:** For this scenario, Median Imputation is the recommended strategy. It is computationally efficient, easy to implement, and preserves the entire dataset, avoiding the risks of listwise deletion. Since it achieved the same classification performance as the more advanced methods, it offers the best balance of simplicity, robustness, and effectiveness.