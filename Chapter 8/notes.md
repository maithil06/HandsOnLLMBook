# 📓 Chapter 8 — Semantic Search & Retrieval-Augmented Generation (RAG)  
### *Hands-On Large Language Models*

<img width="1376" height="768" alt="unnamed (6)" src="https://github.com/user-attachments/assets/1ea0ab23-e877-4c67-90c4-9c77e35372d9" />


This chapter explains how to connect Large Language Models to **external knowledge sources** in order to solve two fundamental problems:

1. **Lack of access to private or new data**
2. **Hallucinations in generated responses**

It introduces the modern information retrieval stack, moving from basic semantic search to fully-featured **RAG systems**.

---

## 🧠 Overview

Modern AI search systems are built on three increasingly sophisticated layers:

1. **Dense Retrieval**
2. **Reranking**
3. **Retrieval-Augmented Generation (RAG)**

Each layer improves both **accuracy** and **trustworthiness** of LLM outputs.

---

## 🧱 1. The Three Pillars of Modern Search

### 🔎 Dense Retrieval  
Uses embeddings to retrieve documents by **semantic meaning** instead of keyword overlap.

### 🧮 Reranking  
A refinement step that reorders results to push the most relevant documents to the top.

### 🧬 RAG  
Combines document retrieval with generative models so answers are produced **only from retrieved knowledge**.

---

## 🧬 2. Dense Retrieval — The Foundation

Dense retrieval relies on **vector embeddings** introduced in earlier chapters.

### ⚙️ Mechanism

1. Convert the user query into an embedding vector  
2. Find **nearest neighbors** in vector space  
3. Return documents with the highest similarity

### 🗄️ Vector Databases

To perform this efficiently at scale, systems use:
- Vector databases
- FAISS or similar ANN libraries

### 🧩 Chunking Strategy

Long documents must be split into smaller pieces before embedding.

**Why:**  
Embedding entire documents dilutes meaning and exceeds context limits.

**Common strategies:**
- Sentence-level chunking
- Paragraph chunking
- Sliding windows with overlap (to preserve context continuity)

---

## 🧪 3. Reranking — The Refinement Stage

Dense retrieval is fast but imperfect.  
A two-stage pipeline improves precision:

### 🧭 Stage 1: Initial Retrieval  
Retrieve a large candidate set (e.g., top 100 documents) using dense retrieval or keyword search.

### 🎯 Stage 2: Reranker

Use a **Cross-Encoder** model that:
- Reads the query and document together
- Produces a precise relevance score

**Result:**  
Search quality improves dramatically by pushing the best matches to the top.

---

## 🧠 4. Retrieval-Augmented Generation (RAG)

RAG grounds LLM outputs in retrieved facts to eliminate hallucinations.

### 🔁 RAG Workflow

1. **Retrieve** relevant documents  
2. **Augment** the prompt with retrieved context  
3. **Generate** the answer using only that context

**Example Prompt:**

### 🧾 Grounded Generation

This allows:
- Fact-based responses
- Source citation
- Reduced hallucination risk

---

## 🧠 5. Advanced RAG Techniques

### 🧩 Query Rewriting
Use an LLM to convert vague queries into precise ones.

**Example:**

"Where do they live?"
"Where do dolphins live?"


### 🔗 Multi-Hop RAG
For complex questions requiring sequential reasoning.

**Example:**

Did the founder of Amazon go to space?
Who founded Amazon?
Did that person go to space?


### 🔀 Multi-Query RAG
Split comparison queries into multiple searches.

**Example:**

"Company revenue 2020 vs 2023"
Search revenue 2020
Search revenue 2023


### 🤖 Agentic RAG
Give the LLM tools (search, calculator, APIs) and allow it to decide how to retrieve and combine information, effectively turning the RAG pipeline into an **autonomous agent**.

---

## 📊 6. Evaluation

### 🔍 Search Evaluation

Common metric:
- **Mean Average Precision (MAP)**  
  Rewards systems that place relevant results higher.

### 🧪 RAG Evaluation

Uses **LLM-as-a-Judge** approaches (e.g., Ragas) to score outputs on:

- **Faithfulness** — did the answer stick to retrieved context?
- **Answer Relevance** — did it answer the user’s question?

---

## 🚀 Key Takeaways

- Dense retrieval provides semantic understanding
- Reranking dramatically improves precision
- RAG grounds LLM outputs in factual knowledge
- Advanced RAG techniques enable complex reasoning
- Proper evaluation is essential for production systems

---

📌 *These techniques form the backbone of modern AI search engines, knowledge assistants, and enterprise LLM applications.*
