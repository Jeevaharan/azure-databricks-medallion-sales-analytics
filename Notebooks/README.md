# Databricks Notebooks – Medallion Architecture

This folder contains **Azure Databricks notebooks** that implement the Medallion Architecture layers for the project. Each notebook represents a distinct stage in the data pipeline and is designed to be **idempotent, modular, and easy to orchestrate**.

## Notebook Layers

### Bronze Layer
- Reads raw CSV data from Azure Data Lake Storage (ADLS Gen2)
- Performs minimal transformations
- Adds ingestion metadata such as:
  - ingestion timestamp
  - source file name
- Writes data as Delta tables

Purpose: **Raw ingestion and traceability**


### Silver Layer
- Reads data from Bronze Delta tables
- Cleans and standardizes columns
- Casts data types
- Removes duplicates
- Generates deterministic business keys
- Uses **Delta Lake MERGE** for incremental and idempotent updates

Purpose: **Clean, reliable, analytics-ready data**


### Gold Layer
- Reads from Silver tables
- Applies business logic and aggregations
- Produces analytics-ready datasets
- Prepares data for BI consumption

Purpose: **Business-facing, query-optimized datasets**


## Execution Flow
The notebooks are intended to be executed in the following order:

1. Bronze ingestion
2. Silver transformation
3. Gold modeling and aggregation

These notebooks are orchestrated using **Azure Data Factory**.


