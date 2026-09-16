# Deep Learning with Keras: LSTM & CNN

Deep learning project exploring two complementary neural network architectures with **TensorFlow and Keras**:

- **LSTM** for one-step-ahead time series forecasting
- **CNN** for multi-class image classification on CIFAR-10

The project demonstrates how neural network architectures can be adapted to fundamentally different data structures: sequential information for recurrent networks and spatial information for convolutional networks.

---

## 🎯 Project Overview

The objective of this project is to implement and evaluate two deep learning workflows covering different application domains.

The first experiment uses a **Long Short-Term Memory (LSTM)** network to learn temporal dependencies in a synthetic time series. The second experiment develops a **Convolutional Neural Network (CNN)** for classifying images from the CIFAR-10 dataset.

The complete workflow includes:

- Data generation and preprocessing
- Sequential data preparation with sliding windows
- LSTM architecture design and training
- Time series forecasting
- CIFAR-10 image preprocessing
- Data augmentation
- CNN architecture design
- Dropout and L2 regularization
- Early Stopping and Model Checkpointing
- Training and validation analysis
- Evaluation on held-out test data

---

## ⏱️ LSTM for Time Series Forecasting

The first experiment uses a synthetic time series composed of multiple sinusoidal signals and random noise.

A sliding-window approach transforms the original series into supervised learning samples. Each input contains the previous **30 observations**, while the following observation is used as the target.

### Architecture

The model uses a compact sequence-to-one architecture:

- Input sequence: 30 time steps
- LSTM layer: 64 units
- Dense output layer: 1 neuron

The network is optimized using **Adam** and **Mean Squared Error (MSE)**.

The experiment demonstrates the complete process of converting sequential data into a format suitable for recurrent neural networks and using an LSTM for one-step-ahead forecasting.

---

## 🖼️ CNN for CIFAR-10 Image Classification

The second experiment uses the **CIFAR-10** dataset, which contains 32 × 32 RGB images distributed across 10 classes:

`airplane` · `automobile` · `bird` · `cat` · `deer` · `dog` · `frog` · `horse` · `ship` · `truck`

Images are normalized to the `[0, 1]` range and labels are one-hot encoded before training.

### Data Augmentation

To improve generalization, the training pipeline applies:

- Random horizontal flipping
- Random translations
- Random rotations

### CNN Architecture

The network contains three convolutional blocks with increasing feature depth:

- 32 convolutional filters
- 64 convolutional filters
- 128 convolutional filters

Each block combines convolution, ReLU activation, Max Pooling and Dropout. The extracted features are then passed to a fully connected layer before the final 10-class Softmax output.

Additional regularization is provided through **L2 regularization**, **Dropout** and **Early Stopping**.

---

## 📈 Results

The LSTM successfully learns the temporal structure of the synthetic sequence and produces predictions that closely follow the real test signal.

For the CIFAR-10 experiment, the final CNN achieves approximately:

- **Test accuracy:** 67.8%
- **Test loss:** 1.00

The final architecture prioritizes generalization rather than maximizing training accuracy. Regularization and data augmentation help reduce overfitting and maintain relatively stable training and validation behavior.

---

## 💡 Key Takeaways

- LSTM networks are suitable for modeling sequential and temporal dependencies.
- CNNs are effective at extracting hierarchical spatial features from image data.
- Different neural network architectures should be selected according to the structure of the input data.
- Sliding windows transform time series into supervised learning sequences suitable for recurrent models.
- Data augmentation, Dropout and L2 regularization can reduce overfitting in image classification.
- Early Stopping and validation monitoring are important for selecting models that generalize beyond the training data.
- Evaluation on held-out test data is essential for estimating real model performance.

---

## 🛠️ Technologies

- **Python**
- **TensorFlow**
- **Keras**
- **NumPy**
- **Scikit-learn**
- **Matplotlib**
- **Jupyter Notebook / Google Colab**

Main techniques:

`Deep Learning` · `LSTM` · `CNN` · `Time Series Forecasting` · `Computer Vision` · `Data Augmentation` · `Dropout` · `L2 Regularization` · `Early Stopping`

---

## 📁 Project Structure

```text
keras-neural-networks/
│
├── README.md
└── notebooks/
    └── keras_lstm_cnn.ipynb
```

The notebook contains both complete experiments, including preprocessing, model construction, training, evaluation and result analysis.

---

## 🎓 Context

This project was developed as part of the **Regressions and Deep Learning** course within the **Master's Degree in Applied Artificial Intelligence**.

It has been reorganized and documented as part of this technical portfolio while preserving the original experiments and results.