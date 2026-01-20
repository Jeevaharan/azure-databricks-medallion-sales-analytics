# Azure Data Factory Orchestration

## Pipeline Overview

The image below illustrates the Azure Data Factory pipeline used to orchestrate the Databricks notebooks:

![ADF Pipeline](ADF%20orchestration/Azure%20Data%20Factory%20workflow.png)

The pipeline is **scheduled to run daily on a regular basis**, enabling automated and repeatable data processing.



## Orchestration Logic

The pipeline follows this control flow:

1. **Get Metadata**
   - Checks for the presence of files in Azure Data Lake Storage
2. **If Condition**
   - Proceeds only if files are available
3. **Databricks Notebook Activities**
   - Executes Bronze, Silver, and Gold notebooks sequentially



