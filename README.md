** Retail Data Pipeline Architecture Diagram:**
                    +----------------------+
                    |  Azure SQL Database  |
                    |  Source Tables       |
                    |----------------------|
                    | transactions         |
                    | products             |
                    | stores               |
                    | customers            |
                    +----------+-----------+
                               |
                               | Data Ingestion
                               v
        +--------------------------------------------------+
        | Azure Data Lake Storage (ADLS) - Bronze Layer   |
        | Raw Parquet Files                               |
        |--------------------------------------------------|
        | bronze/transactions/                             |
        | bronze/products/                                 |
        | bronze/stores/                                   |
        | bronze/customers/                                |
        +----------------------+---------------------------+
                               |
                               | PySpark ETL (Databricks)
                               v
        +--------------------------------------------------+
        | ADLS Silver Layer - Cleaned Data                 |
        | Delta Format                                     |
        |--------------------------------------------------|
        | silver/transactions_cleaned/                     |
        | silver/products_cleaned/                         |
        | silver/stores_cleaned/                           |
        | silver/customers_cleaned/                        |
        +----------------------+---------------------------+
                               |
                               | Data Transformation
                               v
        +--------------------------------------------------+
        | ADLS Gold Layer - Business Aggregates            |
        | Delta Tables                                     |
        |--------------------------------------------------|
        | gold/retail_sales_summary/                       |
        | (Total Sales, Quantity Sold, Transaction Count,  |
        |  Avg Transaction Value)                          |
        +----------------------+---------------------------+
                               |
                               | BI Connection
                               v
                    +----------------------+
                    | Power BI Dashboard   |
                    | Retail Sales Insights|
                    +----------------------+
