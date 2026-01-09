# Spotify Data Engineering Pipeline (AWS)

## Overview

This project implements an end-to-end data engineering pipeline on Amazon Web Services (AWS) to process and analyze Spotify datasets. Raw CSV files containing artist, track, and album information are ingested into Amazon S3, transformed using AWS Glue ETL jobs, stored in analytics-optimized Parquet format, and queried using Amazon Athena. The processed data is visualized using Power BI for downstream analytics and reporting.

This project demonstrates core data engineering concepts such as data ingestion, ETL, schema management, columnar storage optimization, and SQL-based analytics on cloud infrastructure.

---

## Architecture and Components

### 1. Data Source

- CSV files containing Spotify artist, track, and album data  
- Files are manually uploaded to an Amazon S3 bucket as raw data  

---

### 2. AWS Services

**Amazon S3 (Simple Storage Service)**  
- Stores raw CSV files and transformed Parquet datasets  
- Acts as the data lake for the pipeline  

**AWS Glue**  
- Used to perform Extract, Transform, Load (ETL) operations  
- Glue ETL job performs inner joins across artist, track, and album datasets  
- Transformed data is written back to S3 in Parquet format  
- IAM roles are configured to allow Glue access to required S3 resources  

**AWS Glue Crawler**  
- Automatically infers schema from Parquet files  
- Creates and updates metadata tables in the AWS Glue Data Catalog  

**Amazon Athena**  
- Executes SQL queries directly on Parquet data stored in S3  
- Enables serverless, ad-hoc analytics  

---

### 3. Visualization

**Power BI**  
- Connected to Amazon Athena as a data source  
- Used to build dashboards and visualizations for Spotify analytics  

---

## Setup and Execution Steps

### Step 1: Upload Raw Data
- Upload CSV files for artists, tracks, and albums to the raw data S3 bucket  

### Step 2: Configure AWS Glue ETL Job
- Create an AWS Glue ETL job  
- Implement transformations and inner joins across datasets  
- Write the transformed output to S3 in Parquet format  
- Assign an IAM role with appropriate S3 and Glue permissions  

### Step 3: Run AWS Glue Crawler
- Create a crawler pointing to the Parquet output location  
- Run the crawler to generate schema metadata in the Glue Data Catalog  

### Step 4: Query Data Using Amazon Athena
- Connect Athena to the Glue Data Catalog tables  
- Run SQL queries to analyze the transformed Spotify data  

### Step 5: Visualize Using Power BI
- Connect Power BI to Amazon Athena  
- Build dashboards and reports using query results  

---

## Key Features

- End-to-end AWS-based data engineering pipeline  
- Columnar storage using Parquet for optimized query performance  
- Automated schema inference using AWS Glue Crawlers  
- Serverless SQL analytics with Amazon Athena  
- Business intelligence and visualization using Power BI  

---

## Notes and Considerations

- Ensure IAM roles and permissions are properly configured for S3, Glue, and Athena  
- Monitor AWS costs related to storage, ETL jobs, and query execution  
- The pipeline can be extended to support partitioning, incremental loads, and automation  

