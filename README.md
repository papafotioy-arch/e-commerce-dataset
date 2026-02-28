# ecommerce-bigquery-cleaning
BigQuery pipeline that merges and cleans three raw e‑commerce sheets using modular SQL. Covers type casting, normalization, email and country cleaning, and deduplication. Includes a short exploratory analysis highlighting order patterns and channel insights
# Project Overview
This project showcases an end‑to‑end data cleaning workflow using Google BigQuery to transform three raw e‑commerce order sheets into a unified, analysis‑ready dataset. The raw files contain realistic data issues such as inconsistent formatting, invalid emails, mixed date formats, currency symbols, negative values, and duplicate records. The goal is to demonstrate a clear, reproducible, and well‑documented SQL pipeline suitable for analytics, KPI reporting, and BI dashboards.
The workflow follows a structured data‑engineering approach: ingesting raw files, combining them into a staging layer, standardizing fields, cleaning data types, normalizing categories, validating records, removing duplicates, and exporting a final cleaned dataset. All transformations are implemented using modular SQL scripts, and the repository includes documentation, a data dictionary, and a cleaning log.

## Data Cleaning Pipeline
The cleaning process is organized into sequential SQL steps:
- Combine raw sheets into a unified staging table.
- Standardize column names using consistent snake_case formatting.
- Fix data types for dates, prices, quantities, booleans, and ages.
- Clean and validate emails, removing invalid characters and flagging incorrect formats.
- Normalize country values (e.g., GB, U.K., United Kingdom → UK).
- Standardize categorical fields such as order status and marketing channel.
- Remove duplicates and null values, standardise negative numbers, using business‑logic keys.
- Export the cleaned dataset for analysis.
The final output is cleaned_orders.csv, ready for dashboards or further modeling.

## Exploratory Analysis
A brief exploratory analysis was performed on the cleaned dataset to validate data quality and extract initial insights:
- Order volume shows consistent activity across the dataset, with no missing date clusters after cleaning.
- Marketing channels reveal Instagram and Email as the most frequent acquisition sources.
- Product categories such as Footwear and Accessories appear most often, indicating strong representation in the sample.
- Customer behavior shows a mix of first‑time and returning customers, with returning customers contributing a meaningful share of completed orders.
- Order status distribution highlights a realistic mix of Completed, Pending, Cancelled, and Refunded transactions.
These checks confirm that the cleaned dataset is stable, consistent, and suitable for downstream analytics.


## Repository Structure

```
e-commerce-dataset/
│
├── data/
│   ├── power_query_relay_dataset1.csv
│   ├── power_query_relay_dataset2.csv
│   ├── power_query_relay_dataset3.csv
│   └── cleaned_orders.csv
│
├── sql/
│   ├── 01_combine_tables.sql
│   ├── 02_standardize_columns.sql
│   ├── 03_clean_types.sql
│   ├── 04_clean_emails.sql
│   ├── 05_clean_country.sql
│   ├── 06_clean_status.sql
│   ├── 07_product_category_fix.sql
│   ├── 08_remove_duplicates.sql
│   └── 08_export
│
├── docs/
│   ├── README.md
│   ├── data_dictionary.md
│   └── cleaning_log.md
│
└── notebooks/
    └── bigquery_analysis.ipynb
```
