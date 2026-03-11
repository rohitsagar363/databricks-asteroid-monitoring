# 🛰️ NASA Planetary Defense: Automated Data Pipeline

A production-grade Medallion Architecture pipeline on Databricks, automating daily tracking of Near-Earth Objects (NEOs) to identify potential planetary threats.

---

## Project Overview
This project implements an end-to-end data engineering lifecycle: from raw astronomical telemetry ingestion via the NASA NeoWs API to a professional Databricks SQL dashboard. It solves the challenge of handling complex, nested JSON data at scale while ensuring data reliability through incremental watermarking and Delta Lake MERGE operations.

---

## Technical Architecture

```
NASA API (Source) --> Bronze Layer (Raw JSON - Append Only) ---> Silver Layer (Flattened & Cleaned - Delta Merge) ---> Gold Layer (Aggregated Metrics - Dashboard)
```
![Architecture Diagram](./architecture.png)  
---

## Tech Stack

| Component     | Technology                             |
|-------------- |----------------------------------------|
| Platform      | Databricks Community Edition (AWS)      |
| Governance    | Unity Catalog                          |
| Storage       | Delta Lake                             |
| Processing    | PySpark, Python (`json`, `requests`)    |
| Orchestration | Databricks Workflows                    |
| Visualization | Databricks SQL Dashboards               |

---

## Key Engineering Challenges

* **Serverless RDD Limitations:** Overcame Databricks Serverless compute restrictions (RDD/SparkContext limitations) by refactoring JSON parsing to a Python-native dictionary flattening method.
* **Incremental Data Integrity:** Implemented a Watermark-based strategy to prevent duplicate API ingestion, ensuring that only new rows from Bronze are processed each day.
* **Schema Evolution:** Handled dynamic NASA API keys (dated dictionaries) by flattening them into a consistent tabular format in the Silver layer.

---

## Proof of Success

* **Workflow Success:**
  * ![Workflow Success](./workflow_success.png).

* **Dashboard Visualization:**
  * ![Dashboard View](./dashboard.png).
---