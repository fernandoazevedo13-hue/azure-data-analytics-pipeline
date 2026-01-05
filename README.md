# Azure Data Analytics Pipeline – Crypto Market Analysis

## 📌 Overview

This project demonstrates the design and implementation of an **end-to-end data analytics pipeline on Microsoft Azure**, from data ingestion via a public API to analytical consumption using Python.

The main goal is to showcase practical skills in **Data Analytics and Analytics Engineering**, including data ingestion, cloud storage, SQL-based transformations, and analytical exploration.

The dataset used contains **historical Bitcoin price data**, retrieved from a public cryptocurrency API.

---

## 🏗️ Solution Architecture

External API (Crypto Market Data)
↓
Azure Data Factory
↓
Azure Data Lake Storage Gen2 (RAW)
↓
Azure Synapse Analytics (SQL Serverless)
↓
Azure Data Lake Storage Gen2 (CURATED / Parquet)
↓
Python (pandas) – Analysis & Visualization


### Technologies Used

- **Azure Data Factory**
  - Orchestrates data ingestion from a REST API
  - Stores raw data in the Data Lake

- **Azure Data Lake Storage Gen2**
  - Central storage layer using open formats
  - Layered data organization:
    - `raw/` – original JSON data
    - `curated/` – cleaned and analytics-ready data

- **Azure Synapse Analytics (SQL Serverless)**
  - Reads data directly from the Data Lake
  - Parses complex JSON structures (array at root level)
  - Creates a curated dataset using CTAS (Create External Table As Select)
  - Stores results in Parquet format

- **Python (pandas)**
  - Consumes curated Parquet data
  - Performs analytical calculations
  - Generates visualizations and insights

---

## 📂 Repository Structure

azure-data-analytics-pipeline/
│
├── data_factory/
│ └── pipeline_ingest_crypto.json
│
├── synapse/
│ ├── explore_raw.sql
│ ├── create_curated.sql
│
├── python/
│ ├── analysis.ipynb
│ └── requirements.txt
│
├── data/
│ └── bitcoin_prices_daily.parquet
│
└── README.md


> Raw and curated datasets are not versioned in GitHub.  
> Only code, queries, and documentation are tracked.

---

## 🧠 Data Modeling Strategy

### RAW Layer
- Format: **JSON**
- Source: External REST API
- Purpose: Preserve original data with no transformations

### CURATED Layer
- Format: **Parquet**
- Columns:
  - `trade_date` (DATE)
  - `price_usd` (FLOAT)


- Purpose: Provide clean, structured, and analytics-ready data

This separation ensures data traceability and follows modern analytics architecture principles.

---

## 📊 Analytical Work in Python

The notebook (`analysis.ipynb`) includes:

- Temporal ordering of price data
- Daily return percentage calculation
- Rolling averages (7-day moving average)
- Descriptive statistics
- Price trend visualization

The focus is on **analytical reasoning and insight generation**, not just data processing.

---

## ▶️ How to Run the Project Locally

### 1. Clone the repository
```bash
git clone https://github.com/fernandoazevedo13-hue/azure-data-analytics-pipeline.git
cd azure-data-analytics-pipeline
