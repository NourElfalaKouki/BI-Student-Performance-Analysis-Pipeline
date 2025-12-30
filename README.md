# BI Student Performance Analysis Pipeline

## Project Overview
This repository contains an end-to-end **Data Warehouse** and ETL pipeline designed to process large-scale educational data. Using a **Medallion Architecture** (Bronze, Silver, Gold), the project transforms raw data into a structured Star Schema to support administrative decision-making and predictive insights.

## Architecture
The project follows the Medallion Architecture pattern to ensure data quality and lineage:

### 1. Bronze Layer (Ingestion)
* **Objective:** Raw data landing zone.
* **Process:** Documents the ingestion of 9 CSV source files (Student Info, Assessments, Courses, etc.) into **Delta Lake** tables.
* **Notebook:** `01_Bronze_load.ipynb`

### 2. Silver Layer (Transformation)
* **Objective:** Data cleaning and refinement.
* **Process:** * Handled missing values and standardized text fields (Upper/Trim).
  * Implemented data type casting and deduplication.
  * Created composite business keys (e.g., `module_key`) for relational integrity.
* **Notebook:** `02_silver_transform.ipynb`

### 3. Gold Layer (Business Ready)
* **Objective:** Final Star Schema for BI consumption.
* **Process:** Joined refined Silver tables to create localized Fact and Dimension tables.
* **Final Schema:** Includes `Fact_Performance` and `Fact_Inscription`, optimized for high-performance querying in Power BI.
* **Notebook:** `03_gold_transform.ipynb`

## Tech Stack
* **Language:** PySpark (Python)
* **Platform:** Databricks
* **Storage:** Delta Lake
* **Visualization:** Power BI
