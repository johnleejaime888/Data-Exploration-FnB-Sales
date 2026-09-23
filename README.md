In this project, I explored the data based on business requirements to identify key trends, patterns, and insights that can support data-driven decision-making.

The data is divided into three categories.
- Sales Performance
- Product Analysis
- Date-based Analysis

# Sales Performance

- What is total revenue per branch?
- What is total quantity sold per branch?
- What is average transaction value per branch?
- How many transactions were recorded?
- What is the average order quantity per branch?

# Script
SELECT branch, sum(total_amount) as total_amount,
SUM(quantity) AS total_quantity_sold,
COUNT(DISTINCT transaction_id) AS total_transactions,
ROUND(AVG(total_amount), 0) AS average_transaction_value,
ROUND(AVG(quantity),0) AS average_order_quanity
FROM cleaned GROUP BY branch;

SELECT COUNT(transaction_id) AS total_order FROM cleaned;

# Output
<img width="694" height="168" alt="image" src="https://github.com/user-attachments/assets/ad7a6f38-4f39-46df-bbe5-b59680cef831" />

- Based on the data, the “Makati” branch recorded the highest sales and number of transactions in 2025.
- Each branch averaged approximately 2 items or quantity per order, with an average of more than 300 transactions per branch.

# Product Analysis

- Which products generate the most revenue?
- Which products sell the most units?
- Which category generates the highest sales?
- Which products have low sales?


# Script
SELECT product, sum(total_amount) AS total_amount_per_product,
COUNT(quantity) AS total_qty_sold_per_product
FROM cleaned GROUP BY product ORDER BY total_amount_per_product DESC;

# Output
<img width="277" height="214" alt="image" src="https://github.com/user-attachments/assets/291ccf89-b1d4-4081-bbd5-0bd9869ccf95" />
<img width="291" height="230" alt="image" src="https://github.com/user-attachments/assets/8c16aa2f-7f34-4fa1-bbae-25af981192be" />

SELECT category, sum(total_amount) AS total_amount_category
FROM cleaned GROUP BY category ORDER BY total_amount_category DESC;

# Output
<img width="227" height="85" alt="image" src="https://github.com/user-attachments/assets/4b895703-26c1-40cf-9d9b-d3e96da5f461" />

SELECT product, sum(total_amount) AS total_amount_product
FROM cleaned GROUP BY product ORDER BY total_amount_product ASC;

# Output
<img width="262" height="221" alt="image" src="https://github.com/user-attachments/assets/d469a8e8-d0c3-45cc-97ca-f138877b0b55" />

- The “Beef Burger” generated the highest revenue, while the “Americano” had the highest quantity sold.
- Crossant

# Date-based Analysis
- Sales by month
- Sales by day


# Script
SELECT MONTHNAME(transaction_date) AS month_name, SUM(total_amount) AS total_revenue_per_month
FROM cleaned GROUP BY MONTH(transaction_date), MONTHNAME(transaction_date) ORDER BY MONTH(transaction_date) asc;

<img width="260" height="234" alt="image" src="https://github.com/user-attachments/assets/67f7f731-1ead-491a-ae58-f743503b66e0" />


  SELECT transaction_date, SUM(total_amount) AS total_revenue_per_day
FROM cleaned GROUP BY transaction_date, dayname(transaction_date) ORDER BY transaction_date asc;

- Based on the monthly revenue analysis, March generated the highest total revenue, while February recorded the lowest.





