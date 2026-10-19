# Production-Ready Semantic News Recommendation Platform

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

An end-to-end, multi-stage news recommendation system engineered to handle large-scale user impressions from the Microsoft MIND dataset. The system solves the cold-start problem and delivers personalized, diverse article recommendations using vector similarity search, tree-based candidate ranking, and diversity re-ranking.

---

## 📐 System Architecture & Pipeline Funnel

```mermaid
graph LR
    A[User Request] --> B[FastAPI Engine]
    B --> C[MiniLM Embedding Generator]
    C --> D[FAISS Index Retrieval]
    D --> E[LightGBM Ranker]
    E --> F[MMR Re-Ranking]
    F --> G[FastAPI Response]
    G --> H[(PostgreSQL Database)]
