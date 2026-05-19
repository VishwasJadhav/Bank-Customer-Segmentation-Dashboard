# Bank Customer Segmentation & Risk Analytics Dashboard

## Project Overview

This project presents a comprehensive Banking Customer Segmentation and Risk Analytics Dashboard developed in Power BI. The dashboard analyzes customer behaviour, transaction activity, revenue contribution, credit risk, and customer engagement patterns to help banks improve customer retention, identify high-value customers, and monitor revenue exposure across different risk profiles.

The project combines:
- Customer Segmentation (RFM Analysis)
- Risk Profiling
- Revenue Analytics
- Customer Behaviour Analysis
- Transaction Pattern Analysis
- Retention & Churn Monitoring

---

# Dashboard Preview

## Executive Overview

![Executive Overview](https://github.com/VishwasJadhav/Bank-Customer-Segmentation-And-Risk-Analytics-Dashboard/blob/main/Dashboard/Page%201%20-%20Executive%20Overview.png)

---

## Customer Analysis

![Customer Analysis](https://github.com/VishwasJadhav/Bank-Customer-Segmentation-And-Risk-Analytics-Dashboard/blob/main/Dashboard/Page%202%20-%20Customer%20Analysis.png)

---

## Customer Segmentation Analysis

![Customer Segmentation](https://github.com/VishwasJadhav/Bank-Customer-Segmentation-And-Risk-Analytics-Dashboard/blob/main/Dashboard/Page%203%20-%20Customer%20Segmentation.png)

---

## Risk & Revenue Analysis

![Risk & Revenue](https://github.com/VishwasJadhav/Bank-Customer-Segmentation-And-Risk-Analytics-Dashboard/blob/main/Dashboard/Page%204%20-%20Risk%20and%20Revenue.png)

---

# Business Problem

Banks generate massive volumes of customer transaction data, but identifying meaningful customer patterns and risk exposure remains a major challenge.

This dashboard helps answer critical business questions such as:

- Which customers generate the highest revenue?
- Which customer groups are most likely to churn?
- Which risk segments contribute the most revenue?
- How do transaction behaviours vary across customer groups?
- Which customer segments require targeted retention strategies?
- How does customer engagement vary across demographics and time periods?

The goal of this project is to transform raw banking transaction data into actionable business intelligence.

---

# Objectives

- Segment customers using RFM methodology
- Identify high-value and high-risk customer groups
- Analyze revenue contribution across customer segments
- Monitor customer retention and churn indicators
- Track transaction behaviour patterns
- Evaluate revenue exposure by risk profile

---

# Dataset Information

The dataset contains banking customer transaction and account information, including:

- Customer demographics
- Transactions
- Account balances
- Customer locations
- Transaction timestamps

### Dataset Scale
- Total Transactions: 868363
- Analysis Period: Aug 2016 – Oct 2016

---

# Data Cleaning & Preprocessing

The raw banking dataset required multiple preprocessing and transformation steps before analysis.

The following data cleaning operations were performed using Power Query and DAX:

- Handled missing and null values
- Standardized categorical fields
- Corrected inconsistent text formatting
- Converted date columns into proper datetime format
- Created custom age group categories from date of birth
- Derived transaction time buckets
- Generated calculated columns for RFM analysis
- Validated customer transaction records
- Optimized data types for efficient modeling

Additional feature engineering steps included:
- Credit score categorization
- Risk profile classification
- Revenue calculations
- Customer retention indicators
- Churn-risk identification

---

# Tools & Technologies Used

## Power BI
Used for:
- Dashboard development
- Data modeling
- Interactive visualizations
- KPI reporting

## DAX (Data Analysis Expressions)
Used for:
- RFM calculations
- Risk classification
- Revenue measures
- Retention calculations
- Custom KPIs

## Power Query
Used for:
- Data cleaning
- Data transformation
- Feature engineering

## Excel / CSV
Used as source datasets.

---

# Dashboard Pages

# 1. Executive Overview

Provides a high-level business summary including:
- Total Customers
- Revenue Trends
- Retention Rate
- Churn Risk Customers
- Risk Distribution
- Segment Distribution
- Average Transaction Metrics

### Key Insights
- Revenue declines sharply during October.
- Medium-risk customers contribute the largest customer share.
- Customer engagement remains relatively low.
- Core Customers dominate the customer base.

---

# 2. Customer Analysis

Analyzes customer demographics and behavioural patterns.

### Includes:
- Age Group Analysis
- Customer Location Analysis
- Transaction Timing Analysis
- Weekend Transaction Trends
- Peak Activity Period
- Day vs Time Heatmap

### Key Insights
- Evening transactions are highest across all days.
- Most customers belong to the 26–45 age group.
- Mumbai and Delhi contain the largest customer populations.
- Weekend transactions account for approximately 30% of activity.

---

# 3. Customer Segmentation Analysis

Implements RFM-based customer segmentation.

### Segments Included
- Champions
- Loyal Customers
- Core Customers
- New Customers
- Dormant Customers
- At Risk Customers

### Analysis Includes
- Revenue per Customer by Segment
- Segment Distribution
- Recency vs Frequency Matrix
- Segment-wise Age Distribution

### Key Insights
- Champions generate the highest revenue per customer.
- At-Risk customers still contribute significant revenue.
- Core Customers represent the largest customer segment.
- Dormant Customers have minimal revenue contribution.

---

# 4. Risk & Revenue Analysis

Focuses on customer credit quality and revenue exposure.

### Includes
- Credit Score Analysis
- Revenue Exposure by Risk Profile
- Risk Intelligence Summary
- Credit Category Distribution
- High-Risk Revenue Exposure by Segment

### Key Insights
- Medium and High-Risk customers account for most revenue exposure.
- High-Risk customers have significantly lower average credit scores.
- Core Customers contribute the highest high-risk revenue exposure.
- Poor credit category customers represent a major customer share.

---

# RFM Segmentation Methodology

Customers were segmented using RFM analysis:

## Recency (R)
Measures how recently a customer made a transaction.

## Frequency (F)
Measures how often a customer performs transactions.

## Monetary (M)
Measures customer revenue contribution.

---

# Customer Segment Definitions

| Segment | Description |
|---|---|
| Champions | Highly engaged, high-value customers |
| Loyal Customers | Frequent and valuable customers |
| Core Customers | Stable and consistent customers |
| New Customers | Recently acquired customers |
| Dormant Customers | Low engagement customers |
| At Risk | Previously valuable customers with declining activity |

---

# Risk Scoring Methodology

## Objective

Since the dataset did not contain actual actual credit-bureau variables such as
repayment history, loan defaults, debt obligations, and credit inquiry data,
a simulated behavioural credit scoring framework was developed using
customer financial and transaction-based indicators.

---

## Scoring Factors

| Factor | Weight | Purpose |
|---|---|---|
| Balance Score | 40% | Financial stability |
| Utilization Score | 35% | Credit usage behaviour |
| Activity Score | 10% | Transaction engagement |
| Age Score | 15% | Customer stability proxy |

---

## DAX Formula

```DAX
Weighted Score =
(
'Customer Summary'[Balance Score] * 0.40 +
'Customer Summary'[Utilization Score] * 0.35 +
'Customer Summary'[Activity Score] * 0.10 +
'Customer Summary'[Age Score] * 0.15
)

Then customers were classified into:
- Low Risk
- Medium Risk
- High Risk

---

# Important KPIs

| KPI | Value |
|---|---|
| Total Customers | 753K |
| Total Revenue | 1.09B INR |
| Retained Customers | 70.55% |
| Churn Risk Customers | 20.38% |
| Avg Credit Score | 623.58 |
| High Risk Customers | 34.8% |

---

# Key Business Insights

## Revenue Insights
- Medium-risk customers contribute the highest revenue share.
- Revenue trends indicate a sharp decline during October.

## Customer Insights
- Core Customers dominate overall customer distribution.
- Champions contribute the highest revenue per customer.

## Risk Insights
- High-risk customers contribute substantial revenue despite poor credit quality.
- Revenue exposure remains concentrated among Medium and High-Risk customers.

## Behavioural Insights
- Evening periods show the highest transaction activity.
- Customers aged 26–45 form the primary customer base.

---

# Data Modeling

A star schema data model was implemented to optimize reporting performance and analytical flexibility.

The model included:
- Fact tables for transaction analysis
- Dimension tables for customer attributes
- Date-based relationships for time intelligence
- Calculated measures using DAX
- Interactive slicers and cross-filtering

The data model was optimized for:
- Fast KPI calculations
- Dynamic filtering
- Scalable dashboard interactions

---

# Features

- Interactive filtering
- Dynamic KPIs
- Drill-down analysis
- Time-based trend analysis
- Heatmaps
- Risk intelligence reporting
- Executive storytelling layout

---

# Challenges Faced

Some key challenges encountered during the project included:

- Handling large customer volumes efficiently
- Creating meaningful RFM segmentation thresholds
- Managing inconsistent transaction patterns
- Balancing dashboard performance with visual complexity
- Designing a professional banking-focused UI
- Ensuring consistent filtering across multiple report pages

These challenges were addressed using optimized DAX measures, Power Query transformations, and efficient dashboard design practices.

---

# Future Improvements

- Predictive churn modeling
- Machine learning-based customer scoring
- Real-time streaming dashboards
- Advanced anomaly detection
- Customer lifetime value prediction
- Drill-through customer intelligence pages

---

# Conclusion

This project demonstrates how banking transaction data can be transformed into actionable business intelligence using Power BI, DAX, and data modeling techniques.

The dashboard provides a complete analytical view of:

- Customer behaviour
- Revenue performance
- Risk exposure
- Segmentation strategy
- Retention monitoring

It is designed to support data-driven decision-making for banking and financial analytics use cases.

---
