# Walmart Lakehouse Data Engineering Pipeline

An end-to-end modern data lakehouse architecture built using **Databricks Unity Catalog**, implementing a multi-hop (Medallion) data pipeline to ingest, transform, and aggregate retail dataset layers.

---

## Architecture Overview

This project implements a scalable **Medallion Architecture** to process Walmart retail data entirely within the Databricks ecosystem, ensuring data quality, lineage, and high-performance querying without relying on external API dependencies.

```text
[ Raw CSV Data ] 
       │
       ▼
[ Bronze Layer ] ──> (Ingestion & Raw Capture)
       │
       ▼
[ Silver Layer ] ──> (Cleaning, Validation & Schema Enforcement)
       │
       ▼
[ Gold Layer ]   ──> (Business-Level Aggregations & Analytical Tables)
```

### Data Layers (`walmart_project_catalog`)
* **`raw`**: Ingested raw transactional source files.
* **`bronze`**: Appended delta tables capturing raw records with ingestion metadata.
* **`silver`**: Cleaned, deduplicated, and type-casted tables ready for analytical operations.
* **`gold`**: Highly optimized, aggregated dimensional and fact tables designed for business intelligence and reporting.

---

## Tech Stack & Tools

* **Data Processing**: Apache Spark, PySpark, Spark SQL
* **Storage & Governance**: Databricks Unity Catalog, Delta Lake
* **Version Control**: Git, GitHub, Databricks Git Folders

---

## Repository Structure

```text
walmart-lakehouse-project/
│
├── notebooks/
│   └── walmart-lakehouse-pipeline.py     # End-to-end multi-hop ETL pipeline notebook
└── README.md
```

## Pipeline Execution Guide

1. Clone or import this repository into your **Databricks Workspace** using Databricks Git Folders.
2. Attach the notebook to a cluster running Databricks Runtime (**DBR 13.3 LTS** or higher recommended).
3. Execute the notebook cells sequentially to:
   - Initialize the `walmart_project_catalog` schema.
   - Ingest data into the **Bronze** layer.
   - Execute transformations and cleanups for the **Silver** layer.
   - Generate analytical aggregations for the **Gold** layer.
4. Query the resulting tables directly from the Unity Catalog using Spark SQL.
