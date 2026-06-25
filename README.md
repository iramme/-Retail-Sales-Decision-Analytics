# 📊 Retail Sales Decision Analytics — Power BI

End-to-end Business Intelligence solution analyzing 99K+ retail transactions 
across 10 Istanbul shopping malls (2021–2023)

---

## 📌 Project Overview

This project delivers a complete BI solution covering the full data lifecycle:
data modeling, ETL pipeline, interactive dashboards, predictive forecasting,
and automated report delivery.

**Dataset :** Customer Shopping Dataset — Kaggle  
**Period :** January 2021 – March 2023  
**Volume :** 99,457 transactions · 10 malls · Istanbul, Turkey

---

## 🏆 Key Insights

| Metric | Value |
|--------|-------|
| Total Revenue | 251.51M |
| Total Transactions | 99K |
| Top Category | Clothing (114M revenue) |
| Top Mall | Mall of Istanbul |
| Dominant Payment | Credit Card (44.69%) |
| Top Customer Segment | 55+ years old (72M revenue) |
| Female Transactions | 59.81% |

---

## 🗄️ Data Warehouse Architecture

Star Schema with 1 fact table and 5 dimensions : 
**Grain :** One row = one transaction · one customer · one category · one date · one mall · one payment

---

## ⚙️ ETL Pipeline — Power Query (M Language)

### Extraction
- Source : CSV file imported via Power BI Desktop
- Power Query editor opened before loading for upstream transformations

### Transformation
- Column quality check (null values, errors)
- Type corrections : age/quantity → integer, price → decimal, invoice_date → date
- Date reconstruction from text format M/D/YYYY
- Dimension tables created by duplication + deduplication + surrogate key index
- Age_Group column added to Dim_Client (18–24, 25–34, 35–44, 45–54, 55+)
- Fact_Sales built via Left Outer Join with each dimension

### Loading
- 6 tables loaded into Power BI internal model
- Many-to-One relationships configured manually in Model view

---

## 📐 DAX Measures

| Measure | Formula |
|---------|---------|
| Total Revenue | SUMX(Fact_Sales, quantity * price) |
| Total Transactions | COUNTROWS(Fact_Sales) |
| Total Quantity | SUM(Fact_Sales[quantity]) |
| Avg Transaction Value | DIVIDE([Total Revenue], [Total Transactions]) |
| Avg Customer Age | AVERAGE(Dim_Client[age]) |

---

## 📈 Dashboards

### Page 1 — Sales Overview
- Total Revenue, Transactions, Quantity, Avg Transaction Value (KPI cards)
- Revenue by category (bar chart)
- Revenue by mall (bar chart)
- Revenue by Year/Quarter/Month (line chart + forecast)
- Transactions by payment method (pie chart)
- Transactions by gender (pie chart)

### Page 2 — Customer & Product Analysis
- Revenue by Age Group (bar chart)
- Total Quantity by category (bar chart)
- Revenue by mall × category (matrix)
- Transactions by category × gender (stacked bar)

**Slicers :** Year · Category · Gender · Mall · Payment Method

---

## 🔮 Predictive Analytics

- **Tool :** Power BI Analytics — Forecast
- **Algorithm :** Exponential Smoothing
- **Forecast length :** 3 months
- **Confidence interval :** 95%
- **Target variable :** Monthly Total Revenue

---

## 🤖 Automation

Power BI Service subscription configured for automated daily report delivery :
- **Frequency :** Daily at 10:00 AM UTC
- **Recipients :** Project team + supervisor

---

## 🛠️ Tech Stack

- Microsoft Power BI Desktop & Service
- Power Query (M Language)
- DAX (Data Analysis Expressions)
- Star Schema / Data Warehouse
- Kaggle (data source)

---


