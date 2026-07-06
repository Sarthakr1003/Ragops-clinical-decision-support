# RAGOps — Week 1 Progress

## Week 1 — Baseline RAG Chain ✅ COMPLETE

| Task | File | Status |
|---|---|---|
| ChromaDB collection setup | `rag_pipeline/vectorstore.py` | ✅ Done |
| Fixed chunking ingestion (512 tokens, 10% overlap) | `rag_pipeline/ingest.py` | ✅ Done |
| Dense retriever | `rag_pipeline/retriever.py::dense_retriever()` | ✅ Done |
| Basic LangChain chain + clean `query()` API | `rag_pipeline/chain.py` | ✅ Done |
| `bm25_term_scores()` stub for XAI | `rag_pipeline/chain.py` | ✅ Done |
| Package `__init__` exposing public API | `rag_pipeline/__init__.py` | ✅ Done |

## Runtime Checklist

- [ ] `pip install -r rag_pipeline/requirements.txt`
- [ ] `ollama pull llama3`
- [ ] ChromaDB running: `docker run -p 8000:8000 chromadb/chroma`
- [ ] Ingestion smoke test: `python -m rag_pipeline.ingest --data_dir ./data/pubmed --chunk_size 512`
- [ ] Chain smoke test: `python -m rag_pipeline.chain`

## Handoffs

- **Member 1** — share Docker mount path for ChromaDB persistent storage
- **Member 3 (XAI)** — `retrieval_scores` and `bm25_term_scores()` ready
