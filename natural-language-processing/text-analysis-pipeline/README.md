# NLP Text Analysis Pipeline

Natural Language Processing project combining **extractive summarization**, **sentiment analysis** and **Spanish-to-English machine translation** within a single text-processing workflow.

The project demonstrates how classical NLP techniques and pretrained Transformer models can be combined depending on the requirements of each task.

---

## 🎯 Project Overview

The objective is to process a Spanish text discussing the social impact of technology and apply three complementary NLP techniques:

- Extractive text summarization
- Sentiment analysis
- Machine translation from Spanish to English

The notebook emphasizes not only model inference, but also practical considerations such as long-text segmentation, model-domain mismatch and interpretability of NLP outputs.

---

## 📝 Extractive Summarization

A lightweight frequency-based extractive summarization method is used instead of a generative summarization model.

The workflow:

1. Splits the document into sentences.
2. Tokenizes the text and removes common Spanish stopwords.
3. Computes normalized word frequencies.
4. Scores sentences according to the relevance of their words.
5. Selects the highest-scoring sentences while preserving their original order.

This approach is deterministic and interpretable, although it cannot reformulate information because it only selects sentences already present in the source document.

---

## 🙂 Sentiment Analysis

Sentiment is estimated with the multilingual Hugging Face model:

`nlptown/bert-base-multilingual-uncased-sentiment`

The original model predicts ratings between one and five stars. These outputs are mapped to three sentiment categories:

- 1–2 stars → Negative
- 3 stars → Neutral
- 4–5 stars → Positive

To avoid evaluating only the beginning of the document, predictions are produced sentence by sentence and aggregated using the mean star rating.

The notebook also discusses an important limitation: the source text contains both positive and critical perspectives, so reducing the whole document to a single sentiment label inevitably loses nuance.

---

## 🌍 Machine Translation

Spanish-to-English translation is performed using the pretrained MarianMT model:

`Helsinki-NLP/opus-mt-es-en`

The text is translated paragraph by paragraph to reduce the risk of truncation in long inputs.

Beam search is used during generation to improve the quality of the translated sequence.

---

## 💡 Key Takeaways

- Classical NLP techniques can remain useful when transparency and reproducibility are priorities.
- Pretrained Transformer models provide sophisticated NLP capabilities without training models from scratch.
- Long documents often require segmentation before Transformer inference.
- Generic sentiment models may oversimplify argumentative or mixed-perspective texts.
- Model outputs should be interpreted in relation to the domain and training objective of the underlying model.
- A single NLP pipeline can combine deterministic preprocessing with modern pretrained language models.

---

## 🛠️ Technologies

- **Python**
- **Hugging Face Transformers**
- **BERT**
- **MarianMT**
- **PyTorch**
- **NumPy**
- **Regular Expressions**
- **Jupyter Notebook / Google Colab**

Main techniques:

`NLP` · `Extractive Summarization` · `Sentiment Analysis` · `Machine Translation` · `Transformers` · `BERT` · `MarianMT`

---

## 📁 Project Structure

```text
text-analysis-pipeline/
│
├── README.md
└── notebooks/
    └── nlp_text_analysis.ipynb
```

The notebook contains the complete workflow, methodological notes, implementation details and qualitative interpretation of each NLP task.

---

## 🎓 Context

This project was developed as part of the **Unstructured Data Applications and Use Cases** course within the **Master's Degree in Applied Artificial Intelligence**.

It has been reorganized and documented as part of this technical portfolio while preserving the original objective and core NLP tasks.