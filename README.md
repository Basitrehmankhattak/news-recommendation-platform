# Production-Ready Semantic News Recommendation Platform

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

An end-to-end, multi-stage news recommendation system engineered to handle large-scale user impressions from the Microsoft MIND dataset. The system solves the cold-start problem and delivers personalized, diverse article recommendations using vector similarity search, tree-based candidate ranking, and diversity re-ranking.

---

##  System Architecture & Pipeline Funnel

```mermaid
graph LR
    A[User Request / Cold-Start Query] --> B[FastAPI Engine]
    B --> C[MiniLM Embedding Generator]
    C -->|Stage 1: Vector Search| D[FAISS Index Retrieval]
    D -->|Stage 2: Scoring| E[LightGBM Ranker]
    E -->|Stage 3: Diversity| F[MMR Re-Ranking]
    F --> G[FastAPI Response / Streamlit Analytics]
    G -->|Real-time Click & Impression Logs| H[(PostgreSQL Database)]

Key Architectural HighlightsMulti-Stage Recommendation Funnel:Stage 1 — Candidate Retrieval (FAISS): Converts 100k+ news articles into dense vector representations using all-MiniLM-L6-v2 sentence transformers, indexing vectors in FAISS for sub-millisecond retrieval.Stage 2 — Candidate Ranking (LightGBM): Scores candidate items using a pre-trained LightGBM ranking model trained on user interaction signals and historical click-through rates (CTR).Stage 3 — Diversity Re-Ranking (MMR): Applies Maximal Marginal Relevance (MMR) algorithms to prevent recommendation echo chambers and balance relevance with content novelty.Cold-Start & Impression Handling: Incorporates dynamic popularity and category fallback logic for new users without historical interaction data.Production Logging Backend: Powered by a FastAPI REST API with PostgreSQL persistence to log user clicks, impressions, and CTR metrics in real time.Analytics Dashboard: Integrated with an interactive Streamlit dashboard to visualize model performance, impression analytics, and recommendation outputs.🛠️ Technology StackComponentTechnologies & LibrariesLanguages & FrameworksPython 3.10+, FastAPI, PydanticVector Search & MLFAISS, Sentence-Transformers (all-MiniLM-L6-v2), LightGBM, Scikit-LearnData ProcessingPandas, NumPy, PyArrow (Parquet Storage)Database & StoragePostgreSQL, SQLAlchemyContainerization & DeploymentDocker, Docker Compose, StreamlitDatasetMicrosoft News Dataset (MIND)📁 Project StructurePlaintextnews-recommendation-platform/
├── app/
│   ├── api/                  # FastAPI endpoint routes
│   ├── models/               # Pydantic schemas & SQLAlchemy DB models
│   └── services/             # Retrieval (FAISS), Ranking (LightGBM), & MMR logic
├── data/                     # Embeddings, FAISS indices, & Parquet datasets
├── dashboard/                # Streamlit analytics & demonstration interface
├── docker-compose.yml        # Orchestration for FastAPI, PostgreSQL, & Streamlit
├── Dockerfile
├── requirements.txt
└── README.md
🚀 Getting StartedPrerequisitesDocker Engine & Docker Compose installed.Local Setup via DockerClone the repository:Bashgit clone [https://github.com/Basitrehmankhattak/news-recommendation-platform.git](https://github.com/Basitrehmankhattak/news-recommendation-platform.git)
cd news-recommendation-platform
Spin up containerized services:Bashdocker-compose up -d --build
Access Endpoints:FastAPI Docs: http://localhost:8000/docsStreamlit Dashboard: http://localhost:8501PostgreSQL Server: localhost:5432
