# Cassandra Medallion Architecture Project

## Done by: Keerthana Bellam

---

## Overview

This project demonstrates the implementation of Medallion Architecture using Cassandra (Astra DB) and Python in Google Colab. The project focuses on organizing data into layered architecture (Bronze → Silver → Gold) for better data management and analytics.

Dataset used: [sales_100.csv](https://github.com/gchandra10/filestorage/blob/main/sales_100.csv)

---

## Tools & Technologies Used

- Apache Cassandra (Astra DB - Cloud)
- Python
- Google Colab
- Pandas
- Astrapy (Cassandra Python Client)

---

## Architecture

    +-----------------+
    | Raw CSV Data    |
    +-----------------+
             ↓
    +-----------------+
    | Bronze Layer    |
    | (Raw Data)      |
    +-----------------+
             ↓
    +-----------------+
    | Silver Layer    |
    | (Cleaned Data)  |
    +-----------------+
             ↓
    +------------------------------+
    | Gold Layer                   |
    | (Aggregations & Insights)   |
    +------------------------------+


---

## Layer Explanation

### Bronze Layer:
- Loaded raw data from `sales_100.csv` into `sales_bronze` collection.
- No transformations, direct ingestion.

---

### Silver Layer:
- Cleaned the Bronze data:
  - Removed duplicates
  - Removed null values
  - Converted columns to correct datatypes (dates, numbers)
- Stored the clean data into `sales_silver` collection.

---

### Gold Layer:
Created 3 Aggregation Tables:

| Collection Name        | Purpose                           |
|------------------------|----------------------------------|
| sales_gold_region      | Total Revenue by Region          |
| sales_gold_product     | Total Profit by Product (Item Type) |
| sales_gold_country     | Total Revenue by Country         |

---

## Folder Structure

cassandra-medallion-project/
│
├── bronze/                       
│   └── bronze_layer.ipynb        # Raw data loading code (Bronze Layer)
│
├── silver/                       
│   └── silver_layer.ipynb        # Data cleaning & transformation (Silver Layer)
│
├── gold/                         
│   └── gold_layer.ipynb          # Aggregation logic (Gold Layer)
│
├── schema/                       
│   └── collections.md            # Explanation of all Cassandra collections
│
├── screenshots/                  # Output screenshots from Colab & AstraDB
│   └── bronze.png         # Bronze Layer Output Screenshot
│   └── silver.png         # Silver Layer Output Screenshot
│   └── gold1.png    # Gold Layer - Revenue by Region
│   └── gold2.png   # Gold Layer - Profit by Product
│   └── gold3.png   # Gold Layer - Revenue by Country
│
├── requirements.txt              # Required Python Packages (astrapy, pandas)
│
└── README.md                     # Project Documentation & Explanation
