<div align="center">

# ReconcileAI

### Intelligent Claim Resolution

**Healthcare Payment Reconciliation Platform with AI-Powered Matching**

[![Status](https://img.shields.io/badge/Status-Planning-blue?style=flat)]()
[![Java](https://img.shields.io/badge/Java-17-ED8B00?style=flat&logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2-6DB33F?style=flat&logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=flat&logo=react&logoColor=black)](https://react.dev)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?style=flat&logo=postgresql&logoColor=white)](https://postgresql.org)
[![Apache Kafka](https://img.shields.io/badge/Kafka-3.6-231F20?style=flat&logo=apachekafka&logoColor=white)](https://kafka.apache.org)

*ITCS 6112 — Software Systems Design and Implementation — Spring 2026*
*University of North Carolina at Charlotte*

---

</div>

## Overview

ReconcileAI automates healthcare payment reconciliation by matching insurance payments, patient payments, and provider adjustments to their corresponding claims. When rule-based matching fails (roughly 15–20% of cases due to missing or incorrect reference numbers), an ML service predicts the most likely claim matches with confidence scores and explainable reasoning.

## Architecture

```
┌───────────────┐     ┌───────────────────┐     ┌─────────────────────┐
│  EOB / Payment│────▶│   Kafka Broker    │────▶│  Event Ingestion    │
│  Sources      │     │   (Event Bus)     │     │  Service (Java)     │
└───────────────┘     └───────────────────┘     └────────┬────────────┘
                                                         │
                                                         ▼
                                              ┌──────────────────────┐
                                              │  Reconciliation      │
                                              │  Engine (Java)       │
                                              │  CQRS + Saga         │
                                              └──────────┬───────────┘
                                                         │
                                          ┌──────────────┼──────────────┐
                                          │ Rule Match   │ No Match     │
                                          ▼              ▼              │
                                   ┌─────────────┐ ┌────────────────┐   │
                                   │ PostgreSQL  │ │ ML Matching    │   │
                                   │ (Matched)   │ │ Service (Py)   │   │
                                   └─────────────┘ │ XGBoost + SHAP │   │
                                                   └──────┬─────────┘   │
                                                          │             │
                                                          ▼             │
                                                  ┌─────────────────┐   │
                                                  │ Staff Dashboard │◀──┘
                                                  │ (React)         │
                                                  └─────────────────┘
```

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Java 17, Spring Boot 3.2 |
| **Streaming** | Apache Kafka |
| **ML Service** | Python 3.11, FastAPI, XGBoost, SHAP |
| **Frontend** | React 18, TypeScript |
| **Database** | PostgreSQL 16, Redis |
| **DevOps** | Docker, Kubernetes, AWS, GitHub Actions |

## Team

<table>
  <tr>
    <td align="center" width="25%">
      <a href="https://github.com/anuraagpotdaar">
        <img src="docs/team/anuraag_circle.png" width="120" alt="Anuraag Potdaar"/><br/>
        <b>Anuraag Potdaar</b>
      </a><br/>
      <sub>Dashboards & DevOps</sub><br/>
      <sub>📧 Main Contact</sub>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/ShubhamSakhareGEM">
        <img src="docs/team/shubham_circle.png" width="120" alt="Shubham Sakhare"/><br/>
        <b>Shubham Sakhare</b>
      </a><br/>
      <sub>Event Ingestion & Streaming</sub>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/aniruddhadesh1609">
        <img src="docs/team/aniruddha_circle.png" width="120" alt="Aniruddha Deshpande"/><br/>
        <b>Aniruddha Deshpande</b>
      </a><br/>
      <sub>Reconciliation Engine</sub>
    </td>
    <td align="center" width="25%">
      <a href="https://github.com/lavannya22">
        <img src="docs/team/lavannya_circle.png" width="120" alt="Lavannya Patil"/><br/>
        <b>Lavannya Patil</b>
      </a><br/>
      <sub>ML Matching Service</sub>
    </td>
  </tr>
</table>

## Project Timeline

| Weeks | Phase |
|-------|-------|
| 1–2 | ✅ Setup, team agreement, architecture design |
| 3–4 | Event ingestion, Kafka pipeline |
| 5–6 | Reconciliation engine, CQRS + Saga |
| 7–8 | Database schema, REST APIs, Redis caching |
| 9–10 | ML feature engineering, model training |
| 11–12 | ML service integration, SHAP explanations |
| 13–14 | React dashboards, staff workqueue |
| 15–16 | Testing, documentation, demo |

## License

This project is developed as part of ITCS 6112 at UNC Charlotte.

---

<div align="center">

**ReconcileAI** — Built with ☕ and 🐍 at UNC Charlotte

</div>
