# DA5401 A8: Ensemble Learning for Complex Regression Modeling on Bike Share Data

## Name : Pawar Devesh Pramod
## Roll No. : ME22B176
## Date of Submission: 10/11/2025

---

### Overview

This project tackles a complex, time-series-based regression problem using the **UCI Bike Sharing Demand Dataset**. The primary objective is to implement, evaluate, and critically compare three primary ensemble techniques: **Bagging, Boosting, and Stacking**. The effectiveness of each ensemble is measured by its ability to minimize the **Root Mean Squared Error (RMSE)** when forecasting hourly bike rentals. The goal is to demonstrate how these methods manage the **bias-variance trade-off** to produce a model far superior to any single, simple regressor.


---
### File Structure
    - Dataset files: `day.csv` & `hour.csv`.
    - The file ME22B176_Assignment_8.ipynb contains all the code and imports the dataset, libraries and perform the tasks.    

---

### Tasks Performed

#### Part A: Data Preprocessing and Baseline
- **Loaded and Preprocessed Data:** Loaded the `hour.csv` file and dropped irrelevant or leaky columns (`instant`, `dteday`, `casual`, `registered`).
- **Feature Engineering:** Applied **One-Hot Encoding** to all categorical features (`season`, `weathersit`, `mnth`, `hr`) to make them suitable for regression models.
- **Time-Series Split:** Split the data into training (80%) and testing (20%) sets sequentially (no shuffling) to respect the time-series nature of the data and prevent data leakage.
- **Baseline Models:** Trained and evaluated two baseline models: `LinearRegression` and `DecisionTreeRegressor (max_depth=6)`.
- **Baseline Evaluation:** Established the final baseline RMSE using the **Linear Regression** model (RMSE: 133.8276), which performed significantly better than the single Decision Tree.

#### Part B: Ensemble Techniques for Bias and Variance Reduction
- **Bagging (Variance Reduction):** Implemented a `BaggingRegressor` using the `DecisionTreeRegressor` (max_depth=6) as the base estimator, with 50 estimators. This marginally improved the single tree's performance but was still far worse than the baseline.
- **Boosting (Bias Reduction):** Implemented a `GradientBoostingRegressor`, which targets high-bias problems. The default model already outperformed the baseline.
- **Hyperparameter Tuning:** Conducted a `RandomizedSearchCV` on the `GradientBoostingRegressor` to find the optimal combination of parameters (`n_estimators`, `max_depth`, `learning_rate`, etc.), which **dramatically reduced the RMSE** to the lowest score in the project.

#### Part C: Stacking for Optimal Performance
- **Stacking Definition:** Explained the principle of stacking, where a meta-learner is trained on the predictions of diverse base learners.
- **Stacking Implementation:** Defined a `StackingRegressor` with three diverse **Level-0 (Base) Learners**:
    1.  `KNeighborsRegressor`
    2.  `BaggingRegressor` (from Part B)
    3.  The **Tuned Gradient Boosting Regressor** (from Part B)
- **Meta-Learner:** Used a `RidgeRegression` model as the **Level-1 (Meta) Learner** to find the optimal weights for combining the base learners' predictions.
- **Final Evaluation:** Calculated the RMSE for the complete stacking model on the test set.

#### Part D: Final Analysis
- **Comparative Table:** Created a final summary table to directly compare the RMSE of all five models: Baseline (Linear Regression), Decision Tree, Bagging, Gradient Boosting (Tuned), and Stacking.
- **Synthesized Findings:** Analyzed the final rankings, explaining *why* the high-bias baseline models failed and how the ensembles, particularly Gradient Boosting, were able to effectively model the complex, non-linear patterns in the data.
- **Final Recommendation:** Concluded with a final recommendation for the best-performing model, justifying the choice based on its superior RMSE and its demonstrated ability to solve the bias-variance trade-off.

---

### Key Insights

- **Baselines Are Insufficient for Complex Data:** The `LinearRegression` model (RMSE: 133.8276) performed poorly because it suffered from **high bias**, making it incapable of capturing the critical non-linear, bimodal hourly rental patterns. The `DecisionTreeRegressor` (RMSE: 158.7006) performed even worse, suffering from **high variance**.

- **Ensembles Dramatically Reduce Error:** Both Boosting and Stacking ensembles provided a massive performance increase over the baseline. This proves that for a complex problem like this, a single model is insufficient and combining models is the correct approach.

- **Boosting (and Tuning) is Best for Bias:** The **Tuned Gradient Boosting Regressor** was the clear winner, achieving the lowest RMSE of **82.378**. This technique, which sequentially builds trees to correct the errors of its predecessors, was perfectly suited to "learn" the complex patterns that the high-bias `LinearRegression` model missed.

- **Tuning is Not Optional, It's Critical:** The *default* Gradient Boosting model performed well, but the **hyperparameter tuning** step was what pushed its performance from "good" to "excellent." This was the single most impactful optimization in the project.

- **Stacking vs. Boosting:** In this specific case, the `StackingRegressor` (RMSE: 88.0382) performed exceptionally well but was narrowly beaten by the fine-tuned `GradientBoostingRegressor`. This suggests that the Gradient Boosting model was so strong on its own that the other models in the stack (KNN, Bagging) did not add enough new, predictive information to surpass it.

- **Recommended Strategy:** The **Tuned Gradient Boosting Regressor** is the final recommended model. It provides the best predictive accuracy by building a single, strong learner that effectively modeled the complex, non-linear, and time-dependent relationships in the bike rental data.