# Collections Used in Cassandra Medallion Architecture Project

## Bronze Layer
- sales_bronze
> Raw data loaded directly from `sales_100.csv` without any transformation.

---

## Silver Layer
- sales_silver
> Cleaned data with proper data types, removed null values, duplicates handled, and ready for analytics.

---

## Gold Layer

| Collection Name | Purpose | Aggregation Performed |
|-----------------|---------|-----------------------|
| sales_gold_region | Total Revenue by Region | Grouped by Region, Sum of Total Revenue |
| sales_gold_product | Total Profit by Product | Grouped by Product (Item Type), Sum of Total Profit |
| sales_gold_country | Total Revenue by Country | Grouped by Country, Sum of Total Revenue |
