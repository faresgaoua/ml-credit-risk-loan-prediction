# Personal Loan Approval Prediction: A Comparative ML Study

## Project Overview

This project evaluates and compares 10 different machine learning models (ranging from linear baselines to advanced ensemble methods and neural networks) to predict personal loan approval outcomes. In banking and corporate sales environments, matching predictive speed with robust risk control is crucial to avoid costly misclassification errors.

The primary challenge of this financial dataset (5,000 observations) was a severe 90/10 class imbalance (90% of applications were denied), making standard overall accuracy a misleading metric. Evaluation metrics thus heavily prioritize Recall, F1-Score, and ROC-AUC.

---

## Data & Feature Engineering (Value Add)

To improve baseline performance, significant data enrichment and preprocessing were conducted on Excel and Python:

* **Geographic Contextualization:** Converted nominal zip codes into actual city names.
* **Economic Normalization:** Sourced external median household income per city and engineered a custom "Income / Median Income in City" ratio feature.
* **Impact:** This feature engineering process contributed more predictive value than all original variables combined, capturing 58% of the total predictive weight in the final tree models.

---

## Methodology & Models Tested

The study benchmarks 10 classifiers across 4 main methodologies:
1. **Linear Baselines:** OLS Linear Probability Model, Logistic Regression.
2. **Regularized Models:** Ridge, Lasso, Elastic Net (handling multicollinearity).
3. **Non-Linear Single Classifiers:** Support Vector Machines (RBF Kernel), KNN, CART.
4. **Ensemble & Deep Learning:** Random Forest, Gradient Boosting, Convolutional Neural Networks (CNN).

---

## Key Results

While linear models completely failed to identify the minority class (yielding low recall under 35%), non-linear methods achieved clear structural breakthroughs:

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Gradient Boosting (Selected)** | **98.6%** | **92.7%** | **92.7%** | **92.7%** | **0.994** |
| Random Forest | 98.2% | 94.3% | 86.5% | 90.2% | 0.993 |
| CART (Depth=7) | 97.7% | 86.1% | 90.6% | 0.883 | 0.978 |
| SVM (RBF Kernel) | 97.6% | 90.9% | 83.3% | 87.0% | 0.989 |
| Logistic Regression | 94.7% | 83.1% | 56.2% | 67.1% | 0.950 |

### Key Takeaway
**Gradient Boosting** delivered the most robust performance. By sequentially training successive trees to correct previous minority class errors, it maximized **Recall (92.7%)**, drastically reducing missed business opportunities without sacrificing overall data integrity.

---

## Project Nature & Team Role

This project was developed as a comprehensive final study for the **FINA 455** curriculum at **Concordia University**. 

* **My Role (Lead Technical Developer):** While collaborating closely with finance-focused team members on business logic, I acted as the sole developer responsible for building the data preprocessing pipelines, scripting the 10 core ML algorithms in Python, and generating performance visualization graphs.


---

## How to Run

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/faresgaoua/ml-credit-risk-loan-prediction.git](https://github.com/faresgaoua/ml-credit-risk-loan-prediction.git)
2. Install dependencies:
   pip install -r requirements.txt

3. Run the Jupyter Notebooks inside the /notebooks folder to reproduce the metrics.
