# 📄 Smart PDF Q&A Assistant — RAG with Endee Vector DB

An AI-powered PDF Question & Answering system built using **Endee** as the vector database, **Groq LLaMA3** as the LLM, and **Streamlit** for the UI.

## 🧠 Problem Statement
Searching through large PDFs manually is slow. This app lets users upload any PDF and ask natural language questions — getting precise AI answers powered by RAG.

## 🏗️ System Design
```
PDF → Extract Text → Chunk → Embed (MiniLM) → Endee Vector DB
Query → Embed → Endee Search → Top Chunks → Groq LLaMA3 → Answer
```

## 🔧 How Endee is Used
- Creates HNSW index with cosine similarity
- Upserts embedded PDF chunks as vectors
- Semantic search to retrieve top-K relevant chunks

## 🚀 Setup & Run

### 1. Install dependencies
pip install streamlit groq PyMuPDF sentence-transformers requests python-dotenv

### 2. Start Endee
docker run -d -p 8080:8080 --name endee-server endeeio/endee-server:latest

### 3. Create .env file
GROQ_API_KEY=your_groq_api_key_here
ENDEE_URL=http://localhost:8080

### 4. Run
streamlit run app.py

## 🛠️ Tech Stack
- Vector Database: Endee
- LLM: Groq LLaMA3-8B
- Embeddings: sentence-transformers MiniLM
- UI: Streamlit
- PDF Parsing: PyMuPDF