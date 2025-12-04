# 📄 ClauseFinder-AI

This is a Streamlit web app that analyzes **contract PDFs** using a **RAG (Retrieval-Augmented Generation)** pipeline built on:

- 📘 `PyPDFLoader` for PDF ingestion  
- 🧠 `sentence-transformers/all-MiniLM-L6-v2` for embeddings  
- 📚 `FAISS` for vector search  
- 🤖 Groq LLM (`meta-llama/llama-4-maverick-17b-128e-instruct`) for clause extraction & summarization  

The app extracts key legal clauses and generates a concise, user-friendly summary.

---

## 🚀 Features

- Upload a **single contract PDF**
- Automatically:
  - Splits the document into chunks
  - Builds a **FAISS** vector store
  - Retrieves highly relevant sections using RAG
- Extracts these clauses (copied **verbatim** from the contract context):
  - ✂️ **Termination Clause**
  - 🤫 **Confidentiality Clause**
  - ⚖️ **Liability Clause**
- Generates a **100–150 word summary** in simple English:
  - Purpose of the agreement  
  - Key obligations of each party  
  - Major risks / penalties (esp. around termination, confidentiality, liability)
- Saves every analysis into a CSV file:
  - `contracts_analysis.csv` with:
    - `contract_id` (filename)
    - `summary`
    - `termination_clause`
    - `confidentiality_clause`
    - `liability_clause`
    - `timestamp`
- Debug view of **raw LLM clause extraction output** for validation

---

## 🧱 Tech Stack

- **Language**: Python
- **Frontend**: [Streamlit](https://streamlit.io/)
- **LLM API**: [Groq](https://groq.com/) via `langchain-groq`
- **Embeddings**: `sentence-transformers/all-MiniLM-L6-v2` via `langchain-huggingface`
- **Vector Store**: FAISS
- **PDF Loader**: `PyPDFLoader` from `langchain_community`
- **Other**: `dotenv`, `csv`, `tempfile`, `datetime`, `re`, `json`

---

## 📁 Project Structure

For now the project is a single main file (for example):

```text
.
├── app.py                 # Main Streamlit app (code you shared)
├── requirements.txt       # Python dependencies (recommended)
├── contracts_analysis.csv # Auto-created after first analysis (output)
└── .env                   # Environment variables (contains GROQ_API_KEY)
