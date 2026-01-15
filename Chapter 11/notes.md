# 📘 Chapter 11 — Fine-Tuning Representation Models  
### *Hands-On Large Language Models*

This chapter focuses on adapting pretrained **representation models** such as BERT to achieve strong performance on **task-specific and domain-specific problems**.

While pretrained models work reasonably well out of the box, fine-tuning allows the model to internalize the nuances of a dataset and significantly improve downstream performance.

---

## 🧠 Overview

Fine-tuning updates the internal parameters of a pretrained model so it aligns with:
- A specific task (classification, NER, etc.)
- A specific domain (medical, legal, financial text)

The chapter introduces multiple strategies to balance **accuracy**, **data availability**, and **compute efficiency**.

---

## 🎯 1. Supervised Classification via Joint Training

In supervised fine-tuning, **all model parameters** are trained jointly.

### 🔹 Joint Training

- Representation model and classification head are trained together
- The model learns task-specific features rather than generic embeddings

### 🔹 Why This Matters

Frozen embeddings limit performance because:
- The encoder cannot adapt to the task
- The classifier must compensate for misaligned representations

Joint training produces more accurate and robust models.

---

## ⚙️ 2. Efficiency Through Layer Freezing

Fine-tuning large models is computationally expensive.  
Layer freezing offers a practical trade-off.

### 🔹 Bottleneck

- Freezing all encoder layers and training only the classification head
- Results in lower performance

### 🔹 Optimization Strategy

- Fine-tune only the **last few encoder blocks** (e.g., final five layers)
- Achieves near full fine-tuning performance
- Significantly reduces compute and training time

---

## 🧪 3. SetFit — Few-Shot Classification

When labeled data is extremely limited, **SetFit** provides an efficient alternative.

### 🔹 SetFit Workflow

1. **Sampling**  
   Generate positive and negative sentence pairs from a small labeled dataset

2. **Contrastive Fine-Tuning**  
   Fine-tune a SentenceTransformer using contrastive learning

3. **Classification**  
   Train a lightweight classifier on the resulting embeddings

### 🔹 Key Advantage

SetFit can achieve competitive performance using as few as **16 labeled examples per class**.

---

## 🔁 4. Continued Pretraining (Domain Adaptation)

General-purpose models like BERT are pretrained on sources such as Wikipedia, which may lack domain-specific vocabulary.

### 🔹 Continued Pretraining with MLM

- Perform Masked Language Modeling on domain-specific text
- Update internal representations before supervised fine-tuning

### 🔹 Benefits

- Better understanding of specialized terminology
- Improved downstream performance in niche domains

Common applications:
- Medical NLP
- Legal document analysis
- Financial text processing

---

## 🏷️ 5. Token-Level Classification (Named-Entity Recognition)

Not all tasks operate at the document level.

### 🔹 Token-Level Tasks

Named-Entity Recognition (NER) assigns labels to individual tokens rather than full texts.

---

### 🔹 Label Alignment

Subword tokenization introduces alignment challenges:
- Words may be split into multiple sub-tokens
- Labels must be propagated correctly

---

### 🔹 B-I-O Tagging Scheme

To handle token splits:
- **B-** (Beginning): first token of an entity
- **I-** (Inside): subsequent tokens of the same entity
- **O** (Outside): tokens not part of any entity

This ensures consistent entity labeling across sub-tokens.

---

## 🚀 Key Takeaways

- Fine-tuning unlocks task-specific performance
- Joint training outperforms frozen embeddings
- Layer freezing balances efficiency and accuracy
- SetFit enables strong results with minimal labeled data
- Domain adaptation improves understanding of specialized text
- Token-level tasks require careful label alignment

---

📌 *Fine-tuning transforms general-purpose language models into domain-aware, task-optimized systems.*
