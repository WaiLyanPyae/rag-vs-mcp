
# 📡 RAG + MCP News Classifier & Alert System

> A project exploring **real-time news classification, RAG-enhanced summarization, and MCP-inspired decision logic**.

---

## 📖 Overview

This project implements a **real-time news pipeline** that:

* Ingests live news articles (RSS feeds).
* Classifies them into categories: `hate_speech`, `misinformation`, `emergency`, `neutral`.
* Summarizes articles using **Retrieval-Augmented Generation (RAG)**.
* Applies **MCP-inspired agent logic** to decide system actions:

  * Trigger alerts (email/SMS/webhook).
  * Archive non-critical news.
  * Summarize misinformation/emergency items for context.
* Exposes results via a **REST API + live dashboard**.

The system provides a comparative framework:

* **Baseline:** Transformer-only (DistilBERT + BART).
* **Proposed:** Transformer + RAG + MCP decision layer.

---

## 📂 Project Structure

```plaintext
news-rag-mcp/
├─ ingestion/        # RSS poller
├─ backend/          # FastAPI backend (REST + streaming)
├─ models/           # Transformers (classification)
├─ rag/              # FAISS index + RAG summarizer
├─ agent/            # MCP-inspired decision engine
├─ eval/             # Evaluation scripts (metrics, latency)
├─ dashboard/        # React.js frontend (alerts, trends)
├─ infra/            # Postgres + Docker configs
├─ data/             # Datasets and indexes
│   ├─ raw/
│   ├─ processed/
│   └─ indexes/
├─ notebooks/        # Experiments / EDA
└─ scripts/          # Utility scripts
```

---

## 🔍 Research Questions

* **RQ1:** Effectiveness of transformer-based classification (DistilBERT, RoBERTa).
* **RQ2:** Improvement in summarization via Retrieval-Augmented Generation.
* **RQ3:** Structuring MCP-inspired logic for context-aware decision-making.

---

## 📈 Evaluation Criteria

| Aspect           | Baseline (Transformer Only)        | Proposed (RAG + MCP)        |
| ---------------- | ---------------------------------- | --------------------------- |
| Classification   | Precision, Recall, F1, Accuracy    | Same                        |
| Summarization    | ROUGE, BLEU (static model)         | ROUGE, BLEU + human eval    |
| Retrieval        | N/A                                | Cosine similarity relevance |
| Decision Logic   | Rule-based                         | MCP-inspired modular agent  |
| Alert Timeliness | Ingestion → alert latency measured | Same (<5s target)           |

---

## 🚧 Roadmap

* [x] RSS ingestion → Postgres
* [ ] Transformer baseline classifier
* [ ] Baseline summarization (BART)
* [ ] RAG summarization with FAISS
* [ ] MCP-inspired rule-based decision logic
* [ ] Full integration pipeline
* [ ] React dashboard
* [ ] Evaluation experiments
* [ ] Dissertation writing

---