# Sales Data Analysis and Schema Implementation

## Project Overview

This project focuses on analyzing and structuring sales data to gain insights into customer behavior, sales trends, and shipping performance. The primary objective is to clean the data, design a Snowflake schema for efficient querying, and implement the schema by generating the necessary tables.

## Objective

The key objectives of this project are:

**1. Data Exploration and Cleaning:** Perform a thorough exploratory data analysis (EDA) to understand the structure, quality, and distribution of the data. This involves identifying and handling missing values, detecting and managing outliers, and preparing the data for further processing.

**2. Schema Design:** Develop a Snowflake schema based on the cleaned data. The schema is designed to normalize the data, reducing redundancy and ensuring efficient data relationships. This step involves defining both fact and dimension tables and their relationships.

**3. Data Integration:** Generate the final data tables based on the Snowflake schema. These tables are saved as CSV files and are ready to be loaded into a data warehouse for future analysis.

## Tools Used

1. Jupyter Notebook
2. Tableau
3. GitHub

## Language Used

1. Python
2. Tableau Functions

## Libraries 

1. Pandas
2. Xlrd
3. Matplotlib
4. Seaborn
5. Graphviz

**Note: Kindly install Graphviz and refer to document for setup. Link : https://graphviz.org/download/**

## Understanding flow of Work

1. Extract, & Transformation of Data in Python
2. Performing Exploratory Data Analysis in Python
   a. Check Data Integrity, Correctness & Completeness
   b. Checked Duplicate Data to remove redundancy
   c. Check for Outliers - Box Plot Method and Skewness checked
3. Data Modelling - Snowflake Schema
4. Export Final Tables for Visualisation
5. Dashboard Created for Tracking Metrics using Tableau

## Data Exploration and Cleaning

**1. Initial Analysis:** We start by exploring the datasets to understand the data structure and content. This includes checking for missing values, duplicates, and any inconsistencies.
**2. Data Cleaning:** Based on the initial analysis, we clean the data by handling missing values, removing duplicates, and correcting any inconsistencies found in the datasets.
**3. Outlier Detection:** We identify and address outliers in the dataset, particularly focusing on high-value transactions that could skew the analysis.

## Schema Design

**1. Schema Selection:** We choose a Snowflake schema for this project because it allows for normalized data, reducing redundancy and improving query performance.
**2. Fact Table:** The **Order Fact Table** is designed to capture transactional data, including Order_ID, Customer_ID, Product_ID, and Amount.
**3. Dimension Tables:**
   **a. Customer Table:** Stores customer details, linking to the Country Table.
   **b. Country Table:** Normalizes country information to avoid repetition.
   **c. Product Table:** Contains product-related details, linked to the Order Fact Table.
   **d. Shipping Table:** Connected to the Customer Table via Customer_ID, storing shipping status information.


**Data Integration**

**1. Generating Tables:** After designing the schema, we generate the necessary tables as CSV files. These tables are structured according to the Snowflake schema, ensuring that they are ready for efficient querying.
**2. Saving Tables:** The final tables (Country_Table.csv, Customer_Table.csv, Product_Table.csv, Order_Fact_Table.csv, and Shipping_Table.csv) are saved in the working directory, prepared for loading into a data warehouse.


## **Findings**

**1. Data Quality:** The initial data exploration revealed no issues with missing values, but some high-value outliers were identified in the order amounts. These outliers were addressed to ensure accurate analysis. Outliers were for two products : {Monitor, Harddisk}; for which on further exploration I found that these two are high valied product, thus being identified as outliers.

**2. Schema Design:** The Snowflake schema was successfully implemented, with normalized tables ensuring efficient data storage and retrieval. The Shipping Table was effectively connected to the Customer Table via Customer_ID, allowing for comprehensive analysis of shipping data in relation to customer information.


# Final Cleaned Datasets are exported and saved to **DataModelTables** folder; which we will use in creating visualisation dashboards.


# Technical Specification for Data Engineer

## Project Overview

The goal of this project is to implement a Snowflake schema for our sales data to support efficient querying and reporting. This schema will provide a structured and normalized data model, which will help in analyzing customer behavior, sales trends, and shipping performance.

## Data Model
**Fact Table:** Order Fact Table
                _This is our central table, capturing all transactional data related to sales. Key columns include Order_ID, Customer_ID, Product_ID, and Amount._

## Dimension Tables

**1. Customer Table:** Contains all customer-related details. Each customer is linked to a country in the Country Table.
**2. Country Table:** Normalizes country information to avoid repetition.
**3. Product Table:** Stores product information.
**4. Shipping Table:** Tracks the shipping status of each order, linked to the Customer Table via Customer_ID.

## Relationships

**1. Customer Table ↔ Order Fact Table:** One-to-Many
**2. Country Table ↔ Customer Table:** One-to-Many
**3. Product Table ↔ Order Fact Table:** One-to-Many
**4. Customer Table ↔ Shipping Table:** One-to-Many

### ETL Process

**Extract:** Pull data from the source systems (CRM, ERP, Logistics).

**Transform:** Normalize the data and clean up inconsistencies.

**Load:** Load the data into the Snowflake schema, starting with dimension tables.

#### Performance Tips

1. Consider indexing Customer_ID, Product_ID, and Shipping_ID in the fact table.
2. Partition the fact table by date or Order_ID for better performance.
3. Create trigger functions to have an alert system on any data inconsistency or issues encountered.


# Sales Dashboard : https://public.tableau.com/app/profile/raj.vishal/viz/PEIDataAnalystTask-SalesDashboard/SalesDashboard-1
