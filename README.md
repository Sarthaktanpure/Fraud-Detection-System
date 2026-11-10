# 🛡️ Fraud Detection System
### AI-Powered Financial Fraud Detection Platform

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&duration=3000&pause=900&color=22D3EE&center=true&vCenter=true&width=850&lines=Detect+Suspicious+Financial+Activity;XGBoost+%2B+Isolation+Forest;Full-Stack+Fintech+Engineering;Turning+Transaction+Data+into+Risk+Signals" alt="Typing SVG" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" />
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" />
  <img src="https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" />
</p>

<p align="center">
  <b>A full-stack financial fraud detection platform combining supervised machine learning, anomaly detection, secure REST APIs, and an interactive analytics dashboard.</b>
</p>

<p align="center">
  <a href="#-overview">Overview</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-detection-engine">Detection Engine</a> •
  <a href="#-features">Features</a> •
  <a href="#-technology">Technology</a> •
  <a href="#-setup">Setup</a>
</p>

---

## `~/overview` — Why This Project?

Financial transactions generate large volumes of data, making suspicious activity difficult to identify through manual monitoring alone.

Traditional rule-based approaches can struggle with evolving transaction patterns and unusual behavior. A fraud detection system needs to evaluate transaction characteristics, identify anomalies, and make risk information accessible to the people investigating them.

**Fraud Detection System** explores this problem through a full-stack application that combines machine learning with backend services and a React-based analytics interface.

The platform processes **20,000+ synthetic financial transactions** through an end-to-end detection pipeline.

### Project highlights

| Capability | Implementation |
|---|---|
| Transaction processing | 20,000+ synthetic transactions |
| Supervised detection | XGBoost |
| Anomaly detection | Isolation Forest |
| Backend services | Node.js, Express.js |
| ML inference service | Python, Flask |
| Database | PostgreSQL |
| Frontend | React.js |
| API layer | 10+ RESTful APIs |
| Security | JWT, bcrypt, RBAC, input validation |

---

## `~/architecture` — System Design

The application separates the user interface, backend application services, database persistence, and machine learning inference.

### High-level architecture

```mermaid
flowchart TB
    USER["Financial Analyst / Administrator"]

    subgraph FRONTEND["Presentation Layer"]
        UI["React Dashboard"]
        METRICS["Fraud Analytics"]
        MONITOR["Transaction Monitoring"]
        INVESTIGATE["Alert Investigation"]
    end

    subgraph BACKEND["Application Layer"]
        API["Node.js + Express"]
        AUTH["JWT Authentication"]
        RBAC["Role-Based Access Control"]
        VALIDATE["Input Validation"]
    end

    subgraph ML["Machine Learning Layer"]
        FLASK["Python Flask Service"]
        XGB["XGBoost Classifier"]
        ISO["Isolation Forest"]
        SCORE["Fraud Scoring"]
    end

    DB[("PostgreSQL Database")]

    USER --> UI
    UI --> METRICS
    UI --> MONITOR
    UI --> INVESTIGATE

    UI --> API
    API --> AUTH
    AUTH --> RBAC
    RBAC --> VALIDATE

    VALIDATE --> DB
    VALIDATE --> FLASK

    FLASK --> XGB
    FLASK --> ISO
    XGB --> SCORE
    ISO --> SCORE

    SCORE --> API
    API --> UI

    classDef user fill:#172554,stroke:#60A5FA,color:#EFF6FF
    classDef frontend fill:#164E63,stroke:#22D3EE,color:#ECFEFF
    classDef backend fill:#1E3A8A,stroke:#60A5FA,color:#EFF6FF
    classDef ml fill:#312E81,stroke:#A78BFA,color:#F5F3FF
    classDef database fill:#064E3B,stroke:#34D399,color:#ECFDF5

    class USER user
    class UI,METRICS,MONITOR,INVESTIGATE frontend
    class API,AUTH,RBAC,VALIDATE backend
    class FLASK,XGB,ISO,SCORE ml
    class DB database
```

### Component responsibilities

| Component | Responsibility |
|---|---|
| React frontend | Dashboard, transaction monitoring, and investigation workflows |
| Express backend | Application APIs and request orchestration |
| Authentication layer | JWT-based authentication |
| Authorization layer | Role-based access control |
| Flask service | Machine learning inference |
| XGBoost | Supervised fraud classification |
| Isolation Forest | Unsupervised anomaly detection |
| PostgreSQL | Persistent relational data storage |

---

## `~/detection_engine` — Machine Learning Pipeline

The detection engine combines two complementary approaches to identify potentially fraudulent financial activity.

### 01. XGBoost — Supervised Learning

XGBoost is used to learn patterns from labeled transaction data and classify transactions based on learned relationships between transaction features and fraud labels.

Its role in the system is to provide a supervised prediction based on patterns observed during model training.

### 02. Isolation Forest — Anomaly Detection

Not every unusual transaction necessarily matches a previously observed fraud pattern.

Isolation Forest provides an additional anomaly-detection approach by identifying observations that differ from the broader transaction distribution.

This complements supervised classification by introducing an unsupervised perspective.

### Detection workflow

```mermaid
flowchart TD
    A["Incoming Transaction"] --> B["Input Validation"]
    B --> C["Transaction Preprocessing"]
    C --> D["Feature Preparation"]

    D --> E["XGBoost Classifier"]
    D --> F["Isolation Forest"]

    E --> G["Supervised Prediction"]
    F --> H["Anomaly Detection"]

    G --> I["Detection Result"]
    H --> I

    I --> J["Backend Processing"]
    J --> K["Persist / Retrieve Transaction Data"]
    K --> L["Dashboard Visualization"]

    classDef input fill:#172554,stroke:#60A5FA,color:#EFF6FF
    classDef process fill:#164E63,stroke:#22D3EE,color:#ECFEFF
    classDef model fill:#312E81,stroke:#A78BFA,color:#F5F3FF
    classDef output fill:#14532D,stroke:#4ADE80,color:#F0FDF4

    class A,B input
    class C,D,J,K process
    class E,F,G,H model
    class I,L output
```

> **Important:** The two models represent complementary detection techniques. Their exact score-fusion strategy, thresholds, feature transformations, and decision rules should be documented from the implemented inference code rather than assumed.

---

## `~/features` — Application Capabilities

### 01 / Transaction Processing
- Processes a dataset containing 20,000+ synthetic financial transactions.
- Supports an end-to-end transaction analysis workflow.
- Connects transaction data with the machine learning detection pipeline.

### 02 / Machine Learning Detection
- XGBoost-based supervised classification.
- Isolation Forest-based anomaly detection.
- Python Flask service for model integration.
- Fraud scoring and alert generation.

### 03 / Secure Backend APIs
- 10+ RESTful APIs.
- JWT-based authentication.
- bcrypt password hashing.
- Role-based access control.
- Input validation for application requests.

### 04 / Analytics Dashboard
- React-based analytics interface.
- Transaction monitoring.
- Fraud-related metrics and visualizations.
- Alert investigation workflows.

### 05 / Relational Data Management
- PostgreSQL integration.
- Structured storage for application data.
- Backend database communication.

---

## `~/request_lifecycle` — Transaction Analysis Sequence

```mermaid
sequenceDiagram
    autonumber
    actor Analyst
    participant UI as React Dashboard
    participant API as Express Backend
    participant DB as PostgreSQL
    participant ML as Flask ML Service
    participant XGB as XGBoost
    participant IF as Isolation Forest

    Analyst->>UI: Submit transaction for analysis
    UI->>API: Send authenticated request
    API->>API: Validate request and permissions
    API->>ML: Forward transaction features

    ML->>XGB: Supervised prediction
    XGB-->>ML: Classification output

    ML->>IF: Anomaly evaluation
    IF-->>ML: Anomaly output

    ML-->>API: Return detection results
    API->>DB: Persist relevant application data
    DB-->>API: Database response

    API-->>UI: Return analysis response
    UI-->>Analyst: Display result and dashboard updates
```

*This sequence illustrates the documented component responsibilities. Exact request payloads, response fields, and persistence behavior depend on the implementation.*

---

## `~/security` — Application Security

Security is particularly important when building systems that process financial transaction information.

| Mechanism | Purpose |
|---|---|
| JWT | Authenticated application access |
| bcrypt | Password hashing |
| RBAC | Role-based authorization |
| Input validation | Validate incoming application data |
| REST API separation | Separate frontend and backend responsibilities |

### Security considerations

- Keep authentication secrets outside source control.
- Never expose database credentials or private keys in frontend code.
- Validate authorization on the backend, not only in the UI.
- Validate transaction inputs before passing them to the ML service.
- Avoid logging passwords, tokens, or sensitive financial information.
- Use HTTPS for deployed application communication.

---

## `~/technology` — Technology Stack

| Domain | Technologies |
|---|---|
| Frontend | React.js |
| Backend | Node.js, Express.js |
| ML Service | Python, Flask |
| Supervised ML | XGBoost |
| Anomaly Detection | Isolation Forest |
| Database | PostgreSQL |
| Authentication | JWT |
| Password Security | bcrypt |
| API Architecture | REST |

---

## `~/engineering_decisions` — Design Rationale

| Decision | Engineering reasoning |
|---|---|
| React dashboard | Provides an interactive interface for monitoring and investigation |
| Express backend | Centralizes application APIs and request handling |
| Separate Flask service | Keeps Python ML inference independent from the Node.js application |
| XGBoost | Supports supervised classification of transaction patterns |
| Isolation Forest | Adds an unsupervised anomaly-detection approach |
| PostgreSQL | Provides relational persistence |
| JWT + RBAC | Supports authenticated and role-controlled access |

---

## `~/setup` — Local Development

The repository's exact directory structure, dependency files, environment variable names, and startup scripts need to be matched to the source code before these commands can be treated as a verified installation guide.

### Prerequisites

- Node.js and npm
- Python 3.x
- PostgreSQL
- Git

### 1. Clone the repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_REPOSITORY_DIRECTORY>
```

### 2. Backend setup

Navigate to the actual Node.js backend directory:

```bash
cd <BACKEND_DIRECTORY>
npm install
```

Configure the backend environment using the variable names expected by the application.

Example configuration categories:

```env
PORT=<BACKEND_PORT>
DATABASE_URL=<POSTGRESQL_CONNECTION_STRING>
JWT_SECRET=<YOUR_SECRET>
```

Start the backend using the script defined in its `package.json`.

```bash
npm start
```

### 3. Machine learning service setup

Navigate to the Flask service directory:

```bash
cd <ML_SERVICE_DIRECTORY>
```

Create and activate a virtual environment:

```bash
python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

Install the project's Python dependencies:

```bash
pip install -r requirements.txt
```

Start the Flask application using its actual entry-point file.

```bash
python <FLASK_ENTRY_FILE>.py
```

### 4. Frontend setup

Open another terminal and navigate to the React application:

```bash
cd <FRONTEND_DIRECTORY>
npm install
npm run dev
```

Open the local URL printed by the frontend development server.

> Replace the directory names, environment variables, and startup commands above with the actual values from the repository before publishing this README.

---

## `~/roadmap` — Future Engineering Improvements

The following are potential enhancements, not claims about existing functionality.

- [ ] Add automated backend and ML API tests.
- [ ] Document model evaluation with precision, recall, F1-score, and ROC-AUC.
- [ ] Add model versioning and reproducible training configurations.
- [ ] Improve explainability of individual fraud predictions.
- [ ] Add transaction-level audit history.
- [ ] Introduce monitoring for model performance and data drift.
- [ ] Add structured API documentation.
- [ ] Improve deployment configuration and operational observability.

---

## `~/engineering_notes` — Important ML Considerations

Fraud detection is an imbalanced classification problem. Accuracy alone can hide poor fraud detection performance.

A stronger evaluation should report:

| Metric | What it measures |
|---|---|
| Precision | How many transactions flagged as fraud were actually fraudulent |
| Recall | How many actual fraudulent transactions were detected |
| F1-score | Balance between precision and recall |
| ROC-AUC | Ranking ability across classification thresholds |
| Confusion Matrix | True positives, false positives, true negatives, and false negatives |

The cost of a false negative may be significantly different from the cost of a false positive. Threshold selection should therefore reflect the intended investigation workflow.

**Dataset note:** The 20,000+ transaction figure refers to synthetic data as documented for this project. It should not be interpreted as real banking transaction volume or evidence of production financial deployment.

---

## `~/author` — Project Information

**Project:** Fraud Detection System – AI-Powered Financial Fraud Detection Platform  
**Category:** Full-Stack Development · Machine Learning · FinTech  
**Developer:** Sarthak Tanpure  
**Institution:** Pravara Rural Engineering College

<p align="center">
  <b>Building systems that turn data into meaningful decisions.</b>
</p>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F172A,50:164E63,100:0891B2&height=120&section=footer" width="100%" />
</p>