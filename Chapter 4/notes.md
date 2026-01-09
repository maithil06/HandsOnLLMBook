# 🧠 Chapter 4 — Text Classification with Large Language Models  
**Notes from _Hands-On Large Language Models_**

This chapter focuses on **text classification**, using pretrained language models to assign labels (e.g., sentiment, topic, intent) to text.  
The running example throughout the chapter is the **`rotten_tomatoes`** movie reviews dataset.

The chapter contrasts two major paradigms:

- **Representation Models** (encoder-based)
- **Generative Models** (sequence-to-sequence / decoder-based)

---
<img width="1376" height="768" alt="unnamed (1)" src="https://github.com/user-attachments/assets/dce79138-486a-4191-ae4f-e2c685a4f3f5" />


## 🧩 1. Text Classification with Representation Models

Representation models encode text into **vector representations** (embeddings) or directly into **class probabilities**.

### 🏗️ Approach 1: Task-Specific Models

These are foundation models already fine-tuned for a particular task.

**Examples:** RoBERTa, DeBERTa, DistilBERT

**Workflow:**
1. Load a pretrained classification model.
2. Run inference on labeled data.
3. Evaluate with standard classification metrics.

**Evaluation Metrics:**
- Confusion Matrix
- Precision
- Recall
- F1 Score
- Accuracy

This approach is straightforward and performs very well when labeled data exists.

---

### 🧬 Approach 2: Embeddings + Lightweight Classifier

Instead of using a model trained specifically for classification:

1. Use a general-purpose embedding model to convert text into vectors.
2. Freeze the embedding model (no training).
3. Train a small classifier on top of the embeddings.

**Common Classifiers:**
- Logistic Regression
- Linear SVM
- MLP

**Benefits:**
- Very efficient
- Low training cost
- Modular and flexible

---

### 🧪 Approach 3: Zero-Shot Classification

Used when **no labeled data** is available.

**Procedure:**
1. Embed each candidate label description  
   (e.g., `"A positive movie review"`, `"A negative movie review"`).
2. Embed each document.
3. Compute **cosine similarity** between document embeddings and label embeddings.
4. Assign the label with the highest similarity score.

This allows classification without any training data.

---

## 🤖 2. Text Classification with Generative Models

Generative models do not output class IDs.  
They generate **text** based on an instruction prompt.

### 🧾 Prompt Engineering

Classification becomes an instruction-following task:

Classifiy the text as negative or positive:


The model outputs the label as natural language.

---

### 🧠 T5 — Text-to-Text Transfer Transformer

**Architecture:** Encoder–Decoder

**Pretraining:**
- Masked span prediction
- Multi-task fine-tuning (instruction tuning)

T5 converts every NLP task into a **text generation problem**, including classification.

---

### 💬 ChatGPT (GPT-3.5)

**Architecture:** Decoder-only

**Training Pipeline:**
1. Pretraining on massive text corpora
2. Instruction Tuning (human-labeled prompts)
3. Preference Tuning (ranking responses to align with human values)

Used via API and controlled entirely through prompt design.

---

## 📌 3. Key Takeaways

### 🔎 Model Selection
- Representation: BERT, RoBERTa, DeBERTa
- Embeddings: consult the **MTEB leaderboard** for best-performing models

### 🧰 Flexibility vs Efficiency
| Paradigm | Strength |
|---------|---------|
Representation Models | High efficiency & accuracy on specific tasks |
Generative Models | High flexibility via prompting |

### 📊 Evaluation is Essential
Regardless of approach, always evaluate with:
- Accuracy
- Precision
- Recall
- F1 Score

---

## 🧭 Summary

Text classification in modern NLP can be solved via:
- Fine-tuned encoder models
- Embedding + classifier pipelines
- Zero-shot semantic matching
- Prompt-based generative models

Choosing the right approach depends on:
- Availability of labeled data
- Compute budget
- Need for flexibility vs performance
