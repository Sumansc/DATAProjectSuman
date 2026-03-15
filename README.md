Retail Sales Data Pipeline (Azure Databricks + PySpark + ADLS + Power BI)
**Project Overview:**

This project implements an end-to-end retail sales analytics pipeline using Azure SQL Database, Azure Data Lake Storage (ADLS), Azure Databricks (PySpark), Delta Lake, and Power BI. The pipeline follows the Medallion Architecture (Bronze → Silver → Gold) to ingest, clean, transform, and analyze retail sales data.

Architecture

Source → Azure SQL Database
Storage → Azure Data Lake Storage (ADLS)
Processing → Azure Databricks (PySpark)
Storage Format → Delta Lake
Visualization → Power BI

Pipeline Workflow
1. Data Source

Retail datasets were created in Azure SQL Database, including tables for:

Transactions

Products

Stores

Customers

Sample data was inserted into these tables to simulate a retail sales system.

2. Data Ingestion (Bronze Layer)

Data from Azure SQL Database was ingested into Azure Data Lake Storage (ADLS) and stored in the Bronze layer as raw Parquet files.
This layer contains unprocessed raw data for transactions, products, stores, and customers.

3. Data Cleaning and Processing (Silver Layer)

Data from the Bronze layer was processed in Azure Databricks using PySpark to create the Silver layer.

Transformations performed:

Schema enforcement and type casting

Duplicate record removal

Data validation and cleaning

Multi-table joins between transactions, products, stores, and customers

Feature engineering (total transaction amount)

The cleaned dataset was stored in ADLS as Delta tables.

4. Data Transformation for Analytics (Gold Layer)

Further transformations were performed on the Silver dataset to generate business analytics metrics.

Key metrics generated:

Total sales amount

Total quantity sold

Number of transactions

Average transaction value

The aggregated dataset was written to the Gold layer in ADLS using Delta format.

5. Data Visualization

The Gold layer dataset was connected to Power BI via Azure Databricks to build an interactive dashboard.

Key insights visualized:

Store-wise quantity sold

Location-wise sales distribution

Product-wise revenue contribution

Category-wise transaction trends

Technologies Used

Azure SQL Database

Azure Data Lake Storage (ADLS)

Azure Databricks

PySpark

Delta Lake

Power BI

Key Concepts Implemented

Medallion Architecture (Bronze, Silver, Gold)

ETL Pipeline Design

Data Cleaning and Deduplication

Multi-table Joins and Transformations

Delta Lake Storage with ACID Transactions

Data Visualization and Business Insights
