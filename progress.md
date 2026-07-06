# RAGOps — RAG Pipeline Progress Tracker

## Member 2 — RAG Pipeline Engineer

---

## Week 1 — Baseline RAG Chain ✅ COMPLETE

| Task | File | Status |
|---|---|---|
| ChromaDB collection setup | `rag_pipeline/vectorstore.py` | ✅ Done |
| Fixed chunking ingestion (512 tokens, 10% overlap) | `rag_pipeline/ingest.py` | ✅ Done |
| Dense retriever | `rag_pipeline/retriever.py::dense_retriever()` | ✅ Done |
| Basic LangChain chain + clean `query()` API | `rag_pipeline/chain.py` | ✅ Done |
| `bm25_term_scores()` stub for XAI | `rag_pipeline/chain.py` | ✅ Done |
| Package `__init__` exposing public API | `rag_pipeline/__init__.py` | ✅ Done |

### Runtime Checklist
- [ ] `pip install -r rag_pipeline/requirements.txt`
- [ ] `ollama pull llama3`
- [ ] ChromaDB running: `docker run -p 8000:8000 chromadb/chroma`
- [ ] Ingestion smoke test: `python -m rag_pipeline.ingest --data_dir ./data/pubmed --chunk_size 512`
- [ ] Chain smoke test: `python -m rag_pipeline.chain`

### Handoffs
- **Member 1** — share Docker mount path for ChromaDB persistent storage
- **Member 3 (XAI)** — `retrieval_scores` and `bm25_term_scores()` ready for XAI layer

---

## Week 2 — Hybrid Retrieval + Reranker ⬜ NOT STARTED

| Task | File | Status |
|---|---|---|
| BM25 retriever (rank_bm25) | `rag_pipeline/retriever.py::bm25_retriever()` | ⬜ Stub ready |
| Hybrid retriever (dense + BM25) | `rag_pipeline/retriever.py::hybrid_retriever()` | ⬜ Stub ready |
| Cross-encoder reranker (ms-marco-MiniLM-L-6-v2) | `rag_pipeline/retriever.py` | ⬜ Not started |
| Ablation configs: bm25 + hybrid across 256/512/1024 | `rag_pipeline/chain.py::ABLATION_CONFIGS` | ⬜ Not started |
| MLflow experiment tracking for all 9 configs | `rag_pipeline/chain.py` | ⬜ Partial (dense only) |

---

## Week 3 — XAI Layer + Retrieval Score Exposure ⬜ NOT STARTED

| Task | File | Status |
|---|---|---|
| Expose raw `retrieval_scores` to Member 3 | `rag_pipeline/chain.py` | ✅ Done (Week 1) |
| Full `bm25_term_scores()` with corpus-level IDF | `rag_pipeline/chain.py` | ⬜ Not started |
| Ablation results → Paper Table 1 | `run_ablation()` | ⬜ Not started |

---

## Experiment Matrix — Paper Table 1

| Config | retriever_type | chunk_size | reranker | Status |
|---|---|---|---|---|
| 1 | dense | 256 | OFF | ⬜ |
| 2 | dense | 512 | OFF | ⬜ |
| 3 | dense | 1024 | OFF | ⬜ |
| 4 | bm25 | 256 | OFF | ⬜ |
| 5 | bm25 | 512 | OFF | ⬜ |
| 6 | bm25 | 1024 | OFF | ⬜ |
| 7 | hybrid | 256 | ON | ⬜ |
| 8 | hybrid | 512 | ON | ⬜ |
| 9 | hybrid | 1024 | ON | ⬜ |
