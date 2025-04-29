# ToTotes ETL Pipeline

## Overview
This project demonstrates a complete, serverless ETL (Extract, Transform, Load) pipeline built on AWS. It ingests operational data from a PostgreSQL database, transforms it using Python and pandas, and loads it into a data warehouse structured around a star schema. The entire solution is automated using Terraform and CI/CD practices.

Originally built as part of a team, this version has been individually forked, updated, and maintained to showcase end-to-end data engineering capability.

---

## Problem Statement
Businesses often store critical data across transactional systems with limited analytical access. This pipeline extracts raw data from an operational database, structures and transforms it, and loads it into a warehouse-ready format — enabling downstream analytics and dashboards.

---

## Architecture Overview

- **Extract Lambda:**  
  Connects to a PostgreSQL database using `pg8000`, retrieves table data using SQL queries, and writes raw datasets to S3 in CSV format.

- **Transform Lambda:**  
  Reads raw CSVs from S3, cleans and restructures them using `pandas`, and writes processed datasets back to a separate S3 location (processed zone).

- **Load Lambda:**  
  Dynamically generates SQL `INSERT` statements and loads the cleaned data into a PostgreSQL data warehouse using `awswrangler`. Data is written into **fact and dimension tables** following a star schema.

- **Infrastructure & Automation:**  
  All AWS resources (Lambda, IAM, S3, CloudWatch) are provisioned with **Terraform**. CI/CD pipelines are handled via **GitHub Actions** (YAML) and a **Makefile** for automation. Lambda execution is monitored using CloudWatch logs and alerts.

- **Development Process:**  
  Project was managed using **Agile methodology** with Kanban boards in Trello, broken into 2-week sprints.

---

## Technologies Used

- **Python** – pandas, boto3, pg8000, awswrangler
- **AWS Services** – Lambda, S3, IAM, CloudWatch, Secrets Manager
- **PostgreSQL** – Source and destination databases
- **Terraform** – Infrastructure as Code
- **GitHub Actions (YAML)** – CI/CD deployment workflows
- **Makefile** – Automation for build and test commands
- **Agile (Kanban)** – Sprint tasks tracked in Trello
- **Data Modeling** – Star schema (fact and dimension tables)
- **Testing & Quality** – Pytest, Moto, Bandit, Safety, Black

---

## Key Features

- Modular ETL with three independently deployed Lambda functions
- SQL-based extraction and loading, with pandas-based transformation
- Raw and processed storage layers in Amazon S3
- Secure secrets handling via AWS Secrets Manager
- CloudWatch monitoring and Terraform-defined alerting
- Sprint-based agile workflow (Kanban board in Trello)
- Fully tested with mocked AWS resources

---

## Personal Contribution

- Wrote and deployed the Extract and Transform Lambda functions using Python
- Developed dynamic SQL `INSERT` generation logic in the Load Lambda to populate a star schema warehouse
- Wrote and configured Terraform modules for Lambda, IAM, CloudWatch, and S3
- Set up and maintained CI/CD pipelines using GitHub Actions and a Makefile
- Managed sprint planning, task breakdowns, and retros using Trello

---

## Results

- Delivered a production-ready serverless ETL pipeline, deployable via infrastructure as code
- Enabled automated ingestion, cleaning, and structured loading of operational data across 12+ source tables
- Supported downstream analytics through structured warehouse tables and clean, query-ready data
- Demonstrated strong DevOps, DataOps, and Agile discipline throughout the build

