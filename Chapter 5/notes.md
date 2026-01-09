# 📘 Chapter 5 — Text Clustering & Topic Modeling  
### *Hands-On Large Language Models*

This chapter explores how to uncover structure and meaning from large collections of unstructured text using **unsupervised learning**.  
The techniques are demonstrated on **ArXiv abstracts** from the *Computation and Language* domain.

---

## 🧠 Core Concepts

### 🔹 Goal
Group semantically similar documents and discover latent topics **without labeled data**.

---

## 🧩 Text Clustering Pipeline

The chapter presents a standard three-stage pipeline:

### 1️⃣ Embedding
Documents are converted into numerical vectors using pretrained embedding models.

**Example:**
```python
thenlper/gte-small

## 2️⃣ Dimensionality Reduction

High-dimensional embeddings are compressed to make clustering feasible while preserving structure.

**Technique used:**
- **UMAP** (*Uniform Manifold Approximation and Projection*)  
  → typically reduced to **~5 dimensions**

---

## 3️⃣ Clustering

Documents are grouped based on density in the reduced space.

**Algorithm:**
- **HDBSCAN**

### Why HDBSCAN?

- Does **not** force every point into a cluster  
- Naturally detects **outliers**  
- Works well for **uneven cluster densities**

---

## 🧵 Topic Modeling with **BERTopic**

BERTopic extends the clustering pipeline into an interpretable topic modeling framework.

---

## 🧱 Modular Design

BERTopic behaves like **Lego blocks**:

> You can swap embedding models, dimensionality reduction methods, and clustering algorithms depending on your use case.

---

## 🧮 Topic Representation — **c-TF-IDF**

Instead of computing TF-IDF per document, BERTopic computes it **per cluster**:

> **Class-based TF-IDF (c-TF-IDF)** highlights words that are important to one topic relative to the entire corpus.

This produces **highly interpretable topic keywords**.

---

## 🛠 Refining Topic Representations

The chapter explores advanced techniques to improve topic quality beyond simple bag-of-words.

### 🔑 KeyBERTInspired
Extracts keywords using **semantic similarity**, removing irrelevant words and stopwords.

### 🧬 Maximal Marginal Relevance (MMR)
Diversifies topic keywords to reduce redundancy.

**Example:**  
Avoids listing both *"summary"* and *"summaries"* in the same topic.

---

## 🤖 Generative AI for Topic Labeling

Generative models (e.g., **Flan-T5**, **GPT-3.5**) are used to create concise, human-readable topic names.

Instead of: summarization, abstract, document, sentence
The model produces: "Summarization"


---

## 🚀 Key Takeaways

- Clustering + Topic Modeling can be done **fully unsupervised**
- **BERTopic** provides a flexible, modular framework
- Combining **embeddings, UMAP, and HDBSCAN** yields powerful semantic clusters
- **Generative AI** transforms raw keywords into meaningful topic labels

---

## 🧭 Recommended Stack

| Stage | Tool |
|------|------|
Embedding | Sentence-Transformers |
Reduction | UMAP |
Clustering | HDBSCAN |
Topic Modeling | BERTopic |
Keyword Refinement | KeyBERT, MMR |
Label Generation | Flan-T5, GPT-3.5 |

---

📌 *This pipeline forms the foundation of modern semantic search, document understanding, and large-scale text analytics systems.*

---

### Next Steps

If you’d like, I can also:
- Add **code snippets** for each stage, or  
- Help you structure this into a full project repository (`notebooks/`, `src/`, `data/`, etc.)
