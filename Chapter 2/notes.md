# Chapter 2: Tokens and Embeddings

This chapter explores the fundamental mechanisms that allow Large Language Models (LLMs) to process and understand text by converting raw language into numerical representations that neural networks can compute.
---
<img width="1376" height="768" alt="Chapter 2 Summary" src="https://github.com/user-attachments/assets/e868d6ad-863c-42b6-9ba3-cf6d495da867" />

## Tokenization: The Language of Models

LLMs do not process raw text directly. Instead, they operate on tokens, which are chunks of text that may represent characters, subwords, or whole words.

### The Tokenization Pipeline

1. Input text is broken into tokens by a tokenizer  
2. Each token is mapped to an integer called a Token ID  
3. The model processes these IDs and outputs new ones  
4. The tokenizer decodes the output IDs back into readable text

---

### Tokenization Methods

| Method | Description |
|------|------------|
| Word Tokenization | Maps complete words to tokens |
| Character Tokenization | Maps individual characters |
| Byte Tokenization | Uses raw bytes |
| Subword Tokenization | Breaks rare words into meaningful sub-parts while keeping common words whole |

Example:

"apologizing" → "apolog" + "izing"


This approach balances vocabulary size with expressive power.

---

### Tokenizer Design Considerations

Different models adopt different tokenizer designs.

| Model | Design Characteristics |
|-----|----------------|
| BERT | Case-sensitive, special classification tokens |
| GPT-2 and GPT-4 | Byte-level BPE, special tokens like `<|endoftext|>` |
| StarCoder | Code-optimized tokens, whitespace-sensitive |

Design choices strongly influence performance on tasks such as programming, chat systems, and document understanding.

---

## Embeddings: Capturing Meaning

After tokenization, tokens are transformed into embeddings. These are dense numerical vectors that encode semantic meaning.

---

### Token Embeddings

Each model stores a lookup table of vectors, one for every token in its vocabulary.

During execution, these static vectors become contextualized. The meaning of each token shifts depending on the surrounding words.

---

### Text Embeddings

Models can also generate a single embedding vector for complete sentences, paragraphs, or entire documents.

These representations are essential for applications such as semantic search, clustering, recommendation systems, and retrieval-augmented generation.

---

## Word2Vec and Contrastive Training

Modern embedding techniques build on foundational work from word2vec (2013).

### Training Mechanism

Word2vec is trained using a sliding window over text. It learns to predict neighboring words while using negative sampling to distinguish meaningful context from random noise.

This process pulls semantically similar words closer together in vector space.

---

## Beyond Text: Embeddings in Recommendation Systems

Embedding concepts extend beyond language.

A practical example is a music recommendation system. Playlists are treated as sentences, and songs are treated as tokens. By training a word2vec model on this data, the system learns which songs appear in similar contexts and can recommend tracks that are semantically aligned with a user's listening habits.

---
