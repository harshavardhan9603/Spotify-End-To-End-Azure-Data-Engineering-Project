# Spotify End-To-End Azure Data Engineering Project

## 📌 Project Overview
This project demonstrates a production-grade data engineering pipeline built on **Microsoft Azure**. It implements a **Medallion Architecture** to process Spotify data, moving it from raw ingestion to a structured star schema for analytical purposes. The project focuses on modern data practices like Incremental loading, Backfilling, Slowly Changing Dimensions(SCD) and Automated Deployments (CI/CD).

## 🏗️ Architecture & Data Flow
The data pipeline follows these stages:
1. **Data Ingestion:** Extracting data using **Azure Data Factory (ADF)** from source systems (Azure SQL / On-prem) into **Azure Data Lake Storage (ADLS) Gen2**.
2. **Processing (Medallion Architecture):**
    * **Bronze:** Raw data landing zone.
    * **Silver:** Data cleaning, transformation, and deduplication using **Azure Databricks** and **Delta Lake**.
    * **Gold:** Final business-level tables organized in a **Star Schema** (Fact and Dimension tables) for BI reporting.
3. **Governance:** Managed via **Unity Catalog** for fine-grained access control and data lineage.
4. **Automation:** Orchestration via ADF and automated notifications using **Logic Apps**.
5. **DevOps:** Deployment using **Databricks Asset Bundles (DABs)** and **CI/CD** pipelines for Dev and Prod environments.

![Architecture](https://github.com/user-attachments/assets/39228e9b-70d9-4f08-8a9b-fe2eede7c66f)
![Adf](https://github.com/user-attachments/assets/064a345c-ac36-483e-a102-0130008ddb10)
![DLT](https://github.com/user-attachments/assets/08f5f87d-a1af-4369-8c71-e0b78763791e)


## 🛠️ Tech Stack
* **Cloud Provider:** Microsoft Azure
* **Orchestration:** Azure Data Factory (ADF)
* **Compute:** Azure Databricks (PySpark / Delta Lake)
* **Storage:** Azure Data Lake Storage Gen2 (ADLS)
* **Database:** Azure SQL Database
* **Governance:** Unity Catalog
* **DevOps:** Databricks Asset Bundles (DABs), GitHub Actions (CI/CD)
* **Monitoring:** Logic Apps (Alerting)

## 🚀 Key Features
* **Incremental Data Loading:** Optimized processing that only handles new or changed data.
* **Backfilling Mechanism:** Ability to re-process or fill in historical data for specific time intervals.
* **Star Schema Modeling:** Implementation of **SCD (Slowly Changing Dimensions)** to track historical changes in data.
* **Auto-Loader:** Efficiently ingests files from cloud storage as they arrive using Databricks Auto-loader.
* **Environment Isolation:** Complete separation of Dev and Prod environments using Azure Subscriptions and Resource Groups.

## 📂 Project Structure
```text
├── .bundle/spotify_dab/dev/  # Asset bundles for CI/CD deployment
├── spotify_dab/                # PySpark notebooks for Bronze, Silver, Gold layers
├── pipeline/                 # JSON definitions for ADF pipelines
├── spotify_dab/              # Star schema and SCD implementation scripts
└── README.md
