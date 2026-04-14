# AWS Big Data ETL & PySpark Cleaning Pipeline
## 📌 Project Overview
Following the data quality audit in AWS-Serverless-Data-Lake, I developed a production-grade ETL (Extract, Transform, Load) pipeline using PySpark. This project transitions the data lake from a "Raw" landing zone to a "Cleaned" optimized layer, focusing on distributed computing, data standardization, and storage performance optimization.

## 🏗️ Architecture
Source: Raw Global Superstore Sales data (CSV) isolated in S3.

Process: AWS Glue Interactive Session (PySpark) performing distributed transformations.

Storage (Sink): Amazon S3 (Optimized Parquet format).

Catalog & Analysis: Manual DDL mapping in Amazon Athena for sub-second query performance.

## 🛠️ Tech Stack
Cloud: AWS (S3, Glue, Athena, IAM)

Big Data Engine: Apache Spark (PySpark)

Storage Format: Apache Parquet (Columnar Storage)

Security: IAM Scoped Policies (PassRole, S3 CRUD)

## 🔍 Key Transformations & Engineering Wins
Using PySpark, I implemented a robust cleaning logic to resolve the integrity issues discovered previously:

Categorical Standardization: Converted all Region entries to uppercase and trimmed whitespace, successfully merging fragmented records (e.g., "north" and "North" into "NORTH").

Schema Enforcement: Explicitly cast Units_Sold to Integer and Revenue/Profit to Double for mathematical accuracy.

Storage Optimization: Converted the raw 2,000+ row CSV into Snappy-Compressed Parquet. This reduced storage footprint and optimized Athena query costs through columnar projection.

Cloud Troubleshooting: Successfully diagnosed and resolved complex IAM:PassRole and S3:DeleteObject permission errors during the Glue-Spark execution.

## 🚀 How to Reproduce
Move the raw CSV into a dedicated /raw-csv-data/ folder in S3.

Initialize an AWS Glue Notebook and run the cleaning script in /src/pyspark_etl.py.

Verify the output in the /cleaned_parquet_data/ S3 folder.

Execute the manual CREATE EXTERNAL TABLE query in Athena to map the Parquet metadata.

## 🖼️ Project Visuals
1. S3 Organization (S3 Parquet Objects)
![image_alt](https://github.com/NivedhReddy2048/AWS-PySpark-ETL-Pipeline/blob/main/S3%20Organization.png?raw=true)
3. Spark Execution (AWS Glue)
4. Final Production Report (Amazon Athena)
