
# RFM Customer Segmentation Analysis

## Overview

This project applies RFM (Recency, Frequency, Monetary) analysis to segment customers based on purchasing behavior. Using SQL in BigQuery and Power BI for visualization, I identify high-value, at-risk, and disengaged customers to help drive personalized marketing strategies and improve retention.

---

## Objectives

- Calculate RFM metrics using transactional data  
- Assign quantile-based scores to Recency, Frequency, and Monetary metrics  
- Segment customers into meaningful behavioral groups  
- Visualize key patterns using Power BI  
- Deliver actionable insights for business growth and retention  

---

## What is RFM Analysis?

RFM analysis is a classic customer segmentation technique used in marketing and customer analytics:

- **Recency** – Days since the last purchase  
- **Frequency** – Number of purchases made  
- **Monetary** – Total amount spent  

Customers are scored on a scale (1 to 4 in this case), and their combined score determines their segment.

### Example Segments

- Loyal Champions – Recent, frequent, and high spenders  
- Potentially Loyal – Moderate to high spenders, but not as recent  
- Needing Attention – Moderate value but declining engagement  
- Can’t Lose – Previously valuable but now inactive  
- Lost – Low value and inactive  

---

## Tools Used

- SQL (BigQuery) – Data cleaning, aggregation, and scoring  
- Power BI – Dashboard for segment visualization and business insights  

---

## SQL Breakdown

### Key Steps

1. **Filter & Aggregate Transactions**  
   Filtered data to include valid transactions between Dec 2010 and Dec 2011.

2. **Calculate RFM Metrics**  
   - Recency: Days since the last transaction  
   - Frequency: Count of purchase dates  
   - Monetary: Total revenue per customer  

3. **Assign Quantile Scores**  
   Used `APPROX_QUANTILES()` to assign scores (1–4) for each RFM metric.

4. **Create Segments**  
   Generated a combined RFM score and categorized customers using a CASE statement:

   ```sql
   CASE
     WHEN RFMScore BETWEEN 3 AND 4 THEN 'Lost'
     WHEN RFMScore BETWEEN 5 AND 6 THEN 'Can’t Lose'
     WHEN RFMScore BETWEEN 7 AND 9 THEN 'Needing Attention'
     WHEN RFMScore BETWEEN 10 AND 11 THEN 'Potentially Loyal'
     WHEN RFMScore = 12 THEN 'Loyal Champions'
   END AS RFMGroup

  ## Key Findings

- **Loyal Champions (10.1%)** generated the highest revenue with consistent activity and an average purchase value of 15.1  
- **Potentially Loyal** customers made fewer purchases but contributed significantly to revenue (28%)  
- **Needing Attention** accounted for 27.6% of customers and showed declining engagement  
- **Can’t Lose** customers had a history of strong purchases but were largely inactive  
- **Lost** customers made infrequent purchases and were disengaged, representing low revenue potential  
- The **average recency** across all users was 92 days, highlighting long gaps in engagement  
- **Total sales reached 8.4 million**, with 47.9% coming from Loyal Champions alone  

---

## How a Business Can Use These Insights

- **Targeted Marketing**  
  Focus high-converting promotions on Loyal Champions and re-engagement campaigns on Potentially Loyal and Can’t Lose groups.  

- **Customer Retention Strategies**  
  Implement loyalty programs or special incentives for those at risk of churn.  

- **Revenue Forecasting**  
  Use RFM segmentation to forecast future revenue streams and customer value by group.  

- **Customer Journey Mapping**  
  Understand transition trends (e.g., from Potentially Loyal to Lost) to intervene before customers disengage.  

- **Prioritize Support & Service**  
  Provide tailored support to high-value groups to reinforce positive experiences and long-term loyalty.  

---

## PDF Report

The accompanying Power BI dashboard includes:

- Total customers by segment  
- Revenue contribution by segment  
- Average frequency and recency by group  
- Days between purchases per segment  
- Average purchase value  

---

## Contact

- **LinkedIn:** [https://www.linkedin.com/in/khristian-novoa-4529a9353](https://www.linkedin.com/in/khristian-novoa-4529a9353)  
- **Email:** khristiannovoa@gmail.com
