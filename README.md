# RAGOps — Clinical Decision Support System

A modular Retrieval-Augmented Generation (RAG) pipeline built for clinical decision support, with hybrid retrieval, cross-encoder reranking, and MLflow experiment tracking.

---

## My Role
**RAG Pipeline Engineer (Member 2)** — Responsible for designing and implementing the full RAG pipeline including vector storage, document ingestion, dense/hybrid retrieval, and LangChain chain integration.

---

## Tech Stack

| Component | Technology |
|---|---|
| LLM | LLaMA 3 (via Ollama) |
| Vector Store | ChromaDB |
| Sparse Retrieval | BM25 (rank_bm25) |
| Reranker | ms-marco-MiniLM-L-6-v2 (Cross-Encoder) |
| Chain | LangChain |
| Experiment Tracking | MLflow |
| Containerization | Docker |

---

## Project Structure
├── Codes/
│   ├── vectorstore.py       # ChromaDB collection setup
│   ├── ingest.py            # Document ingestion (512 tokens, 10% overlap)
│   ├── retriever.py         # Dense, BM25, and Hybrid retrievers
│   ├── chain.py             # LangChain chain + ablation configs + MLflow
│   └── init.py          # Public API
├── progress.md              # Weekly progress tracker
└── RAGOps_Team_Plans_and_Prompts.docx

---

## Setup & Usage

```bash
pip install -r requirements.txt
ollama pull llama3
docker run -p 8000:8000 chromadb/chroma
python -m rag_pipeline.ingest --data_dir ./data/pubmed --chunk_size 512
python -m rag_pipeline.chain
```

---

## Retrieval Strategy

| Config | Retriever | Chunk Size | Reranker |
|---|---|---|---|
| 1-3 | Dense | 256 / 512 / 1024 | Off |
| 4-6 | BM25 | 256 / 512 / 1024 | Off |
| 7-9 | Hybrid | 256 / 512 / 1024 | On |