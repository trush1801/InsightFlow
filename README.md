# InsightFlow
Data Observability &amp; Analytics Platform with Bronze-Silver-Gold Pipeline
# 🚀 Data Observability Warehouse Platform

> An end-to-end data engineering platform implementing Bronze, Silver, and Gold layers with built-in quality monitoring, profiling, lineage tracking, and machine learning capabilities.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Node.js](https://img.shields.io/badge/Node.js-18%2B-green)
![React](https://img.shields.io/badge/React-18-61DAFB)
![Python](https://img.shields.io/badge/Python-3.10%2B-yellow)
![Status](https://img.shields.io/badge/status-Active-brightgreen)

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [System Architecture](#-system-architecture)
- [Features](#-features)
- [Data Flow](#-data-flow)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [API Reference](#-api-reference)
- [Suggested Improvements](#-suggested-project-improvements)
- [Future Enhancements](#-future-enhancements)
- [Author](#-author)

---

## 🧠 Overview

The **Data Observability Warehouse Platform** is a full-stack data engineering solution that processes raw datasets through a structured **Bronze → Silver → Gold** pipeline. It goes beyond simple data transformation by providing real-time quality monitoring, automated profiling, complete data lineage tracking, and ML-powered anomaly detection — making it production-grade and portfolio-worthy.

---

## ❗ Problem Statement

In real-world systems, incoming data is often unreliable:

| Issue | Impact |
|---|---|
| ❌ Missing values | Incomplete analytics, skewed aggregations |
| ❌ Duplicate records | Inflated counts, incorrect KPIs |
| ❌ Invalid / inconsistent data | Wrong business decisions |
| ❌ No visibility into data flow | Difficult debugging and auditing |

This platform solves all of the above through an automated, observable pipeline.

---

## 🏗️ System Architecture

```
┌──────────────────────────────────────────────────────────┐
│                     USER INTERFACE                        │
│              (React Dashboard + File Upload)              │
└────────────────────────┬─────────────────────────────────┘
                         │
                         ▼
┌──────────────────────────────────────────────────────────┐
│                   REST API LAYER                          │
│                 (Node.js / Express)                       │
└────┬──────────────┬──────────────┬────────────────┬──────┘
     │              │              │                │
     ▼              ▼              ▼                ▼
┌─────────┐  ┌──────────┐  ┌──────────┐   ┌──────────────┐
│ BRONZE  │→ │  SILVER  │→ │   GOLD   │   │  ML ENGINE   │
│  LAYER  │  │  LAYER   │  │  LAYER   │   │  (Python)    │
│Raw Store│  │ Cleaning │  │Analytics │   │Anomaly/Pred. │
└─────────┘  └──────────┘  └──────────┘   └──────────────┘
     │              │              │                │
     └──────────────┴──────────────┴────────────────┘
                         │
                         ▼
┌──────────────────────────────────────────────────────────┐
│              DATABASE LAYER (MySQL / MongoDB)             │
│     Bronze Tables | Silver Tables | Gold Tables           │
│     Quality Metrics | Lineage Logs | ML Results           │
└──────────────────────────────────────────────────────────┘
```

---

## 🔥 Features

### 📥 1. Data Ingestion
- Upload **any CSV dataset** through the UI
- Supports **dynamic schema** — no fixed column structure required
- Automatic type inference for each column
- Stores raw data without modification to preserve original integrity

---

### 🥉 2. Bronze Layer — Raw Data Storage
- Stores uploaded data **exactly as received**
- Attaches metadata to every record:
  - `ingested_at` — timestamp of upload
  - `source_file` — original filename
  - `batch_id` — unique ingestion batch identifier
- Acts as the **immutable source of truth** for the pipeline

---

### 🥈 3. Silver Layer — Data Cleaning & Validation

**Cleaning Operations:**
- Remove exact duplicate rows
- Handle missing/null values (drop, fill mean, fill mode — configurable)
- Correct invalid entries (e.g., negative ages, future birthdates)
- Standardize string formats (trim whitespace, normalize casing)
- Parse and validate date columns

**Quality Checks Generated:**

| Metric | Description |
|---|---|
| Completeness | Percentage of non-null values per column |
| Uniqueness | Duplicate record count and ratio |
| Validity | Rows failing domain/type constraints |
| Consistency | Cross-column rule violations |

---

### 🥇 4. Gold Layer — Analytics & Transformation
- Transforms cleaned data into **analytics-ready format**
- Generates aggregations, summaries, and KPIs automatically
- Supports optional **Star Schema** structure for reporting
- Output is ready for BI tools and visualization

---

### 🔍 5. Data Quality Monitoring
- Tracks quality metrics across every pipeline run
- Stores historical quality scores for trend analysis
- Raises alerts for quality degradation
- Visualized in the dashboard as metric cards and trend charts

---

### 📊 6. Data Profiling *(Key Feature)*

Automatically generates a full statistical profile of any uploaded dataset:

| Statistic | Columns Covered |
|---|---|
| Mean / Median / Mode | Numeric columns |
| Min / Max / Range | Numeric columns |
| Unique value count | All columns |
| Null percentage | All columns |
| Data type distribution | All columns |
| Top N most frequent values | Categorical columns |

---

### 🔗 7. Data Lineage *(Key Feature)*

Tracks the complete journey of every record through the system:

```
CSV Upload → Bronze (Raw) → Silver (Cleaned) → Gold (Transformed) → Dashboard
     ↓              ↓               ↓                  ↓
  Timestamp     Metadata       Quality Score       Aggregation Log
```

- Every transformation step is logged with timestamp and description
- View full lineage of any dataset from a single UI panel
- Helps with debugging, auditing, and compliance

---

### 🤖 8. Machine Learning Integration

**Anomaly Detection**
- Uses Isolation Forest (scikit-learn) to flag statistical outliers
- Example: A sales value of `10,00,000` when the average is `50,000` gets flagged
- Anomaly scores stored and surfaced in the dashboard

**Predictive Analytics** *(Optional)*
- Forecasts future trends for numeric time-series columns
- Model: Linear Regression / Prophet (configurable)

---

### 📊 9. Interactive Dashboard
- Real-time data quality metrics (completeness, uniqueness, validity)
- Column-level profiling statistics
- Anomaly alerts panel
- Data lineage graph view
- Trend charts for quality over time
- Layer-wise row count comparison (Bronze vs Silver vs Gold)

---

## 🔄 Data Flow

```
1. User uploads CSV via UI
        ↓
2. Bronze Layer — stores raw data + adds metadata
        ↓
3. Silver Layer — cleans, validates, generates quality report
        ↓
4. Gold Layer — transforms into analytics-ready tables
        ↓
5. ML Engine — runs anomaly detection and predictions
        ↓
6. Dashboard — displays all results, metrics, and lineage
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 18, Chart.js, Tailwind CSS |
| **Backend** | Node.js, Express.js |
| **Database** | MySQL (structured layers) + MongoDB (metadata/lineage logs) |
| **ML Engine** | Python 3.10+, scikit-learn, pandas, NumPy |
| **Visualization** | Chart.js, Recharts |
| **Communication** | REST API (Express ↔ React), Python Flask microservice |

---

## 📁 Project Structure

```
data-observability-platform/
│
├── frontend/                        # React Application
│   ├── src/
│   │   ├── components/
│   │   │   ├── Dashboard.jsx
│   │   │   ├── FileUpload.jsx
│   │   │   ├── QualityMetrics.jsx
│   │   │   ├── DataLineage.jsx
│   │   │   ├── ProfilingStats.jsx
│   │   │   └── AnomalyAlerts.jsx
│   │   └── App.jsx
│   └── package.json
│
├── backend/                         # Node.js + Express API
│   ├── routes/
│   │   ├── ingest.js
│   │   ├── bronze.js
│   │   ├── silver.js
│   │   ├── gold.js
│   │   ├── lineage.js
│   │   └── quality.js
│   └── server.js
│
├── ml/                              # Python ML Engine
│   ├── app.py                      # Flask microservice entry point
│   ├── anomaly_detection.py
│   ├── prediction.py
│   ├── profiling.py
│   └── requirements.txt
│
├── database/
│   ├── schema.sql
│   └── migrations/
│
├── sample_data/                    # Sample CSVs for demo
│   ├── sales_data.csv
│   └── hr_data.csv
│
├── .env.example
├── docker-compose.yml
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- Python 3.10+
- MySQL 8+
- MongoDB 6+

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/data-observability-platform.git
cd data-observability-platform
```

### 2. Backend Setup

```bash
cd backend
npm install
cp .env.example .env
# Fill in your DB credentials in .env
node server.js
```

### 3. Frontend Setup

```bash
cd frontend
npm install
npm start
```

### 4. ML Engine Setup

```bash
cd ml
pip install -r requirements.txt
python app.py   # Flask ML microservice on port 8000
```

### 5. Database Setup

```bash
mysql -u root -p < database/schema.sql
```

### Environment Variables

```env
PORT=5000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=data_observability
MONGO_URI=mongodb://localhost:27017/lineage_db
ML_SERVICE_URL=http://localhost:8000
```

---

## 📡 API Reference

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/ingest` | Upload CSV file |
| `GET` | `/api/bronze/:batchId` | Get raw Bronze data |
| `GET` | `/api/silver/:batchId` | Get cleaned Silver data |
| `GET` | `/api/gold/:batchId` | Get Gold analytics |
| `GET` | `/api/quality/:batchId` | Get quality metrics |
| `GET` | `/api/lineage/:batchId` | Get full data lineage |
| `GET` | `/api/profile/:batchId` | Get profiling statistics |
| `GET` | `/api/anomalies/:batchId` | Get anomaly detection results |

---

## ⚠️ Suggested Project Improvements

These additions will significantly strengthen the project for your portfolio and interviews:

1. **Docker support** — A `docker-compose.yml` to spin up MySQL, MongoDB, Node.js, and Python together makes setup reproducible and shows DevOps awareness.

2. **ML as Flask microservice** — Instead of calling Python scripts as subprocesses from Node.js, expose the ML engine as a proper REST API on its own port. This is the industry-standard pattern.

3. **JWT authentication** — Even a simple login/register flow makes the project more realistic and demonstrates security thinking.

4. **Sample datasets** — Include 2–3 CSVs in a `sample_data/` folder so anyone cloning the repo can demo it immediately.

5. **Unit tests** — Basic tests for Silver layer cleaning (`jest` for Node.js, `pytest` for Python) are something every interviewer appreciates seeing.

6. **`.env.example` file** — Never commit real credentials. This small detail shows professional habits.

---

## 🔮 Future Enhancements

- [ ] Real-time data streaming (Apache Kafka integration)
- [ ] Advanced ML models (Prophet for time-series, XGBoost)
- [ ] Rule-based validation engine (custom user-defined rules)
- [ ] Email / Slack notifications for quality alerts
- [ ] Role-based access control (RBAC)
- [ ] Export reports as PDF
- [ ] Support for JSON, Parquet, and Excel file formats

---

## 👨‍💻 Author

**Your Name**
- GitHub: [@your-username](https://github.com/your-username)
- LinkedIn: [your-linkedin](https://linkedin.com/in/your-profile)
- Email: your.email@example.com

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## ⭐ Key Highlights

| Domain | Skills Demonstrated |
|---|---|
| **Data Engineering** | Bronze/Silver/Gold pipeline, ETL, dynamic schema |
| **Data Warehousing** | Layered architecture, star schema, aggregations |
| **Data Observability** | Quality monitoring, profiling, lineage tracking |
| **Machine Learning** | Anomaly detection, predictive analytics |
| **Full-Stack Development** | React, Node.js, REST API, dual-database design |

> 💼 **Resume line:** *Developed a Data Observability Warehouse platform implementing Bronze, Silver, and Gold layers with dynamic schema support, integrated data quality checks, profiling, lineage tracking, and machine learning models for anomaly detection and predictive analytics using React, Node.js, Python, and MySQL.*
