# Credit Default Prediction & Explainable AI

Machine learning project for predicting **credit card default risk**, combining supervised classification, model evaluation and Explainable Artificial Intelligence (XAI) using **SHAP**.

The project focuses not only on predictive performance, but also on understanding the factors that drive credit-risk predictions and critically evaluating model behavior on an imbalanced financial dataset.

---

## 🎯 Project Overview

The objective is to develop an end-to-end machine learning pipeline capable of identifying customers with a higher probability of credit card default.

The complete workflow includes:

- Exploratory Data Analysis (EDA)
- Data cleaning and preprocessing
- Analysis of class imbalance
- Logistic Regression
- Random Forest
- Gradient Boosting
- Model comparison using ROC-AUC and F1-score
- Global model explainability with SHAP
- Local prediction explainability with SHAP
- Critical analysis of model limitations

Special attention is given to the **minority default class**, since overall accuracy alone can provide a misleading assessment of model performance.

---

## 📊 Dataset

The project uses the **Default of Credit Card Clients** dataset from the UCI Machine Learning Repository.

The dataset contains information from **30,000 credit card customers**, including:

- Demographic information
- Credit limits
- Historical payment status
- Monthly bill statements
- Previous payment amounts
- Default status

The target variable indicates whether a customer defaulted on their payment.

One of the main challenges is the significant **class imbalance**, with substantially fewer defaulting customers than non-defaulting customers.

---

## 🔎 Exploratory Data Analysis

The exploratory analysis examines the demographic and financial characteristics of the customers and their relationship with default risk.

The analysis includes:

- Credit limit distribution
- Customer age distribution
- Target class distribution
- Relationship between credit limit and default
- Detection and correction of inconsistent categorical values

The analysis shows that customers who default tend to have lower credit limits, while the non-default group exhibits greater dispersion and higher maximum credit limits.

---

## 🤖 Machine Learning Models

Three supervised classification algorithms are compared:

### Logistic Regression

Used as a linear baseline to establish a reference performance.

### Random Forest

Introduces an ensemble of decision trees capable of capturing non-linear relationships and interactions between financial variables.

### Gradient Boosting

Sequentially combines weak learners to improve classification performance and capture complex patterns in customer behavior.

---

## 📈 Model Evaluation

Because the dataset is imbalanced, model selection focuses particularly on **ROC-AUC and F1-score for the default class**.

| Model | ROC-AUC | F1-score — Default |
|---|---:|---:|
| Logistic Regression | 0.7079 | 0.36 |
| Random Forest | 0.7572 | 0.46 |
| **Gradient Boosting** | **0.7790** | **0.47** |

**Gradient Boosting** achieves the best overall balance between discriminative capability and minority-class performance and is therefore selected as the final model.

The selected model achieves an overall accuracy of approximately **82%**, although its performance on the minority class remains considerably more limited.

---

## 🔍 Explainable AI with SHAP

Predictive performance alone is not sufficient in financial risk assessment.

Understanding **why a model predicts that a customer presents a higher or lower default risk** is particularly relevant when automated predictions may influence financial decisions.

SHAP (**SHapley Additive exPlanations**) is used to analyze the Gradient Boosting model from both global and local perspectives.

### Global Explainability

The SHAP Summary Plot identifies the variables with the greatest overall influence on model predictions.

The most relevant features include:

- `PAY_0`
- `LIMIT_BAL`
- `BILL_AMT1`
- `PAY_2`

Recent payment behavior is particularly influential. Payment delays tend to increase the predicted probability of default, while higher credit limits generally contribute toward lower estimated risk.

### Local Explainability

A SHAP Waterfall Plot is used to explain an individual customer prediction.

The visualization decomposes the prediction into individual feature contributions, showing which variables push the estimated risk upward or downward relative to the model's baseline prediction.

This provides a transparent explanation of how the final prediction is constructed for a specific customer.

---

## ⚠️ Limitations

Despite achieving approximately **82% accuracy** and a ROC-AUC of **0.7790**, the model still has important limitations.

Performance on the minority default class remains relatively limited. This means that a significant proportion of customers who eventually default may not be correctly identified.

This is particularly relevant in financial risk assessment, where **false negatives may represent high-risk customers incorrectly classified as low risk**.

Potential improvements include:

- SMOTE or other resampling techniques
- Undersampling
- Class-weighted learning
- Decision-threshold optimization
- Hyperparameter optimization
- XGBoost or LightGBM

These approaches could improve minority-class detection and provide a better balance between precision and recall.

---

## 🛠️ Technologies

- **Python**
- **Pandas**
- **NumPy**
- **Scikit-learn**
- **SHAP**
- **Matplotlib**
- **Seaborn**
- **Jupyter Notebook / Google Colab**

Main techniques:

`EDA` · `Classification` · `Logistic Regression` · `Random Forest` · `Gradient Boosting` · `ROC-AUC` · `F1-score` · `SHAP` · `Explainable AI`

---

## 📁 Project Structure

```text
credit-default-xai/
│
├── README.md
│
├── notebooks/
│   └── credit_default_xai.ipynb
│
└── report/
    └── credit_default_analysis.pdf
```

The **notebook** contains the complete data analysis, model training, evaluation and SHAP explainability workflow.

The **report** contains the original technical analysis developed as part of the Master's Degree in Applied Artificial Intelligence.

---

## 💡 Key Takeaways

- Credit default prediction is an **imbalanced classification problem**, making accuracy insufficient as the sole evaluation metric.
- Tree-based ensemble methods outperform the linear Logistic Regression baseline.
- **Gradient Boosting achieves the best performance**, with a ROC-AUC of **0.7790** and an F1-score of **0.47** for defaulting customers.
- Recent payment behavior is one of the strongest drivers of predicted default risk.
- SHAP provides both **global and individual explanations**, allowing model predictions to be interpreted rather than treated as black-box outputs.
- Model explainability is particularly relevant in financial applications where automated decisions may require justification.
- Strong overall accuracy does not guarantee adequate detection of the minority class, highlighting the importance of critical model evaluation.

---

## 🎓 Context

This project was developed as part of the **Model Calibration, Metrics and Explainability** course within the **Master's Degree in Applied Artificial Intelligence**.

The project demonstrates how predictive performance and model interpretability can be combined when developing machine learning systems for financial risk assessment.
