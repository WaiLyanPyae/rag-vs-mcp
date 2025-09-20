# News-RAG-MCP

This project is a news aggregation and analysis system that uses a Retrieval-Augmented Generation (RAG) approach to process and summarize news articles. It's built with a modular, Microservices-like Communication Pattern (MCP) architecture to handle various stages of the news pipeline, from ingestion to real-time user dashboards.

-----

## 📂 Project Structure

The project is organized into several key directories, each with a specific purpose.

  * **`ingestion/`**: Contains the code for polling RSS feeds or listening to webhooks to ingest raw news articles.
  * **`backend/`**: A **FastAPI** application that serves as the core of the system, handling REST APIs and real-time data streaming (SSE/WebSocket).
  * **`models/`**: Stores code for training and running **Hugging Face** models for tasks like summarization or classification.
  * **`rag/`**: Manages the **FAISS** index for efficient vector search and the code for generating news summaries using a RAG approach.
  * **`agent/`**: Holds the decision logic inspired by the Microservices Communication Pattern (MCP), defined in **YAML rules** and executed by an engine to orchestrate the pipeline.
  * **`eval/`**: Scripts for evaluating the performance of the system, including RAG accuracy and summarization quality.
  * **`dashboard/`**: The frontend application, built with **React (Vite)**, for visualizing real-time data and interacting with the system.
  * **`infra/`**: Configuration files for infrastructure, including **`docker-compose`**, database schemas, and optional Kafka setup.
  * **`scripts/`**: A collection of quick-run scripts for common tasks like seeding the database or running specific parts of the pipeline.
  * **`data/`**: The main data storage directory, broken down into:
      * **`data/raw/`**: Raw, unprocessed JSON or news article files.
      * **`data/processed/`**: Cleaned and normalized JSON data ready for further processing.
      * **`data/indexes/`**: Stores the **FAISS** index and any serialized data (pickles) used by the RAG system.
  * **`notebooks/`**: A space for **Jupyter notebooks** used for ad-hoc exploratory data analysis (EDA), evaluation, and plotting results.

-----