# 🚔 Vehicle Theft Data Engineering Project — Databricks Medallion Architecture

## 🚀 Overview
This beginner-friendly end-to-end project demonstrates how to design and implement an **end-to-end ETL pipeline** on **Azure Databricks**, following the **Medallion Architecture** (Bronze → Silver → Gold) to transform raw vehicle theft records into **business-ready analytical data**.

The solution automates **data ingestion, transformation, and enrichment** using **PySpark**, **Delta Lake**, and **Unity Catalog** to deliver high-quality, governed data for downstream analysis — enabling insights into theft patterns, hotspot areas, recovery timelines, and risk trends.

---

## 🧩 Architecture Overview
![Vehicle Theft Databricks Architecture](assets/Vehicle%20Theft%20Daigram.png)

The above architecture visualizes the **data flow and governance setup**:
- **Azure Data Factory (ADF)** handles data ingestion from multiple CSV sources into the **Landing Layer**.
- **Databricks with Unity Catalog** manages schema evolution and processing across **Bronze**, **Silver**, and **Gold** layers.
- **Power BI / Tableau** consumes the curated Gold data for visualization.

---

## ⚙️ Project Workflow

### 1️⃣ Data Ingestion (Bronze Layer)
- Ingested raw data from CSV sources — `locations.csv`, `make_details.csv`, and `stolen_vehicles.csv` — using **ADF Copy Data** activity.  
- Each dataset was stored as **Parquet files** in ADLS Gen2 under the **Bronze container**.

### 2️⃣ Data Transformation and Cleaning (Silver Layer)
- Cleaned and standardized vehicle data using **PySpark**:
  - Removed duplicates and nulls.  
  - Standardized string casing and timestamp formats.  
  - Joined location and make details with the main stolen vehicle dataset.
- Stored the transformed datasets in **Silver Delta tables** for validation and incremental loads.

### 3️⃣ Business-Ready Data (Gold Layer)
- Created aggregated datasets to support **analytics and KPI dashboards**
- Generated **Gold Delta tables** for downstream BI tools.

---

## 🧰 Tech Stack

| Category | Tools & Technologies |
|-----------|----------------------|
| Data Lake | Azure Data Lake Storage (ADLS Gen2) |
| Orchestration | Azure Data Factory |
| Processing | Azure Databricks (PySpark, Delta Lake) |
| Governance | Unity Catalog |
| Language | Python (PySpark) |
| Visualization | Power BI / Tableau |

---

## 📒 Notebooks

| Layer | Notebook | Description |
|--------|-----------|-------------|
| 🟤 Bronze | [01. Data Ingestion](notebooks/01.%20Data%20Ingestion.html) | Loads CSV data from ADF Landing Layer into Bronze Delta tables |
| ⚪ Silver | [02. Data Transformation and Cleaning](notebooks/02.%20Data%20Transformation%20and%20Cleaning.html) | Cleans, validates, and enriches vehicle theft datasets |
| 🟡 Gold | [03. Business Ready Data](notebooks/03.%20Business%20Ready%20Data.html) | Aggregates and prepares data for BI dashboards |

---

## 💾 Data Folder

📁 **`/data`**

| File Name | Description |
|------------|-------------|
| `locations.csv` | Contains geospatial and administrative location mappings |
| `make_details.csv` | Vehicle make and model information |
| `stolen_vehicles.csv` | Theft records including theft date, recovery date, and location |

All datasets are ingested by ADF into **ADLS Landing Layer**, then processed through **Databricks**.

---

## 📊 ADF Pipeline Visualization
![ADF Copy Activity](assets/Screenshot%202025-11-11%20195225.png)

The **ADF Copy Data activities** orchestrate ingestion from multiple sources to the Bronze container in ADLS, forming the foundation for the Databricks ETL process.

---

## 💡 Key Learnings
- Built an **end-to-end Lakehouse ETL pipeline** using Databricks.  
- Implemented **Medallion Architecture** (Bronze → Silver → Gold) with Delta Lake.  
- Enforced **data governance and lineage** through Unity Catalog.  
- Automated ingestion pipelines using **ADF**.  
- Derived insights on **vehicle theft hotspots and recovery analytics** using BI tools.

---

## 🧭 Outcome
✅ Automated data pipeline from raw CSVs to business-ready analytics  
✅ Unified and governed data model for reliable insights  
✅ BI-ready tables optimized for Power BI & Tableau  
✅ Scalable architecture for future datasets and schema changes  

---

## 🪜 Folder Description

| Folder | Description |
|---------|-------------|
| `data/` | Raw input files (`locations.csv`, `make_details.csv`, `stolen_vehicles.csv`) |
| `notebooks/` | Databricks notebooks for each Medallion layer |
| `assets/` | Architecture and pipeline visuals |
| `README.md` | Complete project documentation |

---

## 👨‍💻 Author
**Rishikesh Gundla**  
_Senior Business Intelligence Engineer | Data Engineering & Analytics Enthusiast_  
🔗 [LinkedIn](https://www.linkedin.com/in/rishikeshgundla)
