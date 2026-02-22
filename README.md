# 🌍 Earthquake Data Pipeline — Azure Databricks Learning Project

This is a personal learning project created to understand how modern cloud data platforms work together using **Microsoft Azure** and **Databricks**.

I built a small end-to-end data pipeline that:

- Ingests public earthquake data from the USGS API
- Processes it through layered transformations
- Stores it in a cloud data lake

The project focuses on learning hands-on workflows — authentication, orchestration, storage structure, and Spark processing — rather than building a production-scale system.

Built primarily using **Azure Databricks** and **Microsoft Azure** services.

---

## 📸 Project Screenshots

<img width="998" height="548" alt="image" src="https://github.com/user-attachments/assets/5ff20d0a-df89-47c9-82d7-4a857d650c7c" />

![Screenshot 1](https://github.com/user-attachments/assets/7f5e2132-59b7-4599-8ee6-fb48954565cd)

![Screenshot 2](https://github.com/user-attachments/assets/a048b0ee-7207-4661-bdf8-bb969ba2deeb)

![Screenshot 3](https://github.com/user-attachments/assets/817631fb-7eef-4cac-8a9a-2d7b4ec3c320)

---

## 🎯 Learning Focus

### Databricks
- Notebook workflows
- Task orchestration
- Parameter passing between tasks
- Spark data processing with PySpark
- Reading and writing distributed files
- Working with external locations and Unity Catalog

### Azure
- Role-based access control (RBAC)
- Managed identity authentication
- Data Lake storage structure
- Service integration between Azure components
- Pipeline orchestration concepts

---

## 🏗 Architecture

```text
Public REST API
       ↓
Azure Data Factory (pipeline trigger)
       ↓
Databricks Notebooks (processing)
       ↓
Azure Data Lake Storage Gen2
```
The pipeline executes notebooks sequentially and shares outputs between them.



## 🧱 Data Layers (Medallion Architecture)

### 🥉 Bronze — Raw
- Fetches earthquake data and stores the original JSON response
- Preserves historical records

### 🥈 Silver — Cleaned
- Normalizes the structure
- Converts timestamps into usable columns
- Handles missing values
- Stored as Parquet files for analytics

### 🥇 Gold — Enriched
- Adds country code (reverse geocoding)
- Adds earthquake significance classification (Low / Moderate / High)
- Analytical dataset ready for querying

---

## 🔄 Pipeline Flow

| Step   | Purpose                  |
|--------|--------------------------|
| Bronze | API ingestion            |
| Silver | Cleaning & structuring   |
| Gold   | Enrichment               |

> Communication between steps is handled using **Databricks workflow task values**.

---

## 🛠 Technologies Used

- PySpark  
- REST APIs  
- Cloud object storage  
- Distributed processing  
- Notebook orchestration
