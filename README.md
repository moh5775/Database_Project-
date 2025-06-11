# 📚 Database Project (Online Bookstore Inventory Management System)

## 📌 Overview
This project is a relational database system for managing a bookstore, designed using SQL. It includes tables for books, customers, orders, reviews, categories, and admins. The database allows for efficient inventory management, customer tracking, order processing, and data analysis.

## 🗃️ Database Structure
The database includes the following tables:

- **Books** – Contains book details like title, genre, price, and stock.  
- **Customers** – Stores customer information and their preferred genre.  
- **Orders** – Tracks orders, total amounts, payment status, and delivery status.  
- **Order_Items** – Contains details of items in each order.  
- **Categories** – Represents different book categories.  
- **Reviews** – Stores customer reviews and ratings for books.  
- **Admins** – Includes admin and manager roles for system management.  

## 🔍 SQL Features Demonstrated
- Data retrieval using `SELECT` queries with `WHERE`, `GROUP BY`, `ORDER BY`, and subqueries  
- Aggregate functions like `AVG()`, `COUNT()`, and `SUM()`  
- Filtering records using date ranges and logical conditions  
- Modifying tables using `ALTER TABLE`  
- Updating records using `UPDATE`  
- Nested and conditional queries  

## 📈 Insights & Use Cases
- Identify low stock books  
- Track customer order history and total spending  
- Calculate average book ratings  
- Monitor order delivery and payment status  
- Analyze genre popularity  
- Maintain admin roles and permissions  

## ✅ Setup Instructions
1. Import the SQL file into your database management system (e.g., MySQL, PostgreSQL).  
2. Run the provided SQL queries for data manipulation and analysis.  
3. Customize the dataset or expand features as needed for your use case.  

## 🧾 Files Included
- `bookstore_schema.sql` – SQL code to create and populate tables  
- `queries.sql` – All queries used for analysis  
- `README.md` – Project documentation (this file)  

## 🧠 Conclusion
This project demonstrates the core concepts of database design and SQL querying in a real-world context. It is suitable for academic use, small business prototypes, or further development into a complete bookstore management system.
