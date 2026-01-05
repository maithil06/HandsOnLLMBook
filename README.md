# 🧠 Hands-On Large Language Models  
### Learning & Code Companion

This repository documents my **end-to-end learning journey through the book**  
**_Hands-On Large Language Models: Language Understanding and Generation_ (O’Reilly)**,  
with full code implementations, experiments, notes, and practical extensions.

This is not just a reproduction of the book’s material.  
It is a hands-on engineering project focused on:
- deep understanding of modern LLM systems,
- building everything from scratch,
- experimenting beyond textbook examples, and
- creating reusable components for real-world applications.

---

## 📚 Learning Coverage

### **Part I — Understanding Language Models**
- Introduction to Large Language Models  
- Representing Language & Embeddings  
- Attention & Transformer Architectures  
- Encoder-Only and Decoder-Only Models  
- Training Paradigms of LLMs  
- Responsible LLM Development  

### **Part II — Using Pretrained Language Models**
- Text Classification  
- Clustering & Topic Modeling  
- Prompt Engineering  
- Advanced Text Generation  
- Memory & Agent Systems  
- Semantic Search & RAG  
- Multimodal Language Models  

### **Part III — Training & Fine-Tuning Language Models**
- Training Embedding Models  
- Contrastive Learning & SBERT  
- Fine-Tuning BERT  
- Generative Model Fine-Tuning  
- PEFT, LoRA & Quantization  
- RLHF & Preference Optimization  

---

## 🗂️ Repository Structure

```text
hands-on-llms/
│
├── 01_understanding_language_models/
│   ├── introduction_to_llms.ipynb
│   ├── embeddings_and_attention.ipynb
│   ├── transformer_architectures.ipynb
│   └── notes.md
│
├── 02_tokens_and_embeddings/
│   ├── tokenization_experiments.ipynb
│   ├── word_vs_subword.ipynb
│   ├── contextual_embeddings.ipynb
│   └── notes.md
│
├── 03_inside_transformers/
│   ├── forward_pass.ipynb
│   ├── attention_mechanisms.ipynb
│   ├── caching_and_speedup.ipynb
│   └── notes.md
│
├── 04_text_classification/
│   ├── sentiment_analysis.ipynb
│   ├── embedding_based_classification.ipynb
│   └── notes.md
│
├── 05_clustering_and_topic_modeling/
│   ├── text_clustering_pipeline.ipynb
│   ├── bertopic.ipynb
│   └── notes.md
│
├── 06_prompt_engineering/
│   ├── prompting_strategies.ipynb
│   ├── chain_of_thought.ipynb
│   ├── tree_of_thought.ipynb
│   └── notes.md
│
├── 07_advanced_text_generation/
│   ├── langchain_chains.ipynb
│   ├── memory_and_agents.ipynb
│   └── notes.md
│
├── 08_semantic_search_and_rag/
│   ├── vector_search.ipynb
│   ├── rag_pipeline.ipynb
│   ├── rag_evaluation.ipynb
│   └── notes.md
│
├── 09_multimodal_models/
│   ├── clip_and_embeddings.ipynb
│   ├── image_captioning.ipynb
│   └── notes.md
│
├── 10_training_and_finetuning/
│   ├── embedding_training.ipynb
│   ├── sbert_and_contrastive.ipynb
│   ├── finetuning_bert.ipynb
│   ├── peft_and_lora.ipynb
│   └── notes.md
│
├── datasets/
├── experiments/
├── utils/
└── README.md
