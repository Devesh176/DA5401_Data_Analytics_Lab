# DA5401 A5: Visualizing Data Veracity Challenges in Multi-Label Classification

## Name : Pawar Devesh Pramod
## Roll No. : ME22B176
## Date of Submission: 05/10/2025

---

### Overview
This project explores data veracity challenges in the multi-label Yeast dataset using non-linear dimensionality reduction techniques.

The focus is on applying t-Distributed Stochastic Neighbor Embedding (t-SNE) and Isomap to visually inspect the gene expression data for quality issues such as noisy labels, outliers, and hard-to-learn samples.

The goal is to understand the underlying structure of the data and identify the challenges a machine learning classifier would face.

---

### File Structure
    - The yeast folder has the necessary data files.
    - The file ME22B176_Assignment_5.ipynb contains all the code and imports dataset from '/yeast' directory and does the necessary visualizations.
    

---

### Tasks Performed
#### Part A: Preprocessing and Visualization Setup
-   Loaded the Yeast dataset, separating the 103 gene expression features from the 14 multi-label functional categories.
-   Simplified the 14 labels into four distinct categories for effective color-coding in visualizations: the two most frequent single-label classes, the most frequent multi-label combination, and an "Other" category.
-   Applied `StandardScaler` to the feature matrix, a crucial step for distance-based algorithms like t-SNE and Isomap.

#### Part B: t-SNE for Local Structure Visualization
-   Applied t-SNE to reduce the high-dimensional feature space to two dimensions.
-   Experimented with the `perplexity` hyperparameter (e.g., 5, 30, 50, 100) to find the most informative visualization of the local data structure.
-   Analyzed the final t-SNE plot (using perplexity=30) to visually identify regions corresponding to outliers, noisy/ambiguous labels, and hard-to-learn samples.

#### Part C: Isomap for Global Manifold Learning
-   Applied Isomap to project the feature data into two dimensions, focusing on preserving global geodesic distances.
-   Created a 2D scatter plot using the same color scheme as the t-SNE visualization.
-   Compared the Isomap and t-SNE plots, analyzing their different strengths in revealing global versus local data structures.
-   Discussed the concept of the data manifold based on the Isomap visualization and related its complexity to the difficulty of classification.

---

### Key Insights
- **Optimal Perplexity**: A t-SNE perplexity between 30 and 50 provides the most balanced visualization, effectively revealing local clusters without the fragmentation seen at lower values or the "crowding" effect at higher values.

- **t-SNE vs. Isomap**: t-SNE is superior for identifying tight, local clusters and spotting anomalies within them. Isomap excels at revealing the global, continuous structure of the data, showing it as a single, connected manifold.

- **Data Veracity Issues**: The visualizations successfully exposed significant data quality challenges. The t-SNE plot highlighted isolated outliers (potential experimental errors), noisy labels (points embedded in incorrect clusters), and large central regions where classes were thoroughly mixed, making them hard to learn.

- **Manifold Complexity**: The Isomap plot suggests that the gene expression data lies on a complex, curved manifold. The fact that different functional classes are interwoven on this manifold is a primary reason why building an accurate classifier for this dataset is fundamentally challenging.