# Sales-data-analysis
in this project, you will dive into a large sales dataset to extract valuable insights. You  will explore sales trends over time, identify the best-selling products, calculate revenue  metrics such as total sales and profit margins, and create visualizations to present your  findings effectively.
## Sales Insights Data Analysis Project
## Sales Data Analysis with SQL and Power BI

### Instructions to setup mysql on your local computer
### Run Locally

1. SQL database dump is in db_dump.sql file above. Download `db_dump_version_2.sql` file to your local computer and import it as per instructions given in the tutorial video
Clone the project

```bash
  git clone https://github.com/deepamkalekar/Sale-Data-Analysis-PowerBI.git
```

Go to the project directory and open ``` .pbix ``` file with Microsoft Power BI Desktop

### Data Analysis Using SQL

1. Show all customer records
    `SELECT * FROM customers;`
1. Show total number of customers
    `SELECT count(*) FROM customers;`
1. Show transactions for Chennai market (market code for chennai is Mark001
    `SELECT * FROM transactions where market_code='Mark001';`
1. Show distrinct product codes that were sold in chennai
    `SELECT distinct product_code FROM transactions where market_code='Mark001';`
1. Show transactions where currency is US dollars
    `SELECT * from transactions where currency="USD"`
1. Show transactions in 2020 join by date table
    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`
1. Show total revenue in year 2020,
    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue in year 2020, January Month,
    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`
1. Show total revenue in year 2020 in Chennai
    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
Power BI Dashboard Preview
============================

1. Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`
![Page1](https://github.com/deepamkalekar/Sale-Data-Analysis-PowerBI/blob/master/Sales-key-insight.png)
![Page2](https://github.com/deepamkalekar/Sale-Data-Analysis-PowerBI/blob/master/sales-profit-analysis.png)
![Page3](https://github.com/deepamkalekar/Sale-Data-Analysis-PowerBI/blob/master/sales-performance-insight.png)
