# Retail Sales Analysis

## Overview

Retail Sales Analysis is an end-to-end Business Intelligence project built with Microsoft Power BI to analyze retail sales performance across **Germany**, **the Czech Republic**, and **Denmark** for fiscal years **2014–2017**.

The project demonstrates the complete analytics workflow, including data extraction from multiple heterogeneous data sources, data transformation using Power Query, dimensional data modeling, DAX calculations, and the development of an interactive dashboard for business decision-making.

---

## Project Objective

The objective of this project is to consolidate sales and reference data from multiple disconnected sources into a single analytical model that enables stakeholders to monitor business performance and make data-driven decisions.

The project focuses on:

- Integrating multiple data sources into one model
- Building a scalable ETL pipeline
- Creating a clean dimensional model
- Performing revenue and profitability analysis
- Developing interactive dashboards
- Generating actionable business insights

---

## Business Questions

The dashboard answers the following business questions:

| Business Area | Question |
|--------------|----------|
| Revenue Growth | How has revenue changed over time? |
| Market Performance | Which countries contribute the most revenue and profit? |
| Product Analysis | Which product categories generate the highest margins? |
| Sales Performance | Which sales representatives perform best? |
| Pricing Analysis | Which price ranges contribute the highest profitability? |

---

## Project Summary

| Metric | Value |
|--------|------:|
| Total Revenue | $126.01M |
| Total Cost | $39.13M |
| Gross Profit | $86.89M |
| Gross Profit Margin | 68.95% |
| Markets | Germany, Czech Republic, Denmark |
| Reporting Period | FY2014–FY2017 |

---

## Technologies

- Microsoft Power BI
- Power Query (M)
- DAX
- PostgreSQL
- SQL
- Excel
- CSV
- Web Data Extraction

---

## Data Sources

| Dataset | Source | Connection Method |
|---------|--------|-------------------|
| FactSales | CSV Files | Folder Connector |
| DimProducts | PostgreSQL | PostgreSQL.Database |
| DimGeography | Web Table | Web Connector |
| DimCategory | Excel | Excel Workbook |
| DimSubCategory | Excel | Excel Workbook |
| DimSalesRep | Excel | Excel Workbook |

The sales data is imported dynamically from a folder, allowing new yearly CSV files to be added without modifying the Power Query pipeline.

---

## Data Transformation

Power Query was used to prepare all datasets before loading them into the model.

Major transformation tasks included:

- Removing duplicate records
- Renaming columns
- Converting data types
- Splitting composite columns
- Cleaning inconsistent values
- Creating surrogate keys
- Merging lookup tables
- Building a refresh-ready ETL process

---

## Data Model

The solution follows a hybrid Star and Snowflake Schema.

### Fact Table

- FactSales

### Dimension Tables

- DimProducts
- DimCategory
- DimSubCategory
- DimSalesRep
- DimGeography
- CalendarMaster

Relationships are configured using one-to-many relationships with single-direction filtering to support efficient analytical queries.

---

## Calendar Table

A dedicated calendar table was created using DAX.

```DAX
CalendarMaster =
CALENDAR(
    MIN(FactSales[Date]),
    MAX(FactSales[Date])
)
```

Additional columns include:

- Year
- Quarter
- Month
- Month Name
- Week Number
- Weekday
- Month-Year
- Quarter-Year
- Sorting Columns

This enables Month-over-Month and Quarter-over-Quarter analysis.

---

## Calculations

### Calculated Columns

FactSales

- Total Revenue
- Total Cost
- Gross Profit

DimProducts

- Price Range

### Measures

- Total Revenue
- Total Cost
- Total Gross Profit
- Gross Profit Margin %
- Revenue per Unit
- Average Discount
- Total Transactions
- Previous Month Profit
- Previous Quarter Profit
- Month-over-Month Growth
- Quarter-over-Quarter Growth

---

## Dashboard Pages

1. Introduction
2. Executive Summary
3. Revenue Analysis
4. Month-over-Month & Quarter-over-Quarter Growth
5. Sales Representative Performance
6. Country & Town Performance
7. Category Analysis
8. Price Range Analysis
9. Business Recommendations

---

## Key Insights

- Germany generated the highest revenue and profit across all markets.
- The Special product category contributed the largest share of gross profit.
- Medium-value products achieved the best balance between sales volume and profitability.
- A small number of sales representatives generated a significant portion of company revenue.

---

## Recommendations

- Expand successful business strategies from Germany into other markets.
- Increase focus on medium-value products with strong profit margins.
- Use trend analysis for forecasting and inventory planning.
- Share best practices from top-performing sales representatives across teams.

---

## Repository Structure

```text
Retail_Sales_Analysis_Power_BI/
│
├── README.md
├── business-questions/
├── conclusion/
├── data/
├── data-model/
├── outputs/
└── report/
```

---

## Getting Started

1. Install Microsoft Power BI Desktop.
2. Clone the repository.

```bash
git clone https://github.com/deadlineZeus/Retail_Sales_Analysis_Power_BI.git
```

3. Open:

```text
report/RetailSalesAnalysis.pbix
```

4. Update local data source paths if required.
5. Refresh the dataset.

---

## Features

- Interactive Power BI dashboard
- Dynamic folder-based data ingestion
- PostgreSQL integration
- Web data extraction
- Power Query ETL
- Star and Snowflake schema
- DAX measures
- Time intelligence
- KPI reporting
- Business performance analysis

---

## Future Improvements

- Incremental Refresh
- Row-Level Security
- Power BI Service Deployment
- Azure SQL Integration
- Forecasting Models
- Mobile Layout Optimization

---

## License

This project is provided for educational and portfolio purposes.

---

Developed by **Aaryan Arora**
