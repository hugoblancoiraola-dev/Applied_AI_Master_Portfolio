# NLP Text Analysis Pipeline

Natural Language Processing project combining **extractive summarization**, **sentiment analysis** and **Spanish-to-English machine translation** within a single workflow.

The project demonstrates how lightweight rule-based text processing can be combined with pretrained Transformer models from Hugging Face for different NLP tasks.

---

## 🎯 Project Overview

The objective is to process a Spanish text discussing the social impact of technology and apply three complementary NLP techniques:

- Extractive text summarization
- Sentiment analysis
- Machine translation from Spanish to English

The notebook also documents methodological limitations so that the model outputs are interpreted in context rather than treated as ground truth.

---

## 📝 Extractive Summarization

A simple deterministic extractive strategy is used to create a concise summary from the original document.

The workflow:

1. Splits the text into sentences using regular expressions.
2. Selects the opening sentence to preserve context.
3. Includes a sentence introducing one of the main challenges discussed in the text.
4. Includes the final sentence to preserve the document's conclusion.

This method is intentionally lightweight and reproducible. It does **not** rank sentences with a learned model and it cannot generate new wording because it only reuses sentences from the source text.

Pretrained Spanish summarization models were initially considered, but the original exercise encountered compatibility and checkpoint issues in the execution environment. The deterministic approach was therefore retained as a stable baseline.

---

## 🙂 Sentiment Analysis

Sentiment is estimated with the multilingual Hugging Face model:

`nlptown/bert-base-multilingual-uncased-sentiment`

The model predicts ratings between one and five stars. These outputs are mapped to three sentiment categories:

- 1–2 stars → Negative
- 3 stars → Neutral
- 4–5 stars → Positive

In the original run, the analyzed portion of the text was classified as **positive**, with a `5 stars` prediction and a confidence score of approximately **0.478**.

An important limitation is that the implementation evaluates the **first 512 characters** of the document. The source text itself contains both positive and critical perspectives, so the result should be interpreted as a demonstration of pretrained-model inference rather than a complete document-level sentiment assessment.

---

## 🌍 Machine Translation

Spanish-to-English translation is performed using the pretrained MarianMT model:

`Helsinki-NLP/opus-mt-es-en`

The text is processed paragraph by paragraph to reduce truncation risk.

Each paragraph is tokenized independently and translated using beam search with four beams. The generated translation preserves the main meaning and structure of the three source paragraphs.

The experiment does not include a reference translation or a quantitative translation metric, so translation quality is assessed qualitatively.

---

## 💡 Key Takeaways

- Rule-based extractive summarization can provide a simple and reproducible baseline.
- Pretrained Transformer models enable useful NLP capabilities without task-specific training.
- Generic sentiment models can oversimplify nuanced or mixed-polarity documents.
- Input-length constraints must be considered when applying Transformer models.
- Segmenting long text can reduce truncation risk during machine translation.
- Model outputs should be interpreted together with the assumptions and limitations of the pipeline.

---

## 🛠️ Technologies

- **Python**
- **Hugging Face Transformers**
- **BERT**
- **MarianMT**
- **PyTorch**
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

The notebook contains the complete workflow, implementation, observed outputs and methodological interpretation of each NLP task.

---

## 🎓 Context

This project was developed as part of the **Unstructured Data Applications and Use Cases** course within the **Master's Degree in Applied Artificial Intelligence**.

It has been reorganized and documented as part of this technical portfolio while preserving the original objective, core NLP tasks and observed results.
