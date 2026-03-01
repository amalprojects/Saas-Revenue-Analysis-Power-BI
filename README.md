# Saas-Revenue-Analysis-Power-BI
Power BI analysis of a SaaS business exploring revenue growth, profitability, customer plans, and marketing funnel performance.


# SaaS Revenue Analysis – Power BI

## Project Summary

This project explores revenue performance for a SaaS subscription business using Power BI.  
The goal was to understand not just how revenue changes over time, but **what drives that growth** from a customer, plan, and marketing perspective.

The analysis focuses on profitability, customer behavior, and the marketing funnel rather than building a dashboard full of visuals.

---

## Data Used

The project combines several datasets:

**Fact tables**
- `fact_revenue_monthly` – monthly revenue, costs, and gross profit
- `fact_subscriptions` – subscription records and signup dates
- `fact_leads` – leads generated
- `fact_marketing_spend` – monthly marketing spend

**Dimension tables**
- `dim_customers`
- `dim_plans`

A date table was used to handle time-based analysis across the model.

The Data Modelling structure implemented in power BI is shown below:

<img width="1117" height="681" alt="image" src="https://github.com/user-attachments/assets/b9e8ccd4-ab6d-4a83-b650-4dd014610ab8" />


---

## Analysis Approach

The work was broken into three sections.

### 1. Revenue & Profitability

Focus:
- Revenue trend over time
- Gross profit trend
- Profit margin %
- Revenue vs costs

Main finding:
- Revenue increased while costs remained relatively stable, leading to stronger margins toward the end of the year.

  <img width="1015" height="574" alt="image" src="https://github.com/user-attachments/assets/eaefefcc-c527-425e-a772-abcbef0aeb98" />


---

### 2. Customer & Plan Analysis

Focus:
- Revenue by plan
- Margin by plan
- Customer distribution by plan
- ARPU (average revenue per user)

Main findings:
- Higher-tier plans drive most revenue.
- Basic plans bring higher customer volume but lower value.
- Growth appears to come from higher-value subscriptions rather than more customers.

---

### 3. Marketing Funnel

Focus:
- Marketing spend trend
- Leads generated
- New subscriptions over time

Main findings:
- Marketing spend fluctuates significantly.
- Lead volume does not always move with spend.
- Subscription numbers remain fairly stable, suggesting consistent conversion behavior.

---

## Metrics / Measures

Examples of measures used:

```DAX
Total Revenue = SUM(fact_revenue_monthly[mrr_usd])

Total Gross Profit = SUM(fact_revenue_monthly[gross_profit_usd])

Profit Margin % =
DIVIDE([Total Gross Profit], [Total Revenue])

Distinct Customers =
DISTINCTCOUNT(fact_subscriptions[customer_id])

ARPU =
DIVIDE([Total Revenue], [Distinct Customers])
