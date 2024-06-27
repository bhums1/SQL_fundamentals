# SQL_fundamentals

This repo is for storing sample SQL codes for reference.

 1) Select Query  

select * 

from Table_name ; 

primary key (column with unique values)

SQL JOIN
A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

SQL LEFT JOIN Keyword
The LEFT JOIN keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.

SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;

Note: In some databases LEFT JOIN is called LEFT OUTER JOIN.

id	date	product	quantity	price
1	2024-04-01	Product A	10	9.99
2	2024-04-02	Product B	5	19.99
3	2024-04-03	Product C	8	14.99
4	2024-04-04	Product A	3	9.99
5	2024-04-05	Product B	7	19.99
6	2024-04-06	Product C	2	14.99
7	2024-05-01	Product A	12	9.99
8	2024-05-02	Product B	6	19.99
9	2024-05-03	Product C	4	14.99
10	2024-05-04	Product A	9	9.99
11	2024-05-05	Product B	8	19.99
12	2024-05-06	Product C	3	14.99
13	2024-06-01	Product A	11	9.99
14	2024-06-02	Product B	4	19.99
15	2024-06-03	Product C	7	14.99
16	2024-06-04	Product A	6	9.99
17	2024-06-05	Product B	5	19.99
18	2024-06-06	Product C	8	14.99
![image](https://github.com/bhums1/SQL_fundamentals/assets/117505089/1f90396f-0ae3-4717-a6a7-9f6972ce8e20)


1. 
SELECT Clause
Retrieve all columns from the sales_data table.

SELECT * FROM sales_data;

2. WHERE Clause
Filter records to show only sales for 'Product A'.

SELECT * FROM sales_data
WHERE product = 'Product A';


3. GROUP BY Clause
Group records by product and calculate total sales for each product.

SELECT product, SUM(quantity * price) AS total_sales
FROM sales_data
GROUP BY product;

4. HAVING Clause
Group records by product and show only those products with total sales greater than 100.

SELECT product, SUM(quantity * price) AS total_sales
FROM sales_data
GROUP BY product
HAVING total_sales > 100;

5. ORDER BY Clause
Order records by total sales in descending order.

SELECT product, SUM(quantity * price) AS total_sales
FROM sales_data
GROUP BY product
ORDER BY total_sales DESC;

6. LIMIT Clause
Limit the number of results to the top 3 products by total sales.


SELECT product, SUM(quantity * price) AS total_sales
FROM sales_data
GROUP BY product
ORDER BY total_sales DESC
LIMIT 3;


7. Combining Clauses
Combine multiple clauses to find the top 3 products by total sales, only considering sales in May 2024.

SELECT product, SUM(quantity * price) AS total_sales
FROM sales_data
WHERE date BETWEEN '2024-05-01' AND '2024-05-31'
GROUP BY product
HAVING total_sales > 50
ORDER BY total_sales DESC
LIMIT 3;

--- Breakdown of Combined Clauses Example
SELECT Clause:

product, SUM(quantity * price) AS total_sales: Selects the product name and calculates total sales.
WHERE Clause:

date BETWEEN '2024-05-01' AND '2024-05-31': Filters records to include only those within May 2024.
GROUP BY Clause:

product: Groups the results by product.
HAVING Clause:

total_sales > 50: Filters groups to include only those with total sales greater than 50.
ORDER BY Clause:

total_sales DESC: Orders the results by total sales in descending order.
LIMIT Clause:

3: Limits the result to the top 3 products.
These examples illustrate how different SQL clauses can be used individually and combined to query data from the sales_data table effectively.







