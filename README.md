# End-to-End Data Engineering Project (Databricks + PySpark + dbt)

## Project Overview

This project demonstrates a complete **end-to-end data engineering pipeline** using modern tools such as **Databricks, PySpark, and dbt Cloud**.

The goal is to simulate a real-world data pipeline by ingesting raw data, transforming it through multiple layers, and applying data modeling techniques like **Slowly Changing Dimensions (SCD)**.

---

## Architecture

<!-- 📷 Add your architecture image here -->
<img width="750" height="440" alt="Untitled Diagram drawio (10)" src="https://github.com/user-attachments/assets/b4e5b8d0-44ee-430e-9839-52aeb5acabe8" />


The pipeline follows a **Medallion Architecture** approach:

- **Bronze Layer** → Raw data ingestion  
- **Silver Layer** → Cleaned and transformed data  
- **Gold Layer** → Final analytics-ready data  

---

## Dataset

The project is based on **6 CSV files**:

- 1 Fact Table:
  - `trips`

- 5 Dimension Tables:
  - `vehicles`
  - `drivers`
  - `customers`
  - `locations`
  - `payments`

---

## Technologies Used

- Databricks
- PySpark
- dbt Cloud
- Delta Lake
- Spark Streaming (conceptually)
- SQL

---

## Data Pipeline Steps

### Bronze Layer (Databricks)

- Ingested raw CSV data into Bronze tables
- Stored data in its original format
- No transformations applied

---

### Silver Layer (Databricks + PySpark)

Performed data cleaning and transformations using PySpark:

- Deduplication using window functions
- Column transformations:
  - Split columns
  - Concatenate columns
  - Rename columns
  - Drop unnecessary columns

Note:
- Silver layer was created for all tables **except the fact table (`trips`)**

---

### dbt Integration

- Established connection between **dbt Cloud and Databricks**
- Built transformation models using dbt

---

### Silver Layer for Fact Table (dbt)

- Created the **Silver version of the `trips` fact table** using dbt models
- Applied transformations and incremental logic

---

### Gold Layer (dbt Snapshots)

Implemented Slowly Changing Dimensions (SCD) using dbt snapshots:

- Created snapshots for all **dimension tables**
- Stored results in the **Gold layer**
- Applied historical tracking for dimension changes

Additionally:

- Created a snapshot for the **fact table (`trips`)**
- Stored it in the Gold layer as well

---


## Key Concepts Covered

- Incremental Data Ingestion
- Data Deduplication
- Data Transformation with PySpark
- Medallion Architecture (Bronze / Silver / Gold)
- dbt Models
- dbt Snapshots
- Slowly Changing Dimensions (SCD)
- Fact & Dimension Data Modeling

