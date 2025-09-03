🍕 Pizza Sales SQL Project

# 📖 Project Overview

This project analyzes a Pizza Sales Dataset using SQL queries.
The goal is to explore customer behavior, sales performance, and product insights.


---

# 🛠️ Tools & Technologies

SQL (MySQL / PostgreSQL / SQLite)

Database Management System (MySQL Workbench / pgAdmin / SQLite Studio)

Pizza Sales Dataset (orders, order details, pizzas, categories)



---

# 📂 Dataset Structure

1️⃣ Orders Table

Column	Type	Description

order_id	INT	Unique order ID
order_date	DATE	Date of order
order_time	TIME	Time of order


2️⃣ Order Details Table

Column	Type	Description

order_details_id	INT	Unique ID for order detail
order_id	INT	Linked to Orders table
pizza_id	TEXT	Linked to Pizzas table
quantity	INT	Number of pizzas ordered


3️⃣ Pizzas Table

Column	Type	Description

pizza_id	TEXT	Unique pizza code
pizza_type_id	TEXT	Linked to Pizza Types
size	TEXT	Size of pizza (S/M/L/XL)
price	DECIMAL	Price of pizza


4️⃣ Pizza Types Table

Column	Type	Description

pizza_type_id	TEXT	Unique pizza type
name	TEXT	Name of pizza
category	TEXT	Pizza category (Veg/Non-Veg)
ingredients	TEXT	Ingredients list



---

# 📊 SQL Queries & Analysis

🔹 1. Total Number of Orders

SELECT COUNT(*) AS total_orders 
FROM orders;

🔹 2. Total Revenue

SELECT ROUND(SUM(quantity * price), 2) AS total_revenue
FROM order_details od
JOIN pizzas p ON od.pizza_id = p.pizza_id;

🔹 3. Most Ordered Pizza

SELECT pt.name, SUM(od.quantity) AS total_ordered
FROM order_details od
JOIN pizzas p ON od.pizza_id = p.pizza_id
JOIN pizza_types pt ON p.pizza_type_id = pt.pizza_type_id
GROUP BY pt.name
ORDER BY total_ordered DESC
LIMIT 5;

🔹 4. Revenue by Pizza Category

SELECT pt.category, ROUND(SUM(od.quantity * p.price), 2) AS revenue
FROM order_details od
JOIN pizzas p ON od.pizza_id = p.pizza_id
JOIN pizza_types pt ON p.pizza_type_id = pt.pizza_type_id
GROUP BY pt.category
ORDER BY revenue DESC;

🔹 5. Daily Sales Trend

SELECT order_date, COUNT(order_id) AS total_orders
FROM orders
GROUP BY order_date
ORDER BY order_date;


---

# 📌 Roadmap

[x] Load dataset into SQL DB

[x] Explore basic queries (count, sum, avg)

[x] Perform sales analysis

[ ] Add advanced queries (CTE, window functions)

[ ] Create dashboard using Power BI / Tableau



---

# 📬 Contact

👤 Your Name

GitHub:https://github.com/34Mohdirshad

Email: mohdirshadmi36542@gmail.com

