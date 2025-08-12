
# Project: ETL with Databricks

This project demonstrates an ETL (Extract, Transform, Load) process using Databricks with a Medallion architecture (Bronze, Silver, Gold).

## Storage

This project uses Google Cloud Storage (GCS) for storing the data and Unity Catalog for managing the tables.

### GCS Bucket

You will need to create a GCS bucket to store the data. The bucket should be named `databricks-final-project`.

### Unity Catalog

You will need to create a Unity Catalog metastore and mount the following volumes:

*   `/Volumes/main/default/bronze`
*   `/Volumes/main/default/silver`
*   `/Volumes/main/default/gold`

## Dataset

The dataset used is the "Adult" dataset from the UCI Machine Learning Repository. It contains information about individuals from a 1994 census database, including age, workclass, education, marital status, occupation, and more. The dataset is used to predict whether an individual's income exceeds $50K/yr.

The dataset is downloaded from the internet and stored in the GCS bucket.

## Architecture

The project follows the Medallion architecture, which consists of three layers:

*   **Bronze Layer:** This layer contains the raw data, as it is ingested from the source system. The data in this layer is immutable.
*   **Silver Layer:** This layer contains the data after it has been cleaned, transformed, and enriched. The data in this layer is queryable and can be used for ad-hoc analysis.
*   **Gold Layer:** This layer contains the data after it has been aggregated and summarized. The data in this layer is used for reporting and visualization.

## ETL Process

The ETL process is implemented in three Jupyter notebooks, one for each layer:

*   **01-bronze.ipynb:** This notebook reads the raw data from the GCS bucket and writes it to a Delta table in the Bronze layer, using a Unity Catalog volume. The schema is defined using DDL.
*   **02-silver.ipynb:** This notebook reads the data from the Bronze layer, performs some data cleaning and transformation, and writes the transformed data to a new Delta table in the Silver layer, using a Unity Catalog volume.
*   **03-gold.ipynb:** This notebook reads the data from the Silver layer, performs some aggregations, and writes the aggregated data to a new Delta table in the Gold layer, using a Unity Catalog volume.
