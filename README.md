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

1. Clear Price–Volume Segmentation Across Plans
   
Basic & Pro → highest customer counts
Business & Enterprise → highest revenue per customer (ARPU)
This suggests a two-tier business model:

-Volume tier: Basic / Pro plans drive user acquisition.
-Value tier: Business / Enterprise plans drive revenue efficiency.

Insight:
Revenue growth is likely driven more by upselling customers to higher plans rather than simply acquiring more Basic users

2. Enterprise Plan Has the Highest Customer Value

Enterprise shows:
Highest ARPU (~13.6K)
Lowest customer count (~20)

This indicates very high customer value but limited adoption.

Insight:
Enterprise customers generate disproportionately high revenue per account, suggesting potential growth through targeted enterprise sales or expansion strategies.

3. Revenue Concentration in Mid-Tier Plans

The revenue chart shows:
-Business plan generates the highest revenue
-Followed by Pro
-Enterprise contributes less overall due to low customer count

Insight:
Business appears to be the optimal balance between price and adoption, making it the most commercially effective plan.

| Plan       | Customers | ARPU      | Strategy Signal         |
| ---------- | --------- | --------- | ----------------------- |
| Basic      | High      | Low       | Entry-level acquisition |
| Pro        | High      | Medium    | Core user base          |
| Business   | Medium    | High      | Revenue driver          |
| Enterprise | Low       | Very high | Premium niche           |

Insight:
The SaaS business likely follows a land-and-expand strategy, acquiring users through lower plans and monetizing through upgrades.

Key Takeaway:

-Revenue growth is driven primarily by mid-tier plans (Business) that balance customer volume and ARPU, while Enterprise   customers generate the highest value per account but remain underrepresented.
-Strategic growth opportunities likely lie in:
-Upselling Pro customers to Business
-Expanding Enterprise adoption
-Maintaining Basic plan as an acquisition channel

<img width="1014" height="571" alt="image" src="https://github.com/user-attachments/assets/52520b39-325d-4158-b59a-6e079179480d" />



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

<img width="1020" height="573" alt="image" src="https://github.com/user-attachments/assets/7dd2f38e-ea07-46d8-9e94-66b988ad9c8a" />



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
