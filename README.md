# Credit_Card_Transaction
 Credit card transaction and Customer Report Dashboard using PowerBi 
This PowerBI dashboard includes Credit Card Transaction Analysis and Credit Card Customer Reports.

# Project Objective 
Develop an integrated dashboard for credit card transaction monitoring and customer report analysis to enhance financial oversight, improve customer service, and identify trends for strategic decision-making.

# Key Goals:

 Real-Time Transaction Monitoring:
        Implement a system to track and display real-time credit card transactions.
        
 Comprehensive Data Visualization:
        Design intuitive visualizations to present transaction data, such as charts, graphs, etc.
        Enable filtering and segmentation of data by various parameters (e.g., time, location, transaction type).

 Customer Insights and Analysis:
        Generate detailed customer reports to analyze spending patterns and behavior.
        Identify high-value customers and offer personalized insights and recommendations.

  Performance Metrics and KPIs:
         Provide historical comparisons and trend analysis to monitor performance over time.

   User-Friendly Interface:
        Ensure the dashboard is user-friendly with an intuitive interface for easy navigation and data interpretation.
       
   Data Integration and Accuracy:
        Maintain high data accuracy and ensure regular updates for reliable analysis.

   Reporting and Export Features:
        Provide capabilities to generate and export detailed reports in various formats (e.g., PDF, Excel).

# Data Source
      The data used in this project consists of two tables in PostgreSQL:
## cc_detail Table (Credit Card Transaction Details Table)
Client_Num: Client number
Card_Category: Category of the credit card (Blue, Silver, Gold, 
Annual_Fees: Annual fees associated with the credit card
Activation_30_Days: Number of activations within 30 days
Customer_Acq_Cost: Acquisition cost for the customer
Week_Start_Date: Start date of the week
Week_Num: Week number
Qtr: Quarter
current_year: Current year
Credit_Limit: Credit limit
Total_Revolving_Bal: Total revolving balance
Total_Trans_Amt: Total transaction amount
Total_Trans_Ct: Total transaction count
Avg_Utilization_Ratio: Average utilization ratio
Use_Chip: Whether the card uses chip technology
Exp_Type: Expenditure type
Interest_Earned: Interest earned
Delinquent_Acc: Delinquent account status

## cust_detail Table ( Customer Details Table )
Client_Num: Client number
Customer_Age: Age of the customer
Gender: Gender of the customer
Dependent_Count: Number of dependents
Education_Level: Education level of the customer
Marital_Status: Marital status of the customer
State_cd: State code
Zipcode: Zip code
Car_Owner: Whether the customer owns a car
House_Owner: Whether the customer owns a house
Personal_Loan: Whether the customer has a personal loan
Contact: Contact information
Customer_Job: Job of the customer
Income: Income of the customer
Cust_Satisfaction_Score: Customer satisfaction score

# Power BI Dashboards
This PowerBI dashboard includes two dashboards:  Credit Card Transaction Analysis and Credit Card Customer Report Dashboards

## Credit Card Transaction Analysis
   This dashboard provides weekly insights into credit card transactions, including:
   Total revenue
   Total interest,
   Total transaction
   Total transaction count
   Quarterly revenue  Vs total transaction count 
   Insight on revenue based on card category, card usage type, customer job, customer education type, and expenditure type.
   Insight into how credit card type depends on revenue, total transaction, and interest earned.

## Credit Card Customer Report 
   This dashboard provides weekly insights into credit card customer report, including:
   Total revenue
   Total interest
   Total income
   Average customer satisfaction score
   Insight on revenue based on customer age group, gender, customer income group, customer education, state code, customer dependent status, and marital status.
   Insight into how customer job depends on revenue, income, and interest earned.


# Steps to develop dashboard
1. Prepare csv file
2. Create tables in PostgresSQL
3. Import csv file into PostgresSQL
4. Import the data from PostgreSQL into Power BI.
5. Create two new columns AgeGroup and IncomeGroup like given below
    AgeGroup = SWITCH(
    TRUE(),
     'public cust_detail'[customer_age] < 30, "20-30",
     'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
     'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
     'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
     'public cust_detail'[customer_age] >= 60, "60+",
   "unknown"
   )
    IncomeGroup = SWITCH(
    TRUE(),
     'public cust_detail'[income] < 35000, "Low",
     'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
     'public cust_detail'[income] >= 70000, "High",
   "unknown"
   )

6. Ensure the necessary measures and filters are set up for the dashboards. Here I use the below measures

week_num2 = WEEKNUM('public cc_detail'[week_start_date])

Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

# Insights

• Overall revenue is 55M
• Total interest is 8M
• Total transaction amount is 45M
• Blue & Silver credit card are contributing to 93% of overall
• Overall Delinquent rate is 6.07%.
• TX, NY & CA is contributing to 68%
• Overall Activation rate is 57.5%

