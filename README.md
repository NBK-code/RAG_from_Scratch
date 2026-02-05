# Retrieval-Augmented Generation (RAG) — From Scratch

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline completely from scratch using Python, PyMuPDF, spaCy, Sentence Transformers, and a local LLM. It processes a PDF textbook, chunks it into meaningful segments, embeds them, retrieves relevant context for a query, and finally generates an answer using an LLM.

---

## Features

### **1. PDF Processing**
- Loads or downloads `Astronomy.pdf`
- Extracts text per page using **PyMuPDF**
- Cleans raw text for downstream processing

### **2. Sentence Chunking**
- Uses **spaCy**’s sentencizer for sentence splitting  
- Groups sentences into fixed-size chunks
  
### **3. Embedding**
- Uses **BAAI/bge-base-en-v1.5** (512-token window, 768-dimensional embeddings)
- Creates embeddings for every chunk
- Saves embeddings to CSV for reuse

### **4. Retrieval**
- Computes dot-product similarity between query embedding and chunk embeddings
- Returns top-k relevant text segments

### **5. LLM Generation**
- Loads a local LLM (Gemma-2B or Gemma-7B with quantization)
- Builds a prompt using:
  - retrieved context chunks  
  - the user query  
- Produces a grounded answer

---
