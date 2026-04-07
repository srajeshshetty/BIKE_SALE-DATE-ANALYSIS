# 🚴 Bike Sales Data Analysis (MySQL Project)

## 📌 Project Overview

This project analyzes bike sales data using **MySQL**.
It demonstrates SQL skills such as **data cleaning, joins, aggregations, and subqueries** to extract meaningful business insights.

---

## 🎯 Objectives

* Analyze total bike sales and revenue
* Identify top-selling bike models
* Understand sales distribution by city and state
* Practice real-world SQL queries

---

## 🛠️ Tools & Technologies

* MySQL Workbench
* SQL (Joins, GROUP BY, Aggregate Functions, Subqueries)
* Excel (Data preparation)
* GitHub

---

## 📂 Dataset Description

### 🟢 bikes_proj (Bike Details)

* bike_id
* model
* category1
* category2
* frame
* price

---

### 🔵 orders_proj (Sales Data)

* order_sequence
* order_id
* order_line
* order_date
* customer_id
* product_id
* quantity

---

### 🟣 bikesales_proj (Shop Details)

* bikeshop_id
* bikeshop_name
* city
* state
* latitude
* longitude

---

## 🔗 Table Relationships

* bikes_proj.bike_id = orders_proj.product_id
* orders_proj.customer_id = bikesales_proj.bikeshop_id

---

## 🧹 Data Cleaning

* Renamed columns with special characters (e.g., `bike.id` → `bike_id`)
* Ensured consistent data types
* Cleaned and formatted imported CSV data

---

## 🔍 SQL Analysis (10 Key Queries)

### 1. Total Sales per Bike

```sql
SELECT b.model, SUM(o.quantity) AS total_quantity
FROM bikes_proj b
JOIN orders_proj o ON b.bike_id = o.product_id
GROUP BY b.model;
```

---

### 2. Total Revenue

```sql
SELECT SUM(o.quantity * b.price) AS total_revenue
FROM bikes_proj b
JOIN orders_proj o ON b.bike_id = o.product_id;
```

---

### 3. Top Selling Bikes

```sql
SELECT b.model, SUM(o.quantity) AS total_sold
FROM bikes_proj b
JOIN orders_proj o ON b.bike_id = o.product_id
GROUP BY b.model
ORDER BY total_sold DESC;
```

---

### 4. Revenue per Bike

```sql
SELECT b.model, SUM(o.quantity * b.price) AS revenue
FROM bikes_proj b
JOIN orders_proj o ON b.bike_id = o.product_id
GROUP BY b.model;
```

---

### 5. Sales by City

```sql
SELECT s.city, SUM(o.quantity) AS total_sales
FROM orders_proj o
JOIN bikesales_proj s ON o.customer_id = s.bikeshop_id
GROUP BY s.city;
```

---

### 6. Revenue by State

```sql
SELECT s.state, SUM(o.quantity * b.price) AS total_revenue
FROM orders_proj o
JOIN bikes_proj b ON b.bike_id = o.product_id
JOIN bikesales_proj s ON o.customer_id = s.bikeshop_id
GROUP BY s.state;
```

---

### 7. Average Bike Price

```sql
SELECT AVG(price) AS avg_price
FROM bikes_proj;
```

---

### 8. Bikes Above Average Price (Subquery)

```sql
SELECT model, price
FROM bikes_proj
WHERE price > (SELECT AVG(price) FROM bikes_proj);
```

---

### 9. Customer Purchase Count

```sql
SELECT customer_id, SUM(quantity) AS total_purchases
FROM orders_proj
GROUP BY customer_id
ORDER BY total_purchases DESC;
```

---

### 10. Full Sales Report

```sql
SELECT 
    s.bikeshop_name,
    s.city,
    b.model,
    o.quantity,
    b.price,
    (o.quantity * b.price) AS revenue
FROM orders_proj o
JOIN bikes_proj b ON b.bike_id = o.product_id
JOIN bikesales_proj s ON o.customer_id = s.bikeshop_id;
```

---

## 📊 Key Insights

* Identified top-selling bike models
* Calculated total revenue generated
* Analyzed sales distribution across different locations

---

## 🚀 Future Improvements

* Add query output screenshots
* Build dashboard using Power BI or Tableau
* Implement advanced SQL (window functions)

---

## 👨‍💻 Author name

Srajesh shetty
