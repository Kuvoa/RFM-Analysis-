# RFM Customer Segmentation Analysis

## Project Overview

This project applies RFM (Recency, Frequency, Monetary) analysis to segment customers based on their purchasing behavior. Using SQL in BigQuery for data preparation and Power BI for visualization, I identified high-value, at-risk, and inactive customers. These insights support targeted marketing, personalized retention strategies, and overall business growth.

## Objectives

- Calculate RFM metrics using transactional data  
- Assign quantile-based scores to Recency, Frequency, and Monetary values  
- Segment customers into behavioral categories based on RFM scores  
- Visualize segment performance using Power BI  
- Deliver actionable insights to improve engagement and retention

## What is RFM Analysis?

RFM Analysis is a widely used customer segmentation technique that evaluates:

- **Recency** – How recently a customer made a purchase  
- **Frequency** – How often a customer makes purchases  
- **Monetary** – How much money a customer has spent  

Each metric is scored individually on a 1–4 scale, and the combined RFM score (ranging from 3 to 12) is used to classify customers into segments.

## Example Customer Segments

- **Loyal Champions** – Recent, frequent, and high-spending customers  
- **Potentially Loyal** – Strong spending/frequency, but less recent activity  
- **Needing Attention** – Moderate engagement, may be drifting  
- **Can’t Lose** – Previously high-value but currently inactive  
- **Lost** – Infrequent, low-value, and inactive customers

## Tools Used

- **SQL (BigQuery)** – for cleaning, transforming, and scoring data  
- **Power BI** – for visual exploration of customer segments and behavior patterns

---

## SQL Breakdown

### Step 1: Filter and Aggregate Transactions

Filtered valid transactions from December 2010 to December 2011, removing null or negative values.

### Step 2: Calculate RFM Metrics

- **Recency**: Days between the last purchase date and a fixed reference date  
- **Frequency**: Count of unique purchase dates per customer  
- **Monetary**: Total purchase value per customer

### Step 3: Assign Quantile-Based Scores

Used `APPROX_QUANTILES()` in BigQuery to assign scores from 1 to 4 for each metric based on distribution:

```sql
APPROX_QUANTILES(Recency, 4)
APPROX_QUANTILES(Frequency, 4)
APPROX_QUANTILES(Monetary, 4)
