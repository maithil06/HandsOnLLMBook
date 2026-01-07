# 🧠 Chapter 3 — How Large Language Models Work Internally  
**Notes from _Hands-On Large Language Models_**

This document summarizes the core internal mechanisms of modern **Generative Large Language Models (LLMs)**, based on Chapter 3 of the book.

---

## 🔁 1. High-Level Workflow: Autoregressive Generation

LLMs generate text **one token at a time**, rather than producing full sentences in one pass.

### How the loop works
1. The model receives a prompt.
2. It predicts the **next token**.
3. The predicted token is appended to the prompt.
4. The updated prompt is fed back into the model.
5. This loop repeats until the output is complete.

### Token streams and context length
Each input token is processed in its own computational stream in parallel.  
The total number of tokens that can be processed at once is the model’s **context length**.

---

## 🧱 2. The Three Major Components

During a forward pass, data flows sequentially through three core components:

### 1. Tokenizer
Converts raw text into **token IDs** from the model’s vocabulary.

### 2. Transformer Stack
A deep stack of layers where all meaningful computation and reasoning happens.

### 3. LM Head
A final linear layer that converts hidden representations into **probability scores** for every token in the vocabulary.

---

## 🧩 3. Inside a Transformer Block

The Transformer Stack consists of repeated **Transformer Blocks**, each containing two main sub-layers:

### 🔍 Self-Attention Layer
Allows each token to reference other tokens in the sequence to understand context  
(e.g., resolving pronouns like “it” or “they”).

### 🧠 Feedforward Neural Network
Acts as the model’s long-term memory, storing learned patterns and associations  
(e.g., knowing “The Shawshank” is often followed by “Redemption”).

---

## 🧮 4. How Attention Works — Queries, Keys, Values

Attention is computed using three learned matrices:

- **Query (Q)**
- **Key (K)**
- **Value (V)**

### Attention process
1. The current token’s **Query** is compared with previous tokens’ **Keys**.
2. This produces relevance scores.
3. These scores weight the corresponding **Values**.
4. The weighted values are combined into the token’s new representation.

### Multi-Head Attention
Instead of doing this once, the model runs multiple attention mechanisms in parallel.  
Each “head” learns different relationships (syntax, meaning, position, etc.).

---

## ⚡ 5. Efficiency and Optimization Techniques

As models scale, several optimizations are required for performance:

### 🧰 KV Caching
When generating token-by-token, recomputing previous attention is inefficient.  
**Key-Value caching** stores previous K and V matrices so only the new token must be processed.

### 🚀 Flash Attention
An optimized attention implementation that minimizes slow GPU memory access and maximizes throughput.

### 🧮 Grouped-Query Attention (GQA)
Used in models like **Llama 2** to reduce memory usage by sharing K and V across multiple attention heads.

---

## 🗳️ 6. Decoding — Choosing the Output

The model outputs **probability distributions**, not text.  
Decoding converts probabilities into actual tokens.

### Common decoding strategies

| Method | Description |
|------|------------|
| **Greedy Decoding** | Always selects the most probable next token |
| **Sampling** | Randomly samples from high-probability tokens for more creative output |
| **Temperature** | Controls randomness in sampling (higher = more creative) |

---

## 🧭 Summary

Large Language Models operate through:
- Autoregressive token generation
- Deep transformer computation
- Attention-based context modeling
- Memory-efficient inference optimizations
- Probabilistic decoding strategies

Together, these components enable modern LLMs to generate fluent, context-aware, and scalable language output.

---

