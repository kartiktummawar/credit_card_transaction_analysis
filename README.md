# Introduction
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enablingg stakeholders to monitor and analyze credit card operations effectively 

The dataset for the project can be accessed here : [dataset](/dataset/)

# Tools I Used
For my deep dive into the credit card transcation analysis, I harnessed the power of several key tools:

- **Power BI:** The backbone of my analysis, allowing me to unearth critical insights.
- **PostgreSQL:** The chosen database management system, ideal for handling the data.

# DAX Queries I Used

```sql
AgeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[customer_age] < 30, "20-30",
 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
 'public cust_detail'[customer_age] >= 60, "60+",
 "unknown"
 )

```

```sql
IncomeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[income] < 35000, "Low",
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
 'public cust_detail'[income] >= 70000, "High",
 "unknown"
)

```

```sql
week_num2 = WEEKNUM('public cc_detail'[week_start_date])

```

```sql
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

```

```sql
Current_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))) 

```

```sql
Previous_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

```

# The Analysis & Insights

### 1. WoW change:
• Revenue increased by 28.8%


### 2. Overview YTD:
• Overall revenue is 57M
• Total interest is 8M
• Total transaction amount is 46M
• Male customers are contributing more in revenue 31M, female 26M
• Blue & Silver credit card are contributing to 93% of overall
transactions
• TX, NY & CA is contributing to 68%
• Overall Activation rate is 57.5%
• Overall Delinquent rate is 6.06%



# What I Learned

- Developed an interactive dashboard using
transaction and customer data from a SQL database,
to provide real-time insights

- Streamlined data processing & analysis to monitor
key performance metrics and trends.

-  Shared actionable insights with stakeholders based
on dashboard findings to support decision-making
processes
