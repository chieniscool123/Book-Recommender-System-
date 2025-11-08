# 📚 Book Embedding Search Engine  

Just a fun side project experimenting with **semantic search** using **FAISS** and **local LLM embeddings**.  
The idea is simple — turn book metadata and descriptions into vectors, then use FAISS to find similar books based on meaning instead of exact keywords.  

---

## 📑 Table of Contents  
- [Description](#description)   
- [Demo](#demo)  
- [Key Features](#key-features)  
- [Built With](#built-with)  
- [Future Improvements](#future-improvements)  

---

## 🧩Description  

This project creates a **semantic book search system** using **Ollama’s local embedding API** and **FAISS (Facebook AI Similarity Search)**.  

Instead of searching by keywords, the system finds books that are **conceptually similar** based on their titles, authors, categories, and descriptions.  

The process:  
1. Load a dataset of books (`books.csv`).  
2. Generate a **textual representation** for each book combining metadata (title, authors, description, etc.).  
3. Convert each book’s text into a **4096-dimensional embedding** using Ollama’s local model (`mxbai-embed-large`).  
4. Store all embeddings in a **FAISS index** for efficient similarity search.  
5. Query the index with a favorite book to find others with similar content or themes.  
