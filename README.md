# 📚 Book Embedding Search Engine

A semantic search engine that recommends books based on **meaning**, not keywords — powered by **local LLM embeddings**, **FAISS**, and **distributed vector search**.

---

## 🧩 Overview

This project builds a semantic book recommender by turning book metadata into dense vector embeddings and searching them using similarity metrics. Instead of matching exact words, it finds books that are **conceptually similar** based on themes, topics, and descriptions.

This project explores:

- Local embedding generation using **Ollama**
- High-dimensional vector search using **FAISS**
- Scaling embeddings and similarity search using **Databricks + PySpark**
- Comparing **local GPU** vs **cloud CPU cluster** performance

---

## ⚙️ How It Works

1. Load a dataset of books (`books.csv`).
2. Combine metadata — title, authors, categories, description — into a single text block.
3. Generate a **4096-dimensional embedding** for each book using `mxbai-embed-large` through Ollama’s local API.
4. Store embeddings in a **FAISS** index for fast similarity search.
5. Query the index to find books with similar semantic meaning.

---

## 🔄 Updates (Scaling to 20M+ Books)

I scaled this system from **7,000 → 20 million+ books** by generating embeddings with a **local GPU LLLM** and performing **distributed vector search** using **Databricks + PySpark + Parquet** on AWS.

---

## 🚀 What I Learned

### **Local GPU embedding is much faster**
GPUs handle large matrix operations efficiently, and running embeddings locally avoids scheduling, startup, and network overhead.

### **Embedding on Databricks was slower**
CPU-only workers and Spark task overhead make per-embedding tasks slower, even with autoscaling.

### **Vector search scales extremely well on Databricks**
Storing embeddings in **Parquet** and using **PySpark** allows parallel reads and distributed cosine similarity, making large-scale search far faster than single-machine FAISS.

---

## 🧰 Technologies Used

- Python + PySpark  
- Ollama (`mxbai-embed-large`)  
- FAISS  
- Databricks (Spark 3.5 LTS)  
- AWS EC2 (`m4.xlarge`, `m4.large`)  
- Parquet (columnar storage for embeddings)
