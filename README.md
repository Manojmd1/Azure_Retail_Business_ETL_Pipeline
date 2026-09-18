#  Azure Retail Business ETL & Power BI Analytics

## 📖 Project Overview

This project demonstrates an end-to-end Azure Data Engineering and Business Intelligence solution for processing retail business data.

The project uses **Azure Data Factory (ADF)** for data ingestion and transformation, **Azure Data Lake Storage Gen2 (ADLS Gen2)** for scalable data storage, **Parquet** as the storage format, and **Power BI** for business reporting and visualization.

The solution processes four retail datasets:

- Transactions
- Products
- Stores
- Customers

The raw data is first ingested and stored in Azure Data Lake Storage Gen2. The data is then cleaned, validated, joined, transformed, and aggregated using **Azure Data Factory Mapping Data Flows**.

The final business-ready Gold dataset is connected to Power BI to create interactive dashboards for analyzing:

- Sales performance
- Product performance
- Store performance
- Category performance
- Location performance
- Transaction trends
- Quantity sold
- Average transaction value


# 🏗️ Architecture

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/2560a7c0-3aa1-46ed-a571-e5ae6c5a3b10" />


# 🎯 Business Objective

* What is the total sales amount?
* How many products were sold?
* How many transactions occurred?
* Which products generate the highest sales?
* Which categories generate the highest revenue?
* Which stores generate the highest sales?
* Which locations perform better?
* How does sales performance change over time?
* What is the average transaction value?


# 🛠️ Technologies Used

| Technology                   | Purpose                       |
| ---------------------------- | ----------------------------- |
| Microsoft Azure              | Cloud platform                |
| Azure Data Factory           | Data ingestion and ETL        |
| Azure Data Lake Storage Gen2 | Data lake storage             |
| Azure SQL Database           | Relational data source        |
| REST API / JSON              | External data source          |
| Parquet                      | Data storage format           |
| ADF Mapping Data Flow        | Data transformation           |
| Power BI                     | Data visualization            |
| DAX                          | Business calculations         |
| Git                          | Version control               |
| GitHub                       | Source code and documentation |


# ☁️ Azure Services Used

## Azure Data Factory

Azure Data Factory is used as the main data integration and ETL service.

It is responsible for:

* Connecting to data sources
* Copying source data
* Moving data to ADLS Gen2
* Running Mapping Data Flows
* Cleaning data
* Joining datasets
* Creating calculated columns
* Aggregating business data

## Azure Data Lake Storage Gen2

ADLS Gen2 is used as the central storage layer.

The project uses ADLS Gen2 to store:

Raw Data
Silver Data
Gold Data

The data is stored using **Parquet format**.

Parquet provides a columnar storage format suitable for analytical workloads.


## Azure SQL Database

Azure SQL Database is used as one of the relational data sources for the project.

ADF connects to the SQL Database through a Linked Service and reads the required retail data.


## REST API / JSON

REST API / JSON data can be used as an external source for retail information.

ADF can ingest this data and move it into ADLS Gen2 for further processing.

## Power BI

Power BI is used as the final analytics and visualization layer.

The Gold dataset is used to create:

* KPI cards
* Bar charts
* Line charts
* Tables
* Slicers
* Interactive dashboards


# 📂 Dataset Information

The project uses four major datasets.

# 1️⃣ Transaction Dataset

The Transaction dataset contains information about retail transactions.

### Columns

id
transaction_id
customer_id
product_id
store_id
quantity
transaction_date

### Description

| Column           | Description                   |
| ---------------- | ----------------------------- |
| id               | Source record identifier      |
| transaction_id   | Unique transaction identifier |
| customer_id      | Customer identifier           |
| product_id       | Product identifier            |
| store_id         | Store identifier              |
| quantity         | Quantity purchased            |
| transaction_date | Date of transaction           |

# 2️⃣ Product Dataset

The Product dataset contains product information.

### Columns

id
product_id
product_name
category
price


### Description

| Column       | Description              |
| ------------ | ------------------------ |
| id           | Source record identifier |
| product_id   | Product identifier       |
| product_name | Product name             |
| category     | Product category         |
| price        | Product selling price    |


# 3️⃣ Store Dataset

The Store dataset contains information about retail stores.

### Columns

id
store_id
store_name
location

### Description

| Column     | Description              |
| ---------- | ------------------------ |
| id         | Source record identifier |
| store_id   | Store identifier         |
| store_name | Store name               |
| location   | Store location           |


# 4️⃣ Customer Dataset

The Customer dataset contains customer information.

### Columns

id
customer_id
first_name
last_name
email
city
registration_date

### Description

| Column            | Description                |
| ----------------- | -------------------------- |
| id                | Source record identifier   |
| customer_id       | Customer identifier        |
| first_name        | Customer first name        |
| last_name         | Customer last name         |
| email             | Customer email             |
| city              | Customer city              |
| registration_date | Customer registration date |


# 🔄 End-to-End Data Flow

The complete data flow is:

Source Data
    ↓
Azure Data Factory
    ↓
Copy Activity
    ↓
ADLS Gen2
    ↓
Raw / Bronze Layer
    ↓
Silver Mapping Data Flow
    ↓
Data Cleaning
    ↓
Data Filtering
    ↓
Product Join
    ↓
Total Amount Calculation
    ↓
Store Join
    ↓
Customer Join
    ↓
Silver Layer
    ↓
Gold Mapping Data Flow
    ↓
Aggregation
    ↓
Business Metrics
    ↓
Gold Layer
    ↓
Power BI
    ↓
Interactive Dashboard

# 🥉 RAW / BRONZE LAYER

The Raw/Bronze layer stores the data after ingestion from the source systems.

The purpose of this layer is to maintain the source data in the data lake before applying business transformations.

The data is stored in **Parquet format**.

The main datasets are:

transactions.parquet
products.parquet
stores.parquet
customers.parquet


# 📥 Data Ingestion Using Azure Data Factory

Azure Data Factory Copy Activities are used to ingest the source datasets into ADLS Gen2.

The ingestion process handles:

Transaction Data
       ↓
ADLS Gen2

Product Data
       ↓
ADLS Gen2

Store Data
       ↓
ADLS Gen2

Customer Data
       ↓
ADLS Gen2


# 🔗 ADF Linked Services

Linked Services are configured in Azure Data Factory to establish connections between ADF and external services.

The project uses connections for:

Azure SQL Database
        ↓
Azure Data Factory

ADLS Gen2
        ↓
Azure Data Factory

# 📦 ADF Datasets

Datasets represent the structure and location of the data used by ADF.

The project uses datasets for:

Transaction Data
Product Data
Store Data
Customer Data
Raw Parquet Data
Silver Parquet Data
Gold Parquet Data


# 🔄 ADF Copy Pipeline

The ingestion pipeline uses Copy Activities to move source data into the Raw layer.

The logical pipeline flow is:

Transaction Copy
       ↓
Product Copy
       ↓
Store Copy
       ↓
Customer Copy


# 🥈 SILVER LAYER

The Silver layer contains cleaned and integrated data.

Azure Data Factory Mapping Data Flow is used to create the Silver layer.

The transformation flow is:

Transaction Source
        ↓
Cleaning
        ↓
Filtering
        ↓
Join Product
        ↓
Calculate Total Amount
        ↓
Join Store
        ↓
Join Customer
        ↓
Select Required Columns
        ↓
Silver Sink

# 🧹 Silver Data Cleaning

The Silver transformation performs several data preparation operations.

These include:

* Removing unnecessary fields
* Selecting required columns
* Cleaning string values
* Handling invalid records
* Filtering unwanted records
* Validating data types
* Removing duplicate join columns
* Joining related datasets
* Creating calculated fields

# 🔍 Filtering

The Filter transformation is used to remove records that do not satisfy the required business conditions.

For example, invalid or unusable transaction records can be excluded before they reach the Silver layer.

# 🔗 Product Join

Transaction data is joined with Product data using:

transaction.product_id
        =
product.product_id

This adds product information to each transaction.

The resulting dataset contains:

product_id
product_name
category
price

# 💰 Total Amount Calculation

A calculated column is created using:

total_amount = quantity * price

For example:

Quantity = 5
Price = 100

Total Amount = 5 × 100

Total Amount = 500


The calculated `total_amount` is used later for sales aggregation.

# 🏪 Store Join

Transaction data is joined with Store data using:

transaction.store_id
        =
store.store_id

This adds:

store_name
location

to the transaction data.

# 👤 Customer Join

Transaction data is joined with Customer data using:

transaction.customer_id
        =
customer.customer_id

This adds customer-related fields such as:

first_name
last_name
email
city
registration_date

# 📋 Silver Select Transformation

The Select transformation is used to control the final columns written to the Silver layer.

Duplicate key columns created by joins are removed from the final output.

The final Silver dataset contains:

id
transaction_id
transaction_date
customer_id
first_name
last_name
email
city
registration_date
product_id
product_name
category
price
store_id
store_name
location
quantity
total_amount

The Select transformation ensures that the Silver dataset contains only the required business columns.

# 🥇 GOLD LAYER

The Gold layer contains business-ready aggregated data.

The Gold Mapping Data Flow reads the Silver data and calculates business metrics.

The Gold transformation groups the data using:

transaction_date
product_id
product_name
category
store_id
store_name
location

# 📊 Gold Aggregations

The following metrics are calculated.

## Total Quantity Sold

SUM(quantity)

Output column:
total_quantity_sold

## Total Sales Amount

SUM(total_amount)

Output column:

total_sales_amount

## Number of Transactions

COUNT(transaction_id)

Output column:

number_of_transactions

## Average Transaction Value

AVG(total_amount)

Output column:

average_transaction_value

# 📦 Final Gold Dataset

The final Gold dataset contains:

transaction_date
product_id
product_name
category
store_id
store_name
location
total_quantity_sold
total_sales_amount
number_of_transactions
average_transaction_value

This dataset is designed for Power BI reporting and business analysis.

# 📊 POWER BI ANALYTICS

The Gold dataset is connected to Power BI.

Power BI is used to convert the aggregated Gold data into interactive business dashboards.

The dashboard includes:

KPI Cards
Line Charts
Bar Charts
Tables
Slicers


# 📈 Dashboard Pages

## Page 1 — Executive Overview

The Executive Overview provides a high-level summary of retail business performance.

### KPI Cards

Total Sales
Total Quantity Sold
Total Transactions
Average Transaction Value
Products Sold

### Visualizations

Sales Trend Over Time
Sales by Category
Sales by Store
Top 10 Products by Sales
Sales by Location


### Slicers

Transaction Date
Category
Store Name

# 📦 Page 2 — Product Analysis

The Product Analysis page focuses on product performance.

### Visuals

Sales by Product
Quantity Sold by Product
Sales by Category
Top Products
Product Performance Table

### Business Questions

Which products generate the highest sales?

Which products have the highest quantity sold?

Which categories generate the highest revenue?

# 🏪 Page 3 — Store Analysis

The Store Analysis page focuses on store performance.

### Visuals

Sales by Store
Quantity Sold by Store
Transactions by Store
Sales by Location
Store Performance Table

### Business Questions

Which stores generate the most sales?

Which locations generate higher sales?

How many transactions are processed by each store?

# 📅 Page 4 — Time Analysis

The Time Analysis page analyzes performance over time.

### Visuals

Sales Trend
Quantity Trend
Transaction Trend
Date-Based Analysis

### Business Questions
How do sales change over time?

Which dates have higher sales?

How does transaction volume change over time?


# 📋 Page 5 — Sales Details

The Sales Details page provides a detailed view of the Gold dataset.

Important columns include:

transaction_date
product_id
product_name
category
store_id
store_name
location
total_quantity_sold
total_sales_amount
number_of_transactions
average_transaction_value

# 🧮 DAX MEASURES

The following DAX measures are created in Power BI.

## Total Sales

Total Sales =
SUM(Gold[total_sales_amount])

## Total Quantity Sold

Total Quantity Sold =
SUM(Gold[total_quantity_sold])


## Total Transactions

Total Transactions =
SUM(Gold[number_of_transactions])

## Average Transaction Value

Average Transaction Value =
DIVIDE(
    [Total Sales],
    [Total Transactions],
    0
)

## Average Selling Price

Average Selling Price =
DIVIDE(
    [Total Sales],
    [Total Quantity Sold],
    0
)


## Products Sold

Products Sold =
DISTINCTCOUNT(Gold[product_id])

## Stores

Stores =
DISTINCTCOUNT(Gold[store_id])

# 🔎 Top 10 Products Analysis

A Top 10 filter is applied to the Product Sales visualization.

The visual uses:

Axis:
product_name

Values:
Total Sales

A Top N filter is applied to `product_name`:

Top 10
By Value:
Total Sales

This visualization identifies the ten products with the highest sales amount.

# 📊 Business Insights

The project enables analysis of several important retail business areas.

## Sales Performance

The dashboard provides:

Total Sales
Total Transactions
Average Transaction Value

These metrics provide a summary of overall sales performance.

## Product Performance

Product-level analysis provides:

Product Sales
Quantity Sold
Category Sales
Average Selling Price

This allows business users to analyze product and category performance.

## Store Performance

Store-level analysis provides:

Store Sales
Store Transactions
Store Quantity
Location Sales

This helps analyze performance across different stores and locations.

## Time-Based Analysis

Time analysis provides:

Sales Trend
Transaction Trend
Quantity Trend

This allows business users to analyze changes in retail activity over time.

# 🗂️ Project Folder Structure

A suggested GitHub repository structure is:

Azure_Retail_Business_ETL_Pipeline/
│
├── README.md
│
├── ADF/
│   ├── Pipelines/
│   ├── Dataflows/
│   ├── Datasets/
│   └── LinkedServices/
│
├── Data/
│   └── Sample/
│
├── PowerBI/
│   ├── Dashboard/
│   └── DAX/
│
├── Screenshots/
│   ├── ADF_Pipeline.png
│   ├── Silver_Dataflow.png
│   ├── Gold_Dataflow.png
│   ├── ADLS_Raw.png
│   ├── ADLS_Silver.png
│   ├── ADLS_Gold.png
│   └── PowerBI_Dashboard.png
│
└── Documentation/
    └── Architecture.png

## Silver Mapping Data Flow

Source
  ↓
Clean
  ↓
Filter
  ↓
Join Product
  ↓
Derived Column
  ↓
Join Store
  ↓
Join Customer
  ↓
Select
  ↓
Sink

## Gold Mapping Data Flow

Silver Source
      ↓
Aggregate
      ↓
Gold Sink

# 🚀 Implementation Workflow

The complete implementation process is:

### Step 1

Create Azure resources.

Resource Group
Azure Data Factory
ADLS Gen2
Azure SQL Database

### Step 2

Configure Azure Data Factory Linked Services.

### Step 3

Create source and sink datasets.

### Step 4

Create Copy Activities.

### Step 5

Run the ingestion pipeline.

### Step 6

Verify the Parquet files in ADLS Gen2.

### Step 7

Create the Silver Mapping Data Flow.

### Step 8

Clean and filter the transaction data.

### Step 9

Join Transaction with Product.

### Step 10

Calculate:

total_amount = quantity * price


### Step 11

Join Store data.

### Step 12

Join Customer data.

### Step 13

Select the required Silver columns.

### Step 14

Write the Silver output to ADLS Gen2.

### Step 15

Create the Gold Mapping Data Flow.

### Step 16

Group the Silver data by:

transaction_date
product_id
product_name
category
store_id
store_name
location

### Step 17

Calculate:

total_quantity_sold
total_sales_amount
number_of_transactions
average_transaction_value


### Step 18

Write the Gold output to ADLS Gen2.

### Step 19

Connect Power BI to the Gold data.

### Step 20

Create DAX measures.

### Step 21

Create Power BI dashboards.

### Step 22

Publish the project documentation and screenshots to GitHub.

# 🧪 Data Validation

Data validation is performed throughout the pipeline.

Important checks include:

✔ Required columns exist
✔ Numeric fields contain valid values
✔ Date fields have valid data types
✔ Join keys are available
✔ Invalid records are filtered
✔ Duplicate join columns are removed
✔ Calculated fields are generated correctly
✔ Gold aggregations are created correctly

# 🧩 Challenges Faced During Development

During implementation, several practical Azure Data Engineering challenges were encountered.

## 1. ADLS File Path Issues

ADF Copy Activity can fail when the configured file path does not match the actual file location in ADLS Gen2.

The solution is to verify:

Storage Account
Filesystem
Folder
File Name

and make sure the ADF dataset points to the correct location.

## 2. Azure SQL Connectivity

Connectivity between Azure Data Factory and Azure SQL Database requires correct configuration of:

Server
Database
Username
Password
Firewall
Network Access
Azure SQL firewall settings must allow the required connection.

## 3. Data Type Conversion

Mapping Data Flow transformations require compatible data types.

For example, date conversion should only be performed when the source field is not already a date or timestamp.

The data type of source columns should be checked before applying conversion functions.

## 4. Duplicate Columns After Joins

Joining multiple datasets can create duplicate key columns.

For example:
transaction.product_id
product.product_id

Both columns represent the same business key.

The Select transformation is used to keep the required column and remove the duplicate output column.

## 5. Power BI Authentication

Power BI and Azure authentication can differ depending on the account type and service being accessed.

When connecting Power BI to Azure resources, the correct authentication method and account permissions must be used.

# 📌 Why Parquet?

Parquet is used as the storage format because it is a columnar file format designed for analytical workloads.

Advantages include:

* Column-based storage
* Efficient analytical queries
* Compression
* Reduced storage requirements
* Efficient processing
* Good integration with Azure data services

# 📌 Why Raw, Silver and Gold Layers?

The layered approach separates different stages of data processing.

## Raw / Bronze

Contains ingested source data.

Purpose:
Data preservation


## Silver

Contains cleaned and integrated data.

Purpose:
Data quality and transformation


## Gold

Contains aggregated business-ready data.

Purpose:
Analytics and reporting

This separation makes the pipeline easier to maintain and understand.


# 📊 Final Dashboard Structure

<img width="1326" height="742" alt="image" src="https://github.com/user-attachments/assets/e2138c86-3207-4876-bf17-ac06ba0b6ae2" />

# 🎓 Skills Demonstrated

This project demonstrates practical knowledge of:

## Azure

Microsoft Azure
Azure Data Factory
Azure Data Lake Storage Gen2
Azure SQL Database

## Azure Data Factory

Linked Services
Datasets
Pipelines
Copy Activities
Mapping Data Flows
Source Transformation
Filter Transformation
Join Transformation
Derived Column Transformation
Select Transformation
Aggregate Transformation
Sink Transformation

## Power BI

Data Connection
Data Modeling
DAX
KPI Cards
Bar Charts
Line Charts
Tables
Slicers
Interactive Dashboards
Business Analysis


# 📈 Final Outcome

The final solution successfully transforms raw retail data into business-ready analytical information.

             RAW RETAIL DATA
                    │
                    ▼
          AZURE DATA FACTORY
                    │
                    ▼
             ADLS GEN2
                    │
                    ▼
             RAW / BRONZE
                    │
                    ▼
          SILVER DATA FLOW
                    │
       ┌────────────┼────────────┐
       │            │            │
    Cleaning     Joining     Validation
       │            │            │
       └────────────┼────────────┘
                    │
                    ▼
              SILVER DATA
                    │
                    ▼
            GOLD DATA FLOW
                    │
                    ▼
          BUSINESS AGGREGATION
                    │
                    ▼
               GOLD DATA
                    │
                    ▼
                POWER BI
                    │
                    ▼
           BUSINESS DASHBOARD

# Project Highlights

✔ End-to-end Azure Data Engineering project

✔ Azure Data Factory used for ETL

✔ ADLS Gen2 used as the central data lake

✔ Parquet used for data storage

✔ Retail transaction data processed

✔ Product, Store and Customer datasets integrated

✔ ADF Mapping Data Flows used for transformations

✔ Data cleaning and filtering implemented

✔ Multiple datasets joined using business keys

✔ Total transaction amount calculated

✔ Silver layer created

✔ Gold aggregation layer created

✔ Business metrics generated

✔ Power BI dashboard developed

✔ DAX measures implemented

✔ GitHub used for project documentation


# Conclusion

This Azure Retail Business ETL project demonstrates how cloud data engineering technologies can be used to transform raw retail data into meaningful business insights.

The solution covers the complete data lifecycle:

Data Ingestion
      ↓
Data Storage
      ↓
Data Cleaning
      ↓
Data Integration
      ↓
Data Transformation
      ↓
Data Aggregation
      ↓
Business Intelligence
      ↓
Data Visualization


The project provides practical hands-on experience with Azure Data Factory, ADLS Gen2, Azure SQL Database, Parquet, Mapping Data Flows, Power BI, DAX, Git, and GitHub.

# 👨‍💻 Author

Manoj M D

# 📚 Conclusion

This Azure Retail Business ETL project demonstrates how cloud data engineering technologies can be used to transform raw retail data into meaningful business insights.
