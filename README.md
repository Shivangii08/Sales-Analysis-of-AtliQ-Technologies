# Project : Sales Insights of Data Analysis-AtliQ Hardware
![image](https://github.com/user-attachments/assets/7fc13841-0237-4be9-b35c-7b9c2229d8a8)

# PROBLEM: STATEMENT
AtliQ Hardware, a Delhi-based computer hardware supplier with regional offices across India, was struggling with declining sales amidst a rapidly growing market. The sales director faced challenges in tracking sales performance due to unreliable verbal reports from regional managers. To address this, we undertook a data analysis project to develop a Power BI dashboard that would provide real-time sales insights and enable data-driven decision-making.
# Data Discovery
## Project Planning using AIMS Grid:
**1. Purpose:**
   Uncover hidden sales patterns, automate data collection, and provide actionable insights to support data-driven decision making.

   
**2. Stakeholders:**
   Sales, Marketing, Customer Service, Data & Analytics, IT
   
**3. End Result:**
   An automated dashboard delivering up-to-date sales information for informed decision making.

   
**4. Success Criteria:**
  -Dashboard reveals valuable sales trends and patterns.
  -Sales team demonstrates improved decision making with a 10% cost reduction.
  -Manual data collection is eliminated, saving 20% of business time for value-added activities.
### Flowchart of Project:
![image](https://github.com/user-attachments/assets/1d05c41d-50e6-4db9-9473-2862dad142a2)

# DATA ANALYSIS USING SQL
Completed the Data discovery and then used mySQL for data analysis.

SQL database dump is in db_dump.sql file above. Download db_dump.sql file to your local computer

1. Importing Data to MySQL workbench
   ![image](https://github.com/user-attachments/assets/20b20dbf-7104-4796-8c6c-6137b02c0436)

The import of data is done from an already existing MySQL file. This file has to be loaded into MySQL workbench for further data analysis.

Analysis of data by looking into different tables and reflecting garbage values

We can see that garbage value that the table market cantains certain values which are incorrect.

**SELECT * FROM sales.market;**

And then we can check that transacation table we can see that ceratin negative value in amount which is not possible. and we can see that certain transactions are in USD. Hence, filtration of that is also needed by converting into INR.

**SELECT * FROM sales.transactions;**

**Analysis of different SQL statement on data base**

1. **To find of all customers records:**

   SELECT * FROM sales.customers;

2. **To find total number of customers**

   SELECT count(*) From sales.customers;

3. **To find transactions for Chennai market (market code for chennai is Mark001**

   SELECT * FROM sales.transactions where market_code='Mark001';

4. **To find distrinct product codes that were sold in chennai**

   SELECT distinct product_code FROM sales.transactions where market_code='Mark001';

5. **To find transactions for Chennai market (market code for chennai is Mark002**

   SELECT * FROM sales.transactions where market_code='Mark002';

6. **To find distrinct product codes that were sold in mumbai**

   SELECT distinct product_code FROM sales.transactions where market_code='Mark002';

7. **To find transactions where currency is US dollars**

   SELECT * from sales.transactions where currency="USD";

8. **To find transactions in 2020 join by date table**

    SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020;

9.  **To find transactions in 2019 join by date table**

    SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019;

9.  **To find total revenue in year 2020,**

    SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.currency="INR\r" 
    or sales.transactions.currency="USD\r";

10. **To find total revenue in year 2019,**

    SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019 and sales.transactions.currency="INR\r" 
    or sales.transactions.currency="USD\r";

11.  **To find total revenue in year 2020, January Month,**

    SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and 
    (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");

12.  **To find total revenue in year 2020, February Month,**

    SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" and 
    (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");

13.  **To find total revenue in year 2019, January Month,**

    SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and 
    (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");

14.  **To find total revenue in year 2019, February Month,**

      SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" 
      and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");

15.  **To find total revenue in year 2020 in Chennai**

      SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and 
      sales.transactions.market_code="Mark001";

16.  **To find total revenue in year 2020 in Mumbai**

        SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and 
        sales.transactions.market_code="Mark002";

Similarly, if we want different of any other particular city the market code of that city is used on the mysql workbench.

# Data Cleaning and ETL (Extract, Transform, Load):
In this process, we are work on data cleaning and ETL.

Step 1: Connect the MySQL database with the PowerBI desktop.

Step 2: Loading data into the Power BI deskstop. This step load all the tables and created in the data base. This load option will connect with the SQL and pull all the records into power BI environment.

In that model view looking up for model which form the star schema.
![image](https://github.com/user-attachments/assets/0ea36471-e02d-48da-bf47-7b49a3c2d3f2)

Step 3: Transform data with the help of Power Query

Perform filtration in market’s table: In the tables perform when we click on the transform data option, we are directed to Power query editor. Power query editor is where we perform out ETL.and then we can perform data transformation i.e. Data Cleaning, Data Wrangling, Data Munging. we need to filter the rows where the values are null and filtering the data and deselecting the blank option.

Perform filtration in Transaction’s table: In the table perform when we check the query in the MySQL to filter some negative values and also 0 values that appears in the table, the desired output is received.and we will perform the similar filtration in PowerBI. we have deselecting the values, don’t want in the table. The result after filtration. the zero values represent some garbage values which is not possible so we need to clean that data.

Convert USD into INR in the transaction’s table: the AtliQ Hardware only works in India so the USD values are not possible. we need to convert those USD values into INR by using some formulas. Add new column - Conditional column - normalized currency where sales amount will be in INR

In power query editore finding the total values having USD as currency.
 `=Table.AddColumn(#"Filtered Rows", "norm_sales_amount",each if [currency] = "USD" then [sales_amount]*75 else [sales_amount]`

 # DATA MODELLING
 And then dataset was cleaned and transformed, it was ready to the data modeled.

The sales insights data tables as show below:

![image](https://github.com/user-attachments/assets/ed905eca-1743-4ad7-a910-d8997d1877d4)

# DAX
Measures used in all visualization are:

Key Measures:

1. Profit Margin % = DIVIDE([Total Profit Margin],[Revenue],0)

2. Profit Margin Contribution % = DIVIDE([Total Profit Margin],CALCULATE([Total Profit Margin],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))

3. Revenue = SUM('sales transactions'[sales_amount])

4. Revenue Contribution % = DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))

5. Revenue LY = CALCULATE([Revenue],SAMEPERIODLASTYEAR('sales date'[date]))

6. sales quntity = SUM('sales transactions'[sales_qty])

7. Total Profit Margin = SUM('Sales transactions'[Profit_Margin])

Profit Target:

8. Profit Target1 = GENERATESERIES(-0.05, 0.15, 0.01)

9. Profit Target Value = SELECTEDVALUE('Profit Target1'[Profit Target])
    
10. Target Diff = [Profit Margin %]-'Profit Target1'[Profit Target Value]

# DASHBOARD:
### Key Insights:
![image](https://github.com/user-attachments/assets/9da5e824-dbb8-40c3-87dc-c096fcd56005)

### Profit Analysis:
![image](https://github.com/user-attachments/assets/a034ad9d-f1f5-428f-be7a-48806175d3d0)

![image](https://github.com/user-attachments/assets/fc63229a-1204-4ab5-a18b-874e894750cf)

# Tools, Software and Libraries :
1.MySQL

2.Microsoft Power BI

3.Power Query Editor

4.DAX Language




   



