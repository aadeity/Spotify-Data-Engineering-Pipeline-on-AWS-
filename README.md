Spotify Data Engineering Pipeline (AWS)
Overview

This project implements an end-to-end data engineering pipeline on Amazon Web Services (AWS) to process and analyze Spotify datasets. Raw CSV files containing artist, track, and album information are ingested into Amazon S3, transformed using AWS Glue ETL jobs, stored in analytics-optimized Parquet format, and queried using Amazon Athena. The processed data is finally visualized using Power BI for downstream analytics and reporting.

The project demonstrates core data engineering concepts such as data ingestion, ETL, schema management, columnar storage optimization, and SQL-based analytics on cloud infrastructure.

Architecture and Components
1. Data Source

CSV files containing Spotify artist, track, and album data

Files are manually uploaded to an Amazon S3 bucket as raw data

2. AWS Services

Amazon S3 (Simple Storage Service)

Stores raw CSV files and transformed Parquet datasets

Acts as the data lake for the pipeline

AWS Glue

Used to perform Extract, Transform, Load (ETL) operations

Glue ETL job joins artist, track, and album datasets using inner joins

Transformed data is written back to S3 in Parquet format

IAM roles are configured to allow Glue access to required S3 resources

AWS Glue Crawler

Automatically infers schema from the generated Parquet files

Creates and updates metadata tables in the Glue Data Catalog

Amazon Athena

Executes SQL queries directly on Parquet data stored in S3

Enables ad-hoc analysis without data movement

3. Visualization

Power BI

Connected to Amazon Athena as a data source

Used to build dashboards and visualizations for Spotify analytics

Setup and Execution Steps

Upload Raw Data

Upload CSV files for artists, tracks, and albums to the raw data S3 bucket

Configure AWS Glue ETL Job

Create an AWS Glue job

Implement ETL logic to clean data and perform inner joins across datasets

Output the transformed data in Parquet format to a separate S3 location

Attach an IAM role with appropriate S3 and Glue permissions

Run AWS Glue Crawler

Create a crawler pointing to the Parquet output directory

Run the crawler to generate schema metadata in the Glue Data Catalog

Query Data Using Athena

Connect Athena to the Glue Data Catalog tables

Execute SQL queries to analyze the transformed Spotify data

Visualize in Power BI

Connect Power BI to Athena

Build dashboards and reports based on query results

Key Features

End-to-end AWS-based data pipeline

Columnar storage using Parquet for efficient querying

Schema inference and metadata management using Glue Crawlers

Serverless SQL analytics with Amazon Athena

BI integration using Power BI

Notes and Considerations

Ensure IAM roles and permissions are correctly configured for S3, Glue, and Athena

Monitor AWS costs related to S3 storage, Glue jobs, and Athena queries

The pipeline can be extended to support incremental loads, partitioning, and automated ingestion
