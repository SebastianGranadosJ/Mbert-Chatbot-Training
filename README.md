# 🧠 Multilingual FAQ Chatbot – mBERT Fine-Tuned for Finance

A multilingual FAQ chatbot built using **Multilingual BERT (mBERT)** and trained on a **synthetic bilingual dataset (Spanish + English)** to classify and answer financial questions related to **StarkAdvisor**, a financial advisory platform, and general finance concepts.


![Made with mBERT](https://img.shields.io/badge/Made%20with-mBERT-blueviolet)

---

## 📘 Overview

This project implements an intelligent FAQ chatbot powered by a fine-tuned **Multilingual BERT model** capable of understanding and classifying user queries in both English and Spanish.

Instead of generating free-form answers, the chatbot works by:

- **Preprocessing and normalizing** the user question (lemmatization, accent removal, etc.)
- **Classifying** the question into one of the predefined FAQ categories
- **Returning** the predefined answer associated with that category

The training corpus includes **synthetic bilingual data**, allowing the chatbot to recognize question patterns across languages and map them to the correct financial FAQ category.

Typical questions include topics related to:

- StarkAdvisor platform usage  
- Trading concepts  
- Market indices  
- Investment fundamentals  
- General finance knowledge  

---

## 🏗️ Project Architecture

The system follows a clear **preprocessing → training → inference** workflow:

Raw FAQs JSON
     ↓
Normalization (lemmatization, deduplication, accent removal)
     ↓
Dataset creation (multilingual questions + labels)
     ↓
mBERT fine-tuning (sequence classification)
     ↓
Model export (HuggingFace format)
     ↓
Inference pipeline (normalize → classify → answer)


## 🧪 Technologies Used

### 🔤 Transformers (Hugging Face)
Used to load and fine-tune the **Multilingual BERT** model.  
`AutoTokenizer`, `AutoModelForSequenceClassification`, and `Trainer` enable:

- Tokenization  
- Model fine-tuning  
- Evaluation metrics  
- Inference pipelines  

---

### 🗣️ spaCy (es/en models)
Used for **lemmatization** in both Spanish and English.

Since the chatbot training corpus contains both languages, each question must be normalized using the **correct language-specific lemmatizer**.

---

### 🔍 rapidfuzz
Provides efficient **string similarity comparison**.  
Used to:

- Detect near-duplicate questions  
- Remove redundant or highly similar entries (>95% similarity)

This ensures a **clean and diverse training set**.

---

### 📦 Datasets (HuggingFace)
Used to define dataset features and convert normalized text into **BERT-compatible tensors**.

---

### 🔢 scikit-learn
Specifically used for:

- **Stratified train-test split**, ensuring each FAQ category (class) is proportionally represented.  

Since each question type corresponds to a class, stratification helps maintain **balanced class distribution**.

---

### 💾 PyTorch
Used as the backend for:

- Model training  
- GPU acceleration  
- Tensor operations  

---

### 🔠 unicodedata
Used to:

- Remove accents  
- Standardize Unicode text before tokenization  

---

### 📄 JSON
Used for:

- Storing the normalized FAQ corpus  
- Mapping labels ↔ FAQ IDs  
- Selecting the correct predefined answer during inference  

---

## 📚 Features

### ✔️ Multilingual (English + Spanish)
Both the training corpus and the preprocessing pipeline support **two languages**.

---

### ✔️ Robust normalizer
Handles:

- Lowercasing  
- Accent removal  
- Punctuation cleanup  
- Language-specific lemmatization  
- Duplicate removal  
- Similarity-based deduplication  

---

### ✔️ Fine-tuned mBERT classifier
mBERT is fine-tuned to classify user questions into **predefined FAQ categories**.

---

### ✔️ Complete inference pipeline
Input question → normalize → classify → return predefined answer.

