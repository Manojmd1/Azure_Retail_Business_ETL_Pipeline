# Azure_Retail_Business_ETL_Pipeline
Built an end-to-end retail data pipeline using Azure Data Factory, ADLS Gen2, Azure Databricks, and Power BI. Integrated transaction, store, and product data from Azure SQL Database with customer data from a REST API in JSON format. Implemented Bronze, Silver, and Gold layers for reliable data processing and analytics for retail reporting insights.

## Project Overview

This project demonstrates an end-to-end data engineering solution for a retail business using Microsoft Azure services.

The solution integrates data from multiple sources, including Azure SQL Database and REST APIs, and builds a scalable data pipeline to ingest, transform, store, and serve data for analytics and reporting.

## Technologies Used

- Azure Data Factory (ADF)
- Azure Data Lake Storage Gen2 (ADLS Gen2)
- Azure SQL Database
- Azure Databricks
- Apache Spark
- REST API
- JSON
- Delta Lake
- Medallion Architecture
- Power BI
- Git / GitHub

## Data Sources

1. Transaction Data – Azure SQL Database
2. Store Data – Azure SQL Database
3. Product Data – Azure SQL Database
4. Customer Data – REST API in JSON format

## Architecture

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/bffc1588-d0d6-4466-ae31-414637a8a764" />


## Business Objective

The objective is to build an end-to-end retail data pipeline that:

- Ingests data from multiple sources
- Stores raw data in Azure Data Lake
- Performs data cleansing and transformation
- Implements Bronze, Silver, and Gold layers
- Creates business-ready datasets
- Enables Power BI reporting and analytics

## Key Features

- Parameterized ADF pipelines
- Incremental data ingestion
- REST API integration
- JSON data processing
- Azure SQL Database integration
- ADLS Gen2 data storage
- Databricks transformations using PySpark
- Delta Lake implementation
- Medallion Architecture
- Error handling and monitoring
- Power BI reporting
- Git-based version control

## Expected Outcome

The final solution provides clean, transformed, and analytics-ready retail data that can be consumed by Power BI for business reporting and decision-making.
