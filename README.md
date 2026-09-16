# Applied Artificial Intelligence — Master's Portfolio

Portfolio of projects developed during my **Master's Degree in Applied Artificial Intelligence**.

This repository brings together practical projects covering different areas of Artificial Intelligence, from statistical analysis and classical Machine Learning to Deep Learning, Natural Language Processing, Computer Vision and Explainable AI.

The objective of this portfolio is to showcase the practical application of AI techniques to different problems, including the complete workflow from **data exploration and preprocessing to model training, evaluation and interpretation**.

---

## 🚀 Featured Projects

### 🫀 ECG Arrhythmia Detection with Machine Learning

Machine learning pipeline for detecting and classifying cardiac arrhythmias from ECG signals.

The project combines statistical analysis, dimensionality reduction and supervised learning on a biomedical dataset containing more than **100,000 ECG heartbeats**.

**Highlights:**

* Exploratory Data Analysis of ECG signals
* Statistical feature extraction
* Principal Component Analysis (PCA)
* Logistic Regression and Decision Tree classification
* Multiclass and binary classification
* Evaluation under strong class imbalance
* Bayesian analysis of ECG signal patterns
* **94.3% accuracy and 90.0% recall** in binary abnormal-heartbeat detection using a Decision Tree

**Technologies:** `Python` · `Pandas` · `NumPy` · `Scikit-learn` · `Matplotlib` · `Seaborn`

➡️ [Explore the project](./mathematics-statistics-for-ai/ecg-arrhythmia-detection/)

### 💳 Credit Default Prediction & Explainable AI

End-to-end machine learning pipeline for predicting **credit card default risk** using a dataset of 30,000 customers.

The project covers exploratory data analysis, imbalanced classification, model comparison and **Explainable AI with SHAP**, providing both global and individual explanations of model predictions.

Three classification algorithms were evaluated: Logistic Regression, Random Forest and Gradient Boosting. **Gradient Boosting achieved the best performance with a ROC-AUC of 0.7790 and an F1-score of 0.47 for the default class.**

SHAP analysis identified recent payment behavior and credit-related variables as the main drivers of predicted default risk.

**Technologies:** `Python` · `Pandas` · `NumPy` · `Scikit-learn` · `SHAP` · `Matplotlib` · `Seaborn`

➡️ [Explore the project](./model-evaluation-explainability/credit-default-xai/)

### 🧠 Deep Learning with Keras: LSTM & CNN

Two complementary deep learning experiments demonstrating how neural network architectures can be adapted to different data structures.

The first experiment uses an **LSTM network** for one-step-ahead forecasting on a synthetic time series. The second develops a **CNN for CIFAR-10 image classification**, incorporating data augmentation, Dropout, L2 regularization and Early Stopping.

The final CNN achieves approximately **67.8% test accuracy**, while the LSTM demonstrates the complete sequence-preparation and forecasting workflow for temporal data.

**Technologies:** `Python` · `TensorFlow` · `Keras` · `NumPy` · `Scikit-learn` · `Matplotlib`

➡️ [Explore the project](./deep-learning/keras-neural-networks/)

### 📝 NLP Text Analysis Pipeline

Natural Language Processing pipeline for Spanish text combining **extractive summarization**, **sentiment analysis** and **Spanish-to-English machine translation**.

The project combines a transparent frequency-based summarization method with pretrained Hugging Face Transformer models, including multilingual BERT for sentiment analysis and MarianMT for machine translation.

It also discusses practical limitations such as sentiment-model domain mismatch, loss of nuance in document-level polarity and long-text segmentation for Transformer inference.

**Technologies:** `Python` · `Hugging Face Transformers` · `BERT` · `MarianMT` · `PyTorch` · `NumPy`

➡️ [Explore the project](./natural-language-processing/text-analysis-pipeline/)

---

## 📚 Projects by Area

### 📊 Mathematics & Statistics for AI

Statistical foundations and mathematical techniques applied to Artificial Intelligence and Machine Learning problems.

| Project | Topics |
|---|---|
| [ECG Arrhythmia Detection](./mathematics-statistics-for-ai/ecg-arrhythmia-detection/) | EDA · PCA · Classification · Model Evaluation · Bayesian Inference |

### 🔍 Model Evaluation & Explainability

| Project | Main Topics |
|---|---|
| [Credit Default Prediction & Explainable AI](./model-evaluation-explainability/credit-default-xai/) | Classification · Imbalanced Data · ROC-AUC · F1-score · Gradient Boosting · SHAP · Explainable AI |

### 🧠 Deep Learning

| Project | Main Topics |
|---|---|
| [Deep Learning with Keras: LSTM & CNN](./deep-learning/keras-neural-networks/) | LSTM · Time Series Forecasting · CNN · CIFAR-10 · Data Augmentation · Regularization |

### 📝 Natural Language Processing

| Project | Main Topics |
|---|---|
| [NLP Text Analysis Pipeline](./natural-language-processing/text-analysis-pipeline/) | Extractive Summarization · Sentiment Analysis · Machine Translation · Transformers · BERT · MarianMT |

---

## 🧠 Areas Covered

Throughout the portfolio, the projects cover topics including:

* Machine Learning
* Statistical Analysis
* Classification & Clustering
* Dimensionality Reduction
* Deep Learning
* Neural Networks
* Natural Language Processing
* Computer Vision
* Time Series
* Model Evaluation
* Explainable AI (XAI)
* Data Governance & AI in Business

---

## 🛠️ Tech Stack

**Languages**

`Python` · `R`

**Data & Machine Learning**

`Pandas` · `NumPy` · `Scikit-learn`

**Deep Learning**

`TensorFlow` · `Keras` · `PyTorch`

**Natural Language Processing**

`Hugging Face Transformers` · `BERT` · `MarianMT`

**Visualization & Explainability**

`Matplotlib` · `Seaborn` · `SHAP`

**Development**

`Jupyter Notebook` · `Google Colab` · `Git` · `GitHub`

---

## 📂 Repository Structure

```text
Applied_AI_Master_Portfolio/
│
├── README.md
│
├── mathematics-statistics-for-ai/
│   └── ecg-arrhythmia-detection/
│       ├── README.md
│       ├── notebooks/
│       │   └── ecg_arrhythmia_detection.ipynb
│       └── report/
│           └── ecg_arrhythmia_analysis.pdf
│
├── model-evaluation-explainability/
│   └── credit-default-xai/
│       ├── README.md
│       ├── notebooks/
│       │   └── credit_default_xai.ipynb
│       └── report/
│           └── credit_default_analysis.pdf
│
├── deep-learning/
│   └── keras-neural-networks/
│       ├── README.md
│       └── notebooks/
│           └── keras_lstm_cnn.ipynb
│
└── natural-language-processing/
    └── text-analysis-pipeline/
        ├── README.md
        └── notebooks/
            └── nlp_text_analysis.ipynb
```

Each project contains its own documentation explaining the **problem, methodology, models, results and conclusions**, together with the corresponding implementation and, when available, the original technical report.

---

## 🎓 Academic Context

These projects were developed as part of the **Master's Degree in Applied Artificial Intelligence**.

The repository has been reorganized and documented as a technical portfolio, preserving the original analyses and results while improving their presentation and accessibility.

---

## 📌 Portfolio Status

This portfolio is being progressively expanded with selected projects from the Master's Degree.

**Projects currently available:**

- ✅ ECG Arrhythmia Detection with Machine Learning
- ✅ Credit Default Prediction & Explainable AI
- ✅ Deep Learning with Keras: LSTM & CNN
- ✅ NLP Text Analysis Pipeline

Additional projects covering clustering, advanced Computer Vision and other AI areas will be added progressively.
