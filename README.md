# DataCo Supply Chain & Fraud Diagnostics

## The Business Problem
Global supply chains suffer significant revenue leakage due to two primary blind spots: undetected fulfillment bottlenecks and unmonitored transaction fraud. This project analyzes the DataCo Smart Supply Chain dataset to pinpoint exactly where orders are delayed and to quantify the financial impact of fraudulent transactions. 

Rather than just building a dashboard, I treated this as a full data engineering project mapping the physical supply chain workflow, transforming a heavy 50 column flat file into a normalized database schema, and building a DAX powered analytical engine to serve the front-end visuals.

## Technical Architecture

* **Process Engineering (BPMN):** Mapped the physical supply chain lifecycle using Camunda BPMN to identify the exact decision gateways where an order either diverges into a "Late Delivery" bottleneck or triggers a "Suspected Fraud" status.
* **ETL Pipeline (Power Query):** Extracted the raw CSV and optimized the data for Excel's memory limits. Stripped out redundant descriptive columns and split the flat file into a true Star Schema structure (one central `Fact_Orders` table and multiple dimension tables).
* **Data Modeling (Power Pivot):** Linked the primary and foreign keys in Excel's Data Model to create a relational database environment.
* **DAX Engine:** Replaced standard grid formulas with scalable DAX measures to calculate dynamic KPIs, such as `Average Fulfillment Delay` and `Total Revenue Lost to Fraud`.

## Dashboard Application (Front-End)
The final deliverable is a multi-view, interactive application built entirely within Excel, utilizing hidden calculation sheets and linked shape navigation.

1. **Executive Summary:** A macro view of global sales, profit margins, and total revenue leakage, featuring a dynamic waterfall chart bridging gross sales down to net profit.
2. **Logistics Diagnostics:** Tracks fulfillment efficiency, correlating specific shipping modes with average delay days and mapping order volume across late delivery risks.
3. **Fraud Control Center:** A targeted risk dashboard. 

## Key Business Insights
* **The Wire Transfer Vulnerability:** The data analysis revealed a critical security flaw in the payment infrastructure. 100% of all suspected fraud cases (4,062 total transactions costing $825,935 in lost revenue) were executed via Wire Transfer. No fraud was detected across Debit, Credit, or Cash payments.
* **Logistics Bottlenecks:** Standard Class shipping consistently experiences the highest variance between scheduled delivery days and actual real delivery days, heavily impacting the overall late delivery rate.

## Files in this Repository
* `DataCo-Study-Case.xlsx` - The final interactive dashboard application (download to test slicers and navigation).
* `ERD.png` - The Entity-Relationship Diagram detailing the Star Schema structure.
* `BPMN.png` - The business logic workflow map.
* `Screenshots/` - High-resolution captures of the three dashboard views.
