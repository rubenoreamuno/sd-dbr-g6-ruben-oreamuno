
# Project: ETL with Databricks

This project demonstrates an ETL (Extract, Transform, Load) process using Databricks with a Medallion architecture (Bronze, Silver, Gold).

## Dataset

The dataset used is the Iris dataset, which is a classic dataset in machine learning and statistics. It contains 150 instances of iris flowers, each with four features: sepal length, sepal width, petal length, and petal width. The dataset also includes the species of each flower.

## Architecture

The project follows the Medallion architecture, which consists of three layers:

*   **Bronze Layer:** This layer contains the raw data, as it is ingested from the source system. The data in this layer is immutable.
*   **Silver Layer:** This layer contains the data after it has been cleaned, transformed, and enriched. The data in this layer is queryable and can be used for ad-hoc analysis.
*   **Gold Layer:** This layer contains the data after it has been aggregated and summarized. The data in this layer is used for reporting and visualization.

## ETL Process

The ETL process is implemented in three Jupyter notebooks, one for each layer:

*   **01-bronze.ipynb:** This notebook reads the raw data from the CSV file and writes it to a Delta table in the Bronze layer.
*   **02-silver.ipynb:** This notebook reads the data from the Bronze layer, performs some data cleaning and transformation, and writes the transformed data to a new Delta table in the Silver layer.
*   **03-gold.ipynb:** This notebook reads the data from the Silver layer, performs some aggregations, and writes the aggregated data to a new Delta table in the Gold layer.
