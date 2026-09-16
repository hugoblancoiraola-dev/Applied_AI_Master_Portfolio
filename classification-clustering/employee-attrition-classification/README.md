# Employee Attrition Prediction with kNN and SVM

People Analytics classification project focused on predicting **employee attrition** using the `attrition` dataset from the R package `modeldata`.

The project develops a complete supervised machine learning workflow with **R and tidymodels**, covering exploratory analysis, feature engineering, class imbalance handling, model tuning and business-oriented model comparison.

---

## 🎯 Project Overview

The objective is to predict whether an employee is likely to leave the organization (`Attrition = Yes`).

The workflow includes:

- Exploratory Data Analysis (EDA)
- Data-quality checks
- Stratified train/test splitting
- Feature engineering with `recipes`
- Dummy encoding and normalization
- Correlation filtering
- Class balancing with SMOTE
- k-Nearest Neighbors hyperparameter tuning
- Polynomial Support Vector Machine classification
- Evaluation using accuracy, sensitivity and specificity
- Business-oriented comparison of false positives and false negatives

The analysis emphasizes that overall accuracy is not enough in an imbalanced classification problem when the operational goal is to detect employees at risk of leaving.

---

## 📊 Dataset

The project uses the `attrition` dataset from the `modeldata` package, originally provided by IBM Watson Analytics Lab.

- **Observations:** 1,470 employees
- **Predictors:** 30 employee-related variables
- **Target:** `Attrition` (`Yes` / `No`)
- **Problem:** supervised binary classification

The target is strongly imbalanced:

- Approximately **83.9%** `No`
- Approximately **16.1%** `Yes`

This imbalance motivates the use of **SMOTE** during model training.

---

## ⚙️ Feature Engineering

A reusable `tidymodels` recipe is built using the training data only.

The preprocessing pipeline includes:

- Near-zero-variance predictor removal
- Median imputation for numeric variables
- Grouping of rare categorical levels
- Dummy encoding of nominal features
- Numeric standardization
- Removal of highly correlated predictors
- SMOTE oversampling of the minority class

Keeping the preprocessing inside the workflow ensures that each resampling iteration learns transformations from the corresponding training fold only, reducing the risk of information leakage.

---

## 🤖 k-Nearest Neighbors

The number of neighbors is tuned using **10-fold stratified cross-validation**.

ROC AUC is used as the primary tuning metric because the target is imbalanced and discrimination between employees who stay and leave is more informative than accuracy alone.

The best value found in the explored grid is:

- **k = 50**
- **Cross-validated ROC AUC ≈ 0.77**

On the test set, the kNN model achieves approximately **64.7% accuracy** while identifying **51 real attrition cases**.

Its main trade-off is a comparatively high number of false positives, meaning that it prioritizes sensitivity toward potentially at-risk employees.

---

## 🧮 Polynomial SVM

A non-linear Support Vector Machine with a polynomial kernel is also evaluated using the same preprocessing pipeline.

Model configuration:

- `cost = 1`
- `degree = 2`
- `scale_factor = 1`

The SVM achieves approximately **81.7% test accuracy**.

Its confusion matrix contains approximately:

- **True positives:** 27
- **False positives:** 36
- **False negatives:** 45
- **True negatives:** 334

The model is substantially more conservative than kNN: it produces fewer false alarms and higher specificity, but misses many real attrition cases.

---

## ⚖️ Model Comparison

The two models exhibit different operational behavior:

- **kNN** provides higher sensitivity for employees who actually leave.
- **SVM** provides higher overall accuracy and specificity.

This makes model selection dependent on the business objective.

In an employee-retention context, false negatives may be particularly costly because they represent employees who leave without being identified as at risk. The project therefore highlights why evaluation metrics must be aligned with the operational objective rather than optimized in isolation.

---

## 💡 Key Takeaways

- Employee attrition is a strongly imbalanced classification problem.
- Stratified splitting preserves class prevalence across training and test data.
- `tidymodels` recipes provide a clean way to integrate feature engineering and resampling.
- SMOTE helps expose models to more minority-class examples during training.
- kNN and SVM can produce very different error profiles even on the same dataset.
- Accuracy alone is insufficient for business-oriented model selection.
- Sensitivity and specificity provide a clearer picture of the trade-off between missed departures and false alarms.
- The optimal model depends on the cost associated with each type of classification error.

---

## 🛠️ Technologies

- **R**
- **tidyverse**
- **tidymodels**
- **modeldata**
- **skimr**
- **themis**
- **kknn**
- **kernlab**
- **Quarto**

Main techniques:

`EDA` · `Feature Engineering` · `SMOTE` · `kNN` · `SVM` · `Cross-Validation` · `ROC-AUC` · `Sensitivity` · `Specificity` · `People Analytics`

---

## 📁 Project Structure

```text
employee-attrition-classification/
│
├── README.md
└── analysis/
    └── employee_attrition_classification.qmd
```

The Quarto document contains the complete analysis, preprocessing workflow, model training, evaluation and interpretation.

---

## 🎓 Context

This project was developed as part of the **Classification and Clustering Techniques** course within the **Master's Degree in Applied Artificial Intelligence**.

It has been reorganized and documented as part of this technical portfolio while preserving the original methodology and results.