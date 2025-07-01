# 🧮 RFM Customer Segmentation Analysis

## 📘 Overview

This project applies **RFM (Recency, Frequency, Monetary)** analysis to segment customers based on purchasing behavior. Using SQL in BigQuery and Power BI for visualization, I identify high-value, at-risk, and disengaged customers to help drive personalized marketing strategies and improve retention.

---

## 🎯 Objectives

- Calculate RFM metrics using transactional data
- Assign quantile-based scores to Recency, Frequency, and Monetary metrics
- Segment customers into meaningful behavioral groups
- Visualize key patterns using Power BI
- Deliver actionable insights for business growth and retention

---

## 📊 What is RFM Analysis?

**RFM Analysis** is a classic customer segmentation technique used in marketing and customer analytics:

- **Recency**: Days since the last purchase
- **Frequency**: Number of purchases made in the period
- **Monetary**: Total amount spent

Each customer is scored on a scale (1 to 4 in this case), and the combined score determines their segment.

### Example Segments
- 🏆 **Loyal Champions** – recent, frequent, high spenders  
- 💎 **Potentially Loyal** – good frequency/spend, but less recent  
- ⚠️ **Needing Attention** – moderate value but may be drifting  
- ❗ **Can't Lose** – previously valuable but inactive  
- ❌ **Lost** – infrequent, low spend, and inactive

---

## 🛠️ Tools Used

- **SQL (BigQuery)** – Data cleaning, aggregation, and scoring
- **Power BI** – Dashboard for visual insights
---

## 🧾 SQL Breakdown

### Key Steps

1. **Filter & Aggregate Transactions**  
   Cleaned data by filtering for valid transactions from Dec 2010 to Dec 2011.

2. **Calculate RFM Metrics**  
   - Recency: Days since last transaction  
   - Frequency: Count of purchase dates  
   - Monetary: Total purchase value  

3. **Assign Scores with Quantiles**  
   Used `APPROX_QUANTILES()` to assign scores for each metric (1–4).

4. **Segment Customers**
   Combined the scores to get an RFM score (3 to 12) and assigned groups using a `CASE` statement:
   
   ```sql
   CASE
     WHEN RFMScore BETWEEN 3 AND 4 THEN 'Lost'
     WHEN RFMScore BETWEEN 5 AND 6 THEN 'Can’t Lose'
     WHEN RFMScore BETWEEN 7 AND 9 THEN 'Needing Attention'
     WHEN RFMScore BETWEEN 10 AND 11 THEN 'Potentially Loyal'
     WHEN RFMScore = 12 THEN 'Loyal Champions'
   END AS RFMGroup
