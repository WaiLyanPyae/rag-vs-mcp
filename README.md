Got it ✅ — here’s your `README.md` rewritten in **clean, proper Markdown format** with headings, code blocks, and tables styled neatly.

---

# 📡 RAG + MCP News Classifier & Alert System

> A dissertation project exploring **real-time news classification, RAG-enhanced summarization, and MCP-inspired decision logic**.

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

## ⚙️ Setup

### 1. Clone repository

```bash
git clone https://github.com/your-username/news-rag-mcp.git
cd news-rag-mcp
```

### 2. Create environment

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```

### 3. Database setup

Run Postgres with Docker:

```bash
cd infra
docker compose up -d
cd ..
```

Load schema:

```bash
docker exec -i newsdb psql -U postgres -d newsdb < infra/schema.sql
```

### 4. Start services

**Ingest RSS → DB**

```bash
python ingestion/rss_poller.py
```

**Classification API (zero-shot baseline)**

```bash
uvicorn models.classify_service:app --reload --port 8001
```

**Summarization API (baseline + RAG)**

```bash
python rag/build_index.py
uvicorn rag.summarize_service:app --reload --port 8002
```

**Decision engine (MCP-inspired rules)**

```bash
python agent/engine.py
```

**Backend (alerts API + SSE stream)**

```bash
uvicorn backend.app:app --reload --port 8000
```

---

## 🧪 Evaluation

### Classifier Metrics

```bash
python eval/classifier_metrics.py
```

### Summarization Metrics

```bash
python eval/summarization_metrics.py
```

---

## 📊 Dashboard (React.js)

```bash
cd dashboard
npm install
npm run dev
```

The dashboard connects to the backend’s `/alerts/stream` SSE endpoint.

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

## 📚 References

* [Hugging Face Transformers](https://huggingface.co/transformers/)
* [FAISS](https://faiss.ai/)
* [Apache Kafka](https://kafka.apache.org/)
* [Model Context Protocol (MCP)](https://modelcontextprotocol.io/)

---

## 📜 License

MIT – for academic research and educational use.

---
