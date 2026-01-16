# 📘 Chapter 12 — Fine-Tuning Generation Models  
### *Hands-On Large Language Models*

This chapter explains how base foundation models are transformed into **helpful, instruction-following, and aligned AI assistants** through a structured fine-tuning and alignment pipeline.

Rather than focusing on representation learning, this chapter dives into **generation models**, alignment techniques, and practical training workflows used in modern LLM development.

---
<img width="1376" height="768" alt="unnamed (10)" src="https://github.com/user-attachments/assets/662696d1-89c6-4896-9225-354b244bd3d9" />

## 🧠 Overview

A pretrained language model understands language patterns but does not inherently:
- Follow instructions
- Produce helpful answers
- Align with human preferences or safety norms

This chapter introduces the **full training lifecycle** required to build production-grade generative LLMs.

---

## 🔁 1. The Three Training Steps

High-quality LLMs are trained using a three-stage paradigm.

### 🔹 1. Language Modeling (Pretraining)

- Trained on massive text corpora
- Objective: predict the next token
- Produces a base model with strong linguistic knowledge
- Does not yet follow instructions

---

### 🔹 2. Supervised Fine-Tuning (SFT)

Also known as **instruction tuning**.

- Uses labeled query–response pairs
- Teaches the model how to answer questions
- Introduces conversational and task-following behavior

---

### 🔹 3. Preference Tuning (Alignment)

Aligns the model with:
- Human preferences
- Helpfulness
- Safety constraints

This is the final step that turns a capable model into a reliable assistant.

---

## ⚙️ 2. Parameter-Efficient Fine-Tuning (PEFT)

Full fine-tuning is computationally expensive.  
PEFT methods update only a **small subset of parameters** while keeping the base model frozen.

---

### 🔧 Adapters

- Small trainable modules inserted into Transformer layers
- Only adapter weights are updated
- Original model weights remain unchanged

---

### 🔹 LoRA (Low-Rank Adaptation)

- Decomposes large weight matrices into two low-rank matrices
- Dramatically reduces trainable parameters
- Example: ~150M parameters → ~200K parameters per block

---

### 🔹 QLoRA (Quantized LoRA)

Combines LoRA with **4-bit quantization**.

Key techniques:
- Blockwise quantization
- NormalFloat (NF4) data type

Benefits:
- Enables fine-tuning on consumer GPUs
- Significantly reduces VRAM requirements
- Maintains strong model quality

---

## 🛡️ 3. Preference Tuning and Alignment

To ensure safe and helpful outputs, models are aligned using human feedback.

---

### 🧪 Reward Models and RLHF

Traditional approach:
1. Humans rank multiple model outputs
2. Train a separate reward model
3. Optimize the LLM using reinforcement learning (e.g., PPO)

Limitations:
- Complex training pipeline
- Training instability
- High computational cost

---

### 🔁 DPO (Direct Preference Optimization)

A simpler and more stable alternative.

- Removes the need for a reward model
- Uses the LLM itself as a reference
- Directly shifts token probabilities toward preferred responses
- More stable and efficient than PPO

---

## 📊 4. Evaluation of Generative Models

Evaluating LLMs is challenging due to their broad use cases.  
The chapter recommends a combination of approaches.

---

### 🔹 Word-Level Metrics

- **Perplexity**: confidence in predicting text
- **ROUGE / BLEU**: overlap with reference answers

---

### 🔹 Public Benchmarks

- **MMLU**: general knowledge
- **GSM8K**: mathematical reasoning
- **HumanEval**: code generation

---

### 🔹 LLM-as-a-Judge

- Uses a stronger LLM to evaluate outputs
- Scales better than manual evaluation
- Useful for rapid iteration

---

### 🔹 Human Evaluation

- Gold standard for alignment
- Humans vote on preferred responses
- Used in platforms such as Chatbot Arena

---

## 🛠️ 5. Practical Training Workflow

The chapter demonstrates a full workflow using **TinyLlama**.

### 🔹 Instruction Data Formatting

Conversation data is templated using special tokens:

<|user|> user query
<|assistant|> assistant response


---

### 🔹 Training Steps

1. Apply 4-bit quantization
2. Train using:
   - `SFTTrainer` for instruction tuning
   - `DPOTrainer` for preference alignment
3. Merge trained LoRA adapters back into the base model

---

## 🚀 Key Takeaways

- Base models require multiple fine-tuning stages to become assistants
- PEFT enables efficient training without full model updates
- LoRA and QLoRA dramatically reduce compute and memory costs
- DPO simplifies alignment compared to PPO-based RLHF
- Evaluation must combine automated metrics and human judgment
- Practical workflows are achievable on consumer hardware

---

📌 *Fine-tuning generation models is the final step that transforms raw language models into safe, helpful, and production-ready AI systems.*
