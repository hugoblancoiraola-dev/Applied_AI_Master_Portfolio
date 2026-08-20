# ECG Arrhythmia Detection with Machine Learning

Machine learning project for the detection and classification of cardiac arrhythmias from **electrocardiogram (ECG) signals**, combining statistical analysis, dimensionality reduction, supervised learning and Bayesian inference.

The project explores how machine learning techniques can be applied to biomedical signals to distinguish between **normal and abnormal heartbeats**, with particular attention to class imbalance, model evaluation and false positive control.

---

### 🔗 Project Resources

[📓 View Notebook](./notebooks/ecg_arrhythmia_detection.ipynb) · [📄 Technical Report](./report/ecg_arrhythmia_analysis.pdf)

## 🎯 Project Overview

The objective is to analyze individual ECG heartbeats and build machine learning models capable of identifying abnormal cardiac patterns.

The complete workflow includes:

* Exploratory Data Analysis (EDA)
* Statistical analysis of ECG signals
* Feature extraction
* Principal Component Analysis (PCA)
* Logistic Regression
* Decision Tree classification
* Multiclass and binary classification
* Model evaluation using Precision, Recall and F1-score
* Bayesian analysis of ECG signal patterns

The analysis emphasizes not only predictive performance, but also the **interpretation of results in an imbalanced biomedical classification problem**.

---

## 📊 Dataset

The project uses the **ECG Heartbeat Categorization Dataset**, based on the MIT-BIH Arrhythmia Database.

Each observation represents an individual heartbeat containing:

* **187 ECG signal measurements**
* **1 target class**
* Sampling frequency: **125 Hz**

The complete dataset contains **109,446 heartbeats**, divided into predefined training and test sets.

### Heartbeat Classes

| Class | Heartbeat Type       |
| ----- | -------------------- |
| 0     | Normal (N)           |
| 1     | Supraventricular (S) |
| 2     | Ventricular (V)      |
| 3     | Fusion (F)           |
| 4     | Noise / Unknown (Q)  |

One of the main challenges is the strong **class imbalance**, with normal heartbeats representing approximately **83% of the training data**.

---

## 🔎 Exploratory Data Analysis

The exploratory analysis focuses on understanding both the statistical properties and morphology of the ECG signals.

The analysis includes:

* Class distribution
* ECG amplitude distributions
* Descriptive statistics
* Statistical features aggregated by heartbeat
* Representative ECG signals
* Average heartbeat morphology by class

Several abnormal heartbeat classes show greater internal variability than normal heartbeats. However, considerable overlap exists between classes, suggesting that simple threshold-based rules are insufficient for reliable classification.

---

## 📉 Dimensionality Reduction with PCA

Each heartbeat contains 187 signal measurements, resulting in a relatively high-dimensional feature space.

**Principal Component Analysis (PCA)** is applied after feature standardization to identify dominant patterns and visualize the structure of the ECG data.

The first two principal components explain approximately:

| Component | Explained Variance |
| --------- | -----------------: |
| PC1       |             36.63% |
| PC2       |             15.63% |
| **Total** |         **52.26%** |

The two-dimensional projection reveals some underlying structure but also substantial overlap between heartbeat classes.

PCA is therefore useful for **exploration and dimensionality reduction**, but does not provide sufficient class separation on its own.

---

## 🤖 Machine Learning Models

Two supervised learning approaches are compared.

### Logistic Regression

Logistic Regression is used as a linear baseline.

In the multiclass classification problem, the model achieves approximately:

* **Accuracy:** 67.4%
* **Macro F1-score:** 0.48

The model shows difficulties separating pathological heartbeat classes, indicating that the underlying relationships are not adequately represented by linear decision boundaries.

### Decision Tree

A Decision Tree is used to capture non-linear relationships between ECG signal features.

Multiclass performance improves to approximately:

* **Accuracy:** 88.9%
* **Macro Recall:** 0.85
* **Macro F1-score:** 0.68

The results indicate that a non-linear model is better suited to the structure of the ECG data.

---

## ❤️ Abnormal Heartbeat Detection

The problem is additionally reformulated as a binary classification task:

**Normal heartbeat vs. Abnormal heartbeat**

This formulation represents a potential monitoring scenario where the main objective is detecting whether a heartbeat requires further attention.

### Binary Classification Results

| Model               |  Accuracy | Precision |    Recall |  F1-score |
| ------------------- | --------: | --------: | --------: | --------: |
| Logistic Regression |     85.1% |     54.7% |     79.3% |     64.7% |
| **Decision Tree**   | **94.3%** | **79.5%** | **90.0%** | **84.4%** |

The Decision Tree provides a substantially better balance between **detecting abnormal heartbeats and limiting false positives**.

---

## 🧮 Bayesian Analysis

Bayes' theorem is used to investigate how individual statistical properties of an ECG signal affect the probability of a ventricular heartbeat.

Three patterns are analyzed:

### Maximum Amplitude

Observing a high maximum amplitude barely modifies the probability of a ventricular heartbeat.

**Prior probability:** ~7.4%
**Posterior probability:** ~7.4%

Maximum amplitude alone therefore provides little discriminatory information.

### Heartbeat Energy

Heartbeat energy provides substantially more information.

**Prior probability of ventricular heartbeat:** ~7.4%
**Posterior probability after observing high energy:** **~22.9%**

A high-energy ECG pattern therefore increases the estimated probability of a ventricular heartbeat by more than three times.

### Maximum Signal Slope

The analyzed maximum-slope pattern reduces the posterior probability of a ventricular heartbeat to approximately **2.6%**, indicating that this particular criterion is not useful as a positive indicator of ventricular beats.

---

## 🛠️ Technologies

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **Matplotlib**
* **Seaborn**
* **Jupyter Notebook / Google Colab**

Main machine learning and statistical techniques:

`EDA` · `PCA` · `Logistic Regression` · `Decision Trees` · `Classification Metrics` · `Bayesian Inference`

---

## 📁 Project Structure

```text
ecg-arrhythmia-detection/
│
├── README.md
│
├── notebooks/
│   └── ecg_arrhythmia_detection.ipynb
│
└── report/
    └── ecg_arrhythmia_analysis.pdf
```

The **notebook** contains the complete analysis, preprocessing, visualizations, model training and evaluation.

The **report** contains the original technical analysis developed as part of the Master's Degree in Applied Artificial Intelligence.

---

## 💡 Key Takeaways

* ECG heartbeat classification is a strongly **imbalanced learning problem**, making metrics such as Recall and F1-score particularly important.
* PCA reveals substantial underlying structure in ECG signals, although the first two components are not sufficient to clearly separate heartbeat classes.
* The **Decision Tree significantly outperforms Logistic Regression**, suggesting important non-linear relationships within ECG signals.
* In binary abnormal-heartbeat detection, the Decision Tree achieves **90% recall and an F1-score of 84.4%** for abnormal heartbeats.
* Simple ECG-derived features differ considerably in predictive value: heartbeat energy provides substantially more information about ventricular beats than maximum amplitude.
* Model evaluation in biomedical applications requires considering the trade-off between **sensitivity and false positives**, rather than relying exclusively on overall accuracy.

---

## 🎓 Context

This project was developed as part of the **Mathematics and Statistics for Artificial Intelligence** course within the **Master's Degree in Applied Artificial Intelligence**.

Its objective was to combine statistical foundations with practical machine learning techniques in a real-world biomedical signal analysis problem.
