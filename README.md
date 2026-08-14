# Revenue Intelligence Platform

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![SQL Server](https://img.shields.io/badge/SQL%20Server-Data%20Layer-CC2927?logo=microsoftsqlserver&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Decision%20Support-F2C811?logo=powerbi&logoColor=black)

![Executive Overview](images/executive_overview.png)

End-to-end Business Intelligence and FP&A analytics platform built with Python, SQL Server and Power BI.

The project simulates the analytics environment of a global B2B company and demonstrates how transactional data can be transformed into management insights across revenue, profitability, forecasting, products, regions and customers.

## Business Problem

Management teams often receive information from multiple disconnected systems:

- ERP sales transactions
- Finance and cost data
- CRM activity
- Forecasting files
- Customer master data
- Product master data
- Inventory systems

This makes it difficult to really understand the business performancce. 

The Revenue Intelligence Platform consolidates these perspectives into one analytical model and converts them into actionable KPIs, variance analyses and management dashboards.

## Business Objectives
The platform helps answer key management questions:

- How is revenue performing versus prior year and forecast?
- Which products, customers, segments and regions drive growth?
- What drives changes in gross margin?
- How accurate are Budget, Rolling Forecast and Latest Estimate?
- Which customers are growing, retained or churning?
- Where should management focus attention?

## Key Capabilities
### Revenue & Commercial Analytics
- Revenue and YoY growth analysis
- Product, customer, segment and regional contribution
- Revenue movement analysis
- Price-Volume-Mix analysis

### Profitability 
- Gross Profit and Gross Margin
- Average Selling Price and Unit Cost
- Discount and margin leakage analysis
- Pricing opportunity identification
- Product portfolio profitability

### Forecasting
- Actual vs Budget / Rolling Forecast / Latest Estimate
- Forecast variance and accuracy
- Forecast bias and absolute error
- Regional forecast performance
- Forecast version comparison

### Customer Analytics
- Active, new and churned customers
- Customer retention
- Net Revenue Retention
- Customer health
- Cohort retention
- Segment performance

### Data Engineering & BI
- Synthetic enterprise data generation
- SQL Server data warehouse
- Raw / staging / curated architecture
- Star-schema modeling
- Power BI semantic model
- Advanced DAX measures

## Technology Stack

| Technology                     | Purpose                                  |
|--------------------------------|------------------------------------------|
| Python                         | Synthetic data generation                |
| Pandas & NumPy                 | Data simulation and transformation       |
| SQL Server Management Studio   | Database development                     |
| SQL                            | Data modeling and transformation         |
| Power BI                       | Analytics and dashboarding               |
| DAX                            | Business logic and KPI calculations      |
| GitHub                        | Version control and portfolio presentation |


## Repository Structure

```text
revenue-intelligence/
│
├── data/
│
├── notebooks/
│   └── generate_dataset.ipynb
│
├── sql/
│   ├── 01_raw/
│   ├── 02_staging/
│   ├── 03_curated/
│
├── dashboards/
│   └── Revenue_Intelligence_Dashboard.pbix
│
├── images/
│   └── executive_overview.png
│   └── revenue_analysis.png
│   └── margin_analysis.png
│   └── forecasting_analysis.png
│   └── customer_analytics.png
│
├── requirements.txt
├── README.md
└── .gitignore
```

## Data Warehouse Design
The project follows a layered enterprise data warehouse architecture.

```text
Python
 ↓
SQL Server
(raw → staging → curated)
 ↓
Power BI Semantic Model
 ↓
Executive Dashboards
```

### Schemas

| Schema    | Purpose                              |
|-----------|--------------------------------------|
| raw       | Source data ingestion                |
| staging   | Data cleansing and transformation    |
| curated   | Business-ready analytical tables     |

### Data Model

The solution follows a star-schema architecture optimized for analytical workloads.

#### Fact Tables

| Table              | Description                              |
|--------------------|------------------------------------------|
| factSales          | Transaction-level sales data             |
| factForecast       | Forecast versus actual performance       |
| factInventory      | Inventory movements                      |
| factCosts          | Product cost history                     |
| factCRMActivities  | Sales and CRM activities                 |
| factReturns        | Product returns                          |
| factPipeline       | Sales opportunities and pipeline         |

#### Dimension Tables

| Table         | Description                           |
|---------------|---------------------------------------|
| dimDate       | Calendar dimension                    |
| dimCustomer   | Customer master data                  |
| dimProduct    | Product hierarchy      |
| dimRegion     | Geography and currency data           |
| dimSalesRep   | Sales representative information      |

### Dataset
The dataset contains:

- 120.000 sales transactions
- Multi-year history
- Multi-currency simulation
- Revenue growth trends
- Forecast deviations
- Margin variability
- Missing values
- Outliers
- Customer churn behavior
- Enterprise and SMB customer dynamics

## Power BI reporting layer

### 1. Executive Overview

Executive landing page combining the most important commercial and financial indicators.

#### KPIs
- Revenue
- Gross Margin %
- Forecast Accuracy
- Active Customers
- Net Revenue Retention (NRR)

#### Analytics
- Revenue by country
- Revenue vs Prior Year and Forecast
- Regional Performance
- Product Performance
- Executive Health Score
- Decision Brief

![Executive Overview](images/executive_overview.png)

### 2. Revenue Analysis
Detailed analysis of revenue development and growth drivers.

#### KPIs
- Revenue
- Units
- Active Customers
- Revenue per Customer
- NRR

#### Analytics
- Revenue Trend & YoY Growth
- Revenue Movement
- Customer Segment Contribution
- Product Contribution
- Top Customer and Product Variations

![Revenue Analysis](images/revenue_analysis.png)

### 3.Margin & Profitability
Focuses on profitability, pricing and margin improvement opportunities.

#### KPIs
- Gross Profit
- Gross Margin
- ASP
- Margin per Unit
- Average Discount

#### Analytics
- Gross Margin Trend
- Price-Volume-Mix
- Portfolio Profitability
- Margin Leakage
- ASP vs Unit Cost
- Pricing Opportunities

![Margin Analysis](images/margin_analysis.png)

### 4. Forecasting 
Measures forecast quality and planning effectiveness.

#### KPIs
- Forecast Revenue
- Actual Revenue
- Forecast Variance
- Forecast Accuracy

#### Analytics
- Actual vs Forecast Versions
- Budget vs Rolling Forecast vs Latest Estimate
- Regional Forecast Accuracy
- Variance Drivers
- Monthly Error & Bias
- Version Comparison

![Forecasting Analysis](images/forecasting_analysis.png)

### 5. Customer Value & Retention
Analyzes customer acquisition, retention, churn, and value.

#### KPIs
- Active Customers
- New Customers
- Churned Customers
- Customer Retention
- NRR

#### Analytics
- Customer Movement
- Customer Value & Health
- Cohort Retention
- Segment Scorecard

![Customer Analytics](images/customer_analytics.png)

## Key Learnings
Throughout this project I gained practical experience in:

- Business Intelligence & dashboard design
- Financial and FP&A analytics
- Revenue and profitability analysis
- Forecast vs Actual analysis
- Forecast accuracy and variance analysis
- Price-Volume-Mix analysis
- Customer retention and cohort analysis
- SQL data warehousing
- Dimensional modeling
- Power BI semantic modeling
- Advanced DAX
- Python data generation and transformation

## Installation

Clone the repository:
```bash
git clone https://github.com/AnastasiaSamoylova92/revenue-intelligence.git
cd revenue-intelligence
```
Install dependencies:
```bash
pip install -r requirements.txt
```

## Author

Anastasia Samoylova
M.Sc. | BI & Data Analytics | Financial & Commercial Analytics | ML
