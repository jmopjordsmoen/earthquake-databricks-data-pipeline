🌍 Earthquake Data Pipeline — Azure Databricks Learning Project

This is a personal learning project created to understand how modern cloud data platforms work together using Microsoft Azure and Databricks.

I built a small end-to-end data pipeline that ingests public earthquake data from the USGS API, processes it through layered transformations, and stores it in a cloud data lake.

The purpose of the project was to gain hands-on experience with real data engineering workflows — especially authentication, orchestration, storage structure, and Spark processing — rather than to build a production-scale system.

Built primarily using Azure Databricks and Microsoft Azure services.

<img width="1437" height="515" alt="image" src="https://github.com/user-attachments/assets/7f5e2132-59b7-4599-8ee6-fb48954565cd" />

<img width="1170" height="439" alt="image" src="https://github.com/user-attachments/assets/a048b0ee-7207-4661-bdf8-bb969ba2deeb" />

<img width="1078" height="200" alt="image" src="https://github.com/user-attachments/assets/b637d495-a444-4e86-917c-cbe983d667f2" />


🎯 Learning Focus

The project was designed to learn:

Databricks

Notebook workflows

Task orchestration

Parameter passing between tasks

Spark data processing with PySpark

Reading and writing distributed files

Working with external locations and Unity Catalog

Azure

Role-based access control (RBAC)

Managed identity authentication

Data Lake storage structure

Service integration between Azure components

Pipeline orchestration concepts

🏗 Architecture
Public REST API
      ↓
Azure Data Factory (pipeline trigger)
      ↓
Databricks Notebooks (processing)
      ↓
Azure Data Lake Storage Gen2


The pipeline executes notebooks sequentially and shares outputs between them.

🧱 Data Layers (Medallion Architecture)
Bronze — Raw

Fetches earthquake data and stores the original JSON response.

Silver — Cleaned

Normalizes the structure and converts timestamps into usable columns.

Gold — Enriched

Adds country code and earthquake significance classification.

🔄 Pipeline Flow
Step	Purpose
Bronze	API ingestion
Silver	Cleaning & structuring
Gold	Enrichment

Communication between steps is handled using Databricks workflow task values.

🛠 Technologies Used

PySpark

REST APIs

Cloud object storage

Distributed processing

Notebook orchestration


