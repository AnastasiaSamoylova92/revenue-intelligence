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

This makes it difficult to answer seemingly simple questions such as:

- Are we growing profitably?
- Which markets are driving performance?
- Is growth driven by price, volume, or mix?
- Which products are creating or destroying margin?
- How reliable are our forecasts?
- Which forecast version performs best?
- Which customers are expanding or churning?
- Which commercial issues require management attention?

The Revenue Intelligence Platform consolidates these perspectives into one analytical model and converts them into actionable KPIs, variance analyses and management dashboards.

## Business Objectives
The platform helps answer key management questions:

- How is revenue performing versus prior year and forecast?
- Which products, customers, segments and regions drive growth?
- What drives changes in gross margin?
- How accurate are Budget, Rolling Forecast, and Latest Estimate?
- Which customers are growing, retained, or churning?
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
  
## Business Context
The synthetic dataset simulates a global B2B company operating across:

- Multiple countries and regions
- Multiple customer segments
- Multiple product families
- Multiple currencies
- Multiple fiscal years

The generated data includes realistic business dynamics such as:

- Revenue growth and decline
- Forecast inaccuracies
- Customer churn
- Product mix shifts
- Margin variation
- Regional performance differences
- Inventory fluctuations
- CRM activity tracking
- Product returns

## Technology Stack

| Technology                     | Purpose                                  |
|--------------------------------|------------------------------------------|
| Python                         | Synthetic data generation                |
| Pandas & NumPy                 | Data simulation and transformation       |
| SQL Server Management Studio   | Database development                     |
| SQL                            | Data modeling and transformation         |
| Power BI                       | Analytics and dashboarding               |
| DAX                            | Business logic and KPI calculations      |
| Git & GitHub                   | Version control and portfolio presentation |


## Project Architecture

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

### Dataset Characteristics
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
Provides a high-level summary of business performance and serves as the executive landing page.

#### Key KPIs
- Revenue
- Gross Margin %
- Forecast Accuracy
- Active Customers
- Revenue at Risk
- Net Revenue Retention (NRR)

#### Focus Areas
- Business Performance
- Executive Health Score
- Revenue Growth Drivers
- Regional Performance
- Product Performance
- Forecast Reliability

![Executive Overview](images/executive_overview.png)

### 2. Revenue Analysis
Analyzes revenue performance and identifies growth drivers.

#### Focus Areas
- Revenue Growth
- Customer Contribution
- Product Contribution
- Revenue Drivers
- Revenue Retention

#### Key Analytics
- Revenue Trend Analysis
- Price-Volume-Mix Analysis
- Customer Segment Analysis
- Product Portfolio Analysis

![Revenue Analysis](images/revenue_analysis.png)

### 3. Gross Margin Analysis
Evaluates profitability and pricing effectiveness.

#### Focus Areas
- Gross Profit
- Gross Margin %
- Average Selling Price (ASP)
- Margin Drivers
- Discount Analysis
- Product Profitability

#### Key Analytics
- Margin Waterfall Analysis
- Pricing Power Assessment
- Margin Risk Detection

![Margin Analysis](images/margin_analysis.png)

### 4. Forecasting Analysis
Measures forecast quality and planning effectiveness.

#### Focus Areas
- Forecast Accuracy
- Forecast Variance
- Forecast Achievement
- Variance Drivers
- Rolling Forecast Outlook

#### Key Analytics
- Price Variance
- Volume Variance
- Forecast Driver Analysis

![Forecasting Analysis](images/forecasting_analysis.png)

### 5. Customer Analytics
Provides insights into customer health, retention, and growth.

#### Focus Areas
- Active Customers
- New Customers
- Churn Customers
- Customer Retention
- Revenue Concentration

#### Key Analytics
- Churn Risk Segmentation
- Revenue Contribution Analysis
- Revenue at Risk Monitoring

![Customer Analytics](images/customer_analytics.png)

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

## Key Learnings
Throughout this project I gained practical experience in:

- Designing an enterprise-style data warehouse
- Building a scalable Power BI semantic model
- Developing advanced DAX measures and KPI frameworks
- Simulating realistic business scenarios using Python
- Creating executive-ready dashboards focused on decision support


## Author

Anastasia Samoylova
M.Sc. | BI & Data Analytics | ML
