# Inventory Management, Cancellation Exposure & Operational Demand Analysis

![Power BI Dashboard](PowerBI%20Executive%20Dashboard.png)

## Overview

This project explores how cancelled orders affect revenue quality, profit visibility, stock allocation, and warehouse pressure within an inventory management environment.

Using a public inventory management dataset from Kaggle, the project was built as a SQL-based reporting workflow using PostgreSQL and Power BI. The aim was to move beyond a simple sales dashboard and examine where operational demand does not fully convert into shipped revenue.

The project demonstrates a more realistic reporting architecture:

CSV files → PostgreSQL staging schema → SQL reporting views → Power BI dashboards → executive case study

The analysis was designed as a practical business intelligence and operational reporting case study suitable for:

* SME operations environments,
* warehouse and inventory reporting,
* finance and revenue-quality analysis,
* ERP / SAP-style reporting demonstrations,
* PostgreSQL and Power BI portfolio work,
* and operational improvement discussions.

---

# The Problem

Headline order value can give a misleading view of business performance when cancelled orders are not separated from actual shipped activity.

In this dataset, total ordered revenue reached approximately:

* £79.0M ordered revenue
* £50.2M actual revenue
* 36.4% cancelled revenue exposure
* £7.03M projected profit
* £5.01M actual profit
* 28.8% cancelled profit exposure

The operational issue goes beyond finance.

Approximately 35K units were ordered, but around 9K units were linked to cancelled orders. This means roughly 25.7% of ordered stock quantity did not convert into shipped activity.

This reflects a common operational reporting challenge:

> Ordered demand is not the same as realised value.

Cancelled orders can still create cost, warehouse pressure, procurement activity, administrative work, and planning noise before the value disappears from the business.

---

# The Approach

The project used a multi-table inventory management dataset containing:

* customers,
* orders,
* order details,
* products,
* employees,
* warehouses,
* and regions.

The source CSV files were imported into PostgreSQL using a structured staging schema. Reporting views were then created to prepare clean, Power BI-ready datasets.

The analysis focused on:

* ordered vs actual revenue,
* cancelled revenue exposure,
* ordered vs actual profit,
* cancelled profit exposure,
* actual vs cancelled quantity,
* product-category demand,
* high-value order exceptions,
* and data limitations affecting warehouse and regional analysis.

The Power BI report was intentionally split into stakeholder-focused pages:

* Management overview
* Finance view
* Warehouse view
* Executive case study summary

This allowed the same dataset to support different operational questions without overloading one dashboard page.

---

# The Solution

The reporting environment combines PostgreSQL and Power BI to create a practical operational BI workflow.

## PostgreSQL Layer

The PostgreSQL database was structured with:

* a `staging` schema for raw imported CSV tables,
* a `reporting` schema for cleaned and joined reporting views,
* primary and foreign key relationships where supported by the dataset,
* adjusted data types for business identifiers and financial values,
* and reporting logic for cancelled vs actual order activity.

Key reporting views included:

* `reporting.vw_orders_enriched`
* `reporting.vw_product_performance`
* `reporting.vw_customer_order_summary`
* `reporting.vw_product_demand_summary`
* `reporting.vw_monthly_order_trend`
* `reporting.vw_warehouse_location_reference`

The reporting views separate:

* total ordered values,
* cancelled values,
* and actual commercial values.

This made it possible to analyse cancellations without deleting them from the dataset.

## Power BI Layer

The Power BI report includes:

## Management Dashboard

Focused on overall business visibility:

* total ordered revenue,
* actual revenue,
* percentage revenue cancelled,
* total ordered profit,
* actual profit,
* percentage profit cancelled,
* and order status split.

## Finance Dashboard

Focused on financial exposure and order-level concentration:

* revenue and profit over time,
* high-value order exceptions,
* customer-level order value,
* order status impact,
* and cancellation-related revenue distortion.

## Warehouse Dashboard

Focused on operational demand and stock movement:

* actual quantity ordered,
* cancelled quantity,
* actual vs cancelled quantity by product category,
* average quantity trends,
* and category-level stock exposure.

## Executive Case Study

A two-page PDF-style summary was created to show how the findings could be presented in a weekly management report.

---

# Dashboard Highlights

Key findings from the analysis included:

* £79.0M total ordered revenue
* £50.2M actual revenue
* 36.4% cancelled revenue exposure
* £7.03M total projected profit
* £5.01M actual profit
* 28.8% cancelled profit exposure
* approximately 35K total ordered quantity
* approximately 9K cancelled quantity
* roughly 25.7% of ordered quantity not shipped

Product-category analysis showed that cancellation exposure was not evenly distributed. Some categories generated substantial actual demand while also carrying meaningful cancellation value.

The analysis demonstrated that:

* headline revenue can overstate operational performance,
* cancellations affect warehouse and procurement activity as well as finance,
* quantity-based reporting and value-based reporting tell different parts of the story,
* and better data integration would improve regional and warehouse-level insight.

---

# Operational Recommendations

The analysis led to five practical recommendations:

## 1. Introduce Cancellation Exposure Monitoring

Track cancellation percentages across revenue, profit, and quantity metrics. This should be reviewed by product category and over time to identify where ordered demand is not reliably converting into shipped activity.

## 2. Review Stock Allocation and Procurement Strategy

Where cancelled order quantity is consistently high, review purchasing thresholds, stock holding policies, and order validation controls. Stock allocated to unstable demand consumes warehouse space and may create avoidable cost.

## 3. Develop Exception-Based Operational Reporting

Introduce monitoring for unusually large orders, quantity spikes, and high-value cancellations. These exceptions can materially distort reporting totals and create operational planning risk.

## 4. Improve Warehouse and Regional Data Integration

The dataset included warehouse and regional information, but order lines were not directly linked to warehouse fulfilment locations. Customer address data was also not cleanly linkable to warehouse regions.

Improving these data relationships would allow the business to analyse:

* cancellation exposure by region,
* fulfilment performance by warehouse,
* customer demand patterns by location,
* and potential distribution capacity gaps.

## 5. Use Demand Trends to Support Capacity Planning

If customer demand increases consistently in certain geographic areas, this could support decisions around additional warehouse locations, revised fulfilment routes, or regional stock allocation.

Better regional visibility would allow operational growth decisions to be based on evidence rather than reactive expansion.

---

# Demo

The repository includes:

* PostgreSQL table setup scripts
* SQL reporting view scripts
* Power BI dashboard screenshots
* executive case study PDF
* dashboard PDF export
* source dataset notes
* and operational recommendations

Suggested walkthrough order:

1. Review the database structure
2. Review the staging and reporting schemas
3. Open the SQL reporting views
4. Open the Power BI report
5. Review the Management dashboard
6. Review the Finance dashboard
7. Review the Warehouse dashboard
8. Read the executive case study summary

---

# How to Run

## Requirements

* PostgreSQL
* pgAdmin or psql
* Power BI Desktop
* CSV source files from the Kaggle dataset

## Steps

1. Download or clone the repository

```bash
git clone <repository-url>
