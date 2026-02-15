🌍 Earthquake Data Pipeline — Azure Databricks Learning Project

This project is a personal learning exercise where I built a small end-to-end cloud data pipeline to understand how modern data engineering workflows are implemented in Azure.

The pipeline ingests public earthquake data from the USGS API, processes it using a Medallion Architecture, and stores curated datasets in a data lake for querying.

The goal of the project was not scale or production deployment, but to learn how different Azure data services work together in a realistic workflow.

Built using Azure Databricks, Azure Data Factory, and Azure Data Lake Storage.


<img width="1170" height="439" alt="image" src="https://github.com/user-attachments/assets/a048b0ee-7207-4661-bdf8-bb969ba2deeb" />

<img width="1078" height="200" alt="image" src="https://github.com/user-attachments/assets/b637d495-a444-4e86-917c-cbe983d667f2" />


🎯 What I Wanted to Learn

How a medallion architecture works in practice

How Databricks notebooks communicate in a workflow

How Azure manages permissions using managed identity & RBAC

How to orchestrate jobs using Data Factory

How raw API data becomes analytics-ready tables

🏗 High Level Architecture
USGS Earthquake API
        ↓
Azure Data Factory (trigger & orchestration)
        ↓
Databricks Notebooks (Bronze → Silver → Gold)
        ↓
Azure Data Lake Storage Gen2


The pipeline runs notebooks sequentially and passes parameters between them.

🧱 Data Layers
Bronze — Raw Data

Calls the earthquake REST API

Saves raw JSON exactly as received

Keeps historical records

Example:

/bronze/2026-02-14_earthquake_data.json

Silver — Cleaned Data

Transforms raw JSON into structured format:

Flatten nested structure

Convert timestamps

Handle missing values

Select relevant columns

Stored as Parquet files.

Gold — Enriched Data

Adds analytical value:

Reverse geocoding → country code

Earthquake significance classification (Low / Moderate / High)

This layer represents a dataset analysts could use directly.

🔄 Pipeline Flow
Step	Notebook	Purpose
1	Bronze	Ingest API data
2	Silver	Clean & structure
3	Gold	Enrich & classify

Notebooks communicate using:

dbutils.jobs.taskValues

🛠 Technologies Used

PySpark

REST API ingestion

Databricks workflows

ADLS Gen2 external locations

Managed identity authentication

Basic data enrichment with Python UDF
