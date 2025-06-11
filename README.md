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
- [**ER Diagram**](https://github.com/moh5775/Database_Project-/blob/main/ER%20diagram.png) 
- [**Schema Diagram**](https://github.com/moh5775/Database_Project-/blob/main/Schema%20Diagram.png) 
- [**Report.docx**](https://github.com/moh5775/Database_Project-/blob/main/Report.docx)
- [**Report.pdf**](https://github.com/moh5775/Database_Project-/blob/main/Report.pdf)
- [**MySQL.sql**](https://github.com/moh5775/Database_Project-/blob/main/MySQL.sql)
- [**MySQL.pdf**](https://github.com/moh5775/Database_Project-/blob/main/MySQL.pdf)
  


```MySQL
-- 1. Admins
CREATE TABLE Admins (
    admin_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    phone VARCHAR(15),
    role VARCHAR(50),
    created_at VARCHAR(10)
);


-- 2. Categories
CREATE TABLE Categories (
    category_id INT PRIMARY KEY,
    name VARCHAR(50),
    description TEXT,
    created_by INT,
    created_at VARCHAR(10),
    status VARCHAR(20),
    FOREIGN KEY (created_by) REFERENCES Admins(admin_id)
);

-- 3. Books
CREATE TABLE Books (
    book_id INT PRIMARY KEY,
    title VARCHAR(100),
    author VARCHAR(100),
    genre VARCHAR(50),
    price DECIMAL(6,2),
    stock INT,
    category_id INT,
    FOREIGN KEY (category_id) REFERENCES Categories(category_id)
);

-- 4. Customers
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    phone VARCHAR(15),
    address VARCHAR(200),
    registration_date VARCHAR(10)
);

-- 5. Orders
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date VARCHAR(10),
    total_amount DECIMAL(8,2),
    payment_status VARCHAR(20),
    delivery_status VARCHAR(20),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);

-- 6. Order_Items
CREATE TABLE Order_Items (
    item_id INT PRIMARY KEY,
    order_id INT,
    book_id INT,
    quantity INT,
    price DECIMAL(6,2),
    subtotal DECIMAL(8,2),
    FOREIGN KEY (order_id) REFERENCES Orders(order_id),
    FOREIGN KEY (book_id) REFERENCES Books(book_id)
);

-- 7. Reviews
CREATE TABLE Reviews (
    review_id INT PRIMARY KEY,
    book_id INT,
    customer_id INT,
    rating INT,
    comment TEXT,
    review_date VARCHAR(10),
    
    FOREIGN KEY (book_id) REFERENCES Books(book_id),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);


INSERT INTO Admins VALUES
(1, 'admin1', 'admin1@gmail.com', '016561234', 'Manager', '01-01-2023'),
(2, 'admin2', 'admin2@gmail.com', '25451234', 'Manager', '01-02-2023'),
(3, 'admin3', 'admin3@gmail.com', '04551234', 'Staff', '01-03-2023'),
(4, 'admin4', 'admin4@gmail.com', '1532334', 'Staff', '15-03-2023'),
(5, 'admin5', 'admin5@gmail.com', '12336984', 'Manager', '01-04-2023'),
(6, 'admin6', 'admin6@gmail.com', '1233684', 'Staff', '05-04-2023'),
(7, 'admin7', 'admin7@gmail.com', '12338634', 'Staff', '10-04-2023'),
(8, 'admin8', 'admin8@gmail.com', '126938534', 'Manager', '15-04-2023'),
(9, 'admin9', 'admin9@gmail.com', '12334534', 'Staff', '18-04-2023'),
(10, 'admin10', 'admin10@gmail.com', '12354334', 'Staff', '20-04-2023'),
(11, 'admin11', 'admin11@gmail.com', '123425744', 'Manager', '22-04-2023'),
(12, 'admin12', 'admin12@gmail.com', '1275274534', 'Staff', '24-04-2023'),
(13, 'admin13', 'admin13@gmail.com', '1252434', 'Manager', '25-04-2023'),
(14, 'admin14', 'admin14@gmail.com', '1578237234', 'Staff', '26-04-2023'),
(15, 'admin15', 'admin15@gmail.com', '12543234', 'Staff', '27-04-2023'),
(16, 'admin16', 'admin16@gmail.com', '1235244', 'Manager', '28-04-2023'),
(17, 'admin17', 'admin17@gmail.com', '1237543274', 'Staff', '29-04-2023'),
(18, 'admin18', 'admin18@gmail.com', '123753274', 'Staff', '30-04-2023');

INSERT INTO Categories (category_id, name, description, created_by, created_at, status) VALUES
(1, 'Fiction', 'Stories that are imaginative and not real.', 1, '29-04-2025', 'Active'),
(2, 'Self-help', 'Books that guide personal development.', 3, '29-04-2025', 'Active'),
(3, 'Dystopian', 'Fictional society in decline or oppression.', 1, '15-04-2025', 'Active'),
(4, 'Classic', 'Timeless literary works.', 2, '29-04-2025', 'Active'),
(5, 'History', 'Books based on historical events.', 1, '18-03-2025', 'Active'),
(6, 'Finance', 'Books about managing money.', 1, '29-04-2025', 'Active'),
(7, 'Thriller', 'Books full of suspense and excitement.', 6, '29-04-2025', 'Stock Out'),
(8, 'Drama', 'Emotional and realistic storytelling.', 1, '10-04-2025', 'Active'),
(9, 'Mystery', 'Books about solving crimes or puzzles.', 9, '10-04-2025', 'Active'),
(10, 'Memoir', 'Personal life stories.', 2, '12-03-2025', 'Active'),
(11, 'Biography', 'Books about famous people.', 1, '14-04-2025', 'Active'),
(12, 'Science', 'Books exploring scientific topics.', 1, '22-03-2025', 'Active'),
(13, 'Religion', 'Books about religious beliefs.', 4, '29-04-2025', 'Active'),
(14, 'Politics', 'Books related to political theory or history.', 1, '29-04-2025', 'Active'),
(15, 'Poetry', 'Books of poems.', 8, '23-04-2025', 'Active'),
(16, 'Philosophy', 'Books on thinking and wisdom.', 7, '20-03-2025', 'Active'),
(17, 'Technology', 'Books on modern tech trends.', 1, '29-04-2025', 'Active'),
(18, 'Romance', 'Love and relationship stories.', 6, '29-04-2025', 'Active');
INSERT INTO Books VALUES
(1, 'The Alchemist', 'Paulo Coelho', 'Fiction', 12.99, 20,1),
(2, 'Atomic Habits', 'James Clear', 'Self-help', 15.50, 15,2),
(3, '1984', 'George Orwell', 'Dystopian', 11.00, 25,3),
(4, 'To Kill a Mockingbird', 'Harper Lee', 'Classic', 10.99, 30,4),
(5, 'The Subtle Art...', 'Mark Manson', 'Self-help', 13.75, 18,2),
(6, 'Sapiens', 'Yuval Noah Harari', 'History', 17.80, 22,5),
(7, 'Think and Grow Rich', 'Napoleon Hill', 'Self-help', 14.00, 16,2),
(8, 'Rich Dad Poor Dad', 'Robert Kiyosaki', 'Finance', 9.99, 27,6),
(9, 'Crime and Punishment', 'Fyodor Dostoevsky', 'Classic', 13.49, 12,3),
(10, 'The Book Thief', 'Markus Zusak', 'Historical', 12.30, 21,5),
(11, 'The Power of Habit', 'Charles Duhigg', 'Self-help', 14.25, 19,2),
(12, 'Digital Fortress', 'Dan Brown', 'Thriller', 11.75, 20,7),
(13, 'The Da Vinci Code', 'Dan Brown', 'Thriller', 12.50, 14,7),
(14, 'Inferno', 'Dan Brown', 'Thriller', 13.25, 23,7),
(15, 'The Kite Runner', 'Khaled Hosseini', 'Drama', 12.99, 18,8),
(16, 'A Thousand Splendid Suns', 'Khaled Hosseini', 'Drama', 13.45, 17,8),
(17, 'The Girl on the Train', 'Paula Hawkins', 'Mystery', 11.60, 26,9),
(18, 'Educated', 'Tara Westover', 'Memoir', 10.95, 15,10);


INSERT INTO Customers VALUES
(1, 'Ayesha Khan', 'ayesha@mail.com', '01711112222', 'Dhaka', '10-01-2024'),
(2, 'Mehedi Hasan', 'mehedi@mail.com', '01712345678', 'Chittagong', '12-01-2024'),
(3, 'Tania Rahman', 'tania@mail.com', '01811113333', 'Sylhet', '01-02-2024'),
(4, 'Junaid Alam', 'junaid@mail.com', '01719876543', 'Dhaka', '05-02-2024'),
(5, 'Nusrat Jahan', 'nusrat@mail.com', '01688889999', 'Khulna', '10-02-2024'),
(6, 'Arif Hossain', 'arif@mail.com', '01923456789', 'Rajshahi', '15-02-2024'),
(7, 'Farhana Noor', 'farhana@mail.com', '01745678901', 'Comilla', '18-02-2024'),
(8, 'Tamim Iqbal', 'tamim@mail.com', '01899990000', 'Barisal', '01-03-2024'),
(9, 'Jannat Ara', 'jannat@mail.com', '01911112222', 'Rangpur', '05-03-2024'),
(10, 'Sakib Ali', 'sakib@mail.com', '01776543210', 'Mymensingh', '08-03-2024'),
(11, 'Salma Akter', 'salma@mail.com', '01711223344', 'Sylhet', '11-03-2024'),
(12, 'Shuvo Rahman', 'shuvo@mail.com', '01812344321', 'Bogura', '15-03-2024'),
(13, 'Lamia Haque', 'lamia@mail.com', '01987654321', 'Dhaka', '17-03-2024'),
(14, 'Munna Hossain', 'munna@mail.com', '01799887766', 'Chandpur', '20-03-2024'),
(15, 'Rifat Karim', 'rifat@mail.com', '01845678912', 'Kushtia', '25-03-2024'),
(16, 'Shamima Nasrin', 'shamima@mail.com', '01722334455', 'Noakhali', '28-03-2024'),
(17, 'Saif Ahmed', 'saif@mail.com', '01833221100', 'Cox’s Bazar', '01-04-2024'),
(18, 'Nadia Islam', 'nadia@mail.com', '01955667788', 'Dhaka', '05-04-2024');


INSERT INTO Orders VALUES
(1, 1, '2024-04-10', 25.98, 'Paid', 'Delivered'),
(2, 2, '2024-04-11', 15.50, 'Unpaid', 'Pending'),
(3, 3, '2024-04-11', 22.00, 'Paid', 'Shipped'),
(4, 3, '2024-04-12', 10.99, 'Paid', 'Delivered'),
(5, 5, '2024-04-13', 13.75, 'Paid', 'Processing'),
(6, 6, '2024-04-14', 17.80, 'Unpaid', 'Cancelled'),
(7, 6, '2024-04-14', 28.00, 'Paid', 'Delivered'),
(8, 8, '2024-04-15', 26.49, 'Paid', 'Delivered'),
(9, 9, '2024-04-16', 36.75, 'Paid', 'Pending'),
(10, 10, '2024-04-16', 13.25, 'Paid', 'Delivered'),
(11, 11, '2024-04-17', 12.99, 'Unpaid', 'Pending'),
(12, 6, '2024-04-17', 25.94, 'Paid', 'Shipped'),
(13, 13, '2024-04-18', 24.55, 'Paid', 'Delivered'),
(14, 14, '2024-04-18', 27.50, 'Paid', 'Delivered'),
(15, 6, '2024-04-19', 29.95, 'Unpaid', 'Processing'),
(16, 18, '2024-04-19', 14.00, 'Paid', 'Delivered'),
(17, 8, '2024-04-20', 31.80, 'Paid', 'Shipped'),
(18, 18, '2024-04-21', 15.45, 'Paid', 'Delivered');


INSERT INTO Order_Items VALUES
(1, 1, 1, 1, 12.99, 12.99),
(2, 1, 2, 1, 12.99, 12.99),
(3, 2, 2, 1, 15.50, 15.50),
(4, 3, 3, 2, 11.00, 22.00),
(5, 4, 4, 1, 10.99, 10.99),
(6, 5, 5, 1, 13.75, 13.75),
(7, 6, 6, 1, 17.80, 17.80),
(8, 7, 3, 2, 11.00, 22.00),
(9, 7, 8, 1, 6.00, 6.00),
(10, 8, 9, 1, 13.49, 13.49),
(11, 8, 10, 1, 12.99, 12.99),
(12, 9, 11, 1, 14.25, 14.25),
(13, 9, 5, 2, 11.25, 22.50),
(14, 10, 14, 1, 13.25, 13.25),
(15, 11, 15, 1, 12.99, 12.99),
(16, 12, 16, 2, 12.97, 25.94),
(17, 13, 17, 1, 11.60, 11.60),
(18, 13, 18, 1, 12.95, 12.95);


INSERT INTO Reviews VALUES
(1, 1, 1, 5, 'Amazing book!', '01-04-2024'),
(2, 2, 2, 4, 'Very helpful.', '01-04-2024'),
(3, 3, 3, 3, 'Quite interesting.', '02-04-2024'),
(4, 4, 4, 5, 'Loved the story.', '02-04-2024'),
(5, 5, 5, 4, 'Motivating read.', '03-04-2024'),
(6, 6, 6, 5, 'Highly recommended.', '03-04-2024'),
(7, 7, 7, 3, 'Good but slow.', '04-04-2024'),
(8, 8, 8, 2, 'Not as expected.', '04-04-2024'),
(9, 9, 9, 5, 'Masterpiece!', '05-04-2024'),
(10, 10, 10, 4, 'Emotional journey.', '05-04-2024'),
(11, 11, 11, 3, 'Informative.', '06-04-2024'),
(12, 12, 12, 4, 'Thrilling!', '06-04-2024'),
(13, 13, 13, 5, 'Best in the series.', '07-04-2024'),
(14, 14, 14, 4, 'Great plot.', '07-04-2024'),
(15, 15, 15, 5, 'Deeply touching.', '08-04-2024'),
(16, 16, 16, 4, 'Lovely writing.', '08-04-2024'),
(17, 17, 17, 2, 'Confusing ending.', '09-04-2024'),
(18, 18, 18, 5, 'Truly inspiring.', '09-04-2024');


select * from Books; -- Shows all book records.

SELECT * FROM Customers; -- Shows all customer records

SELECT * FROM Orders ; -- Shows all order records

SELECT * FROM Categories; -- Shows all book categories

SELECT * FROM Admins; -- Shows all admin users

SELECT * FROM Reviews; -- Shows all book reviews

SELECT * FROM Order_Items; -- Shows all items included in orders

SELECT * FROM Orders WHERE order_date BETWEEN '2024-04-17' AND '2024-04-30'; -- Shows orders placed between April 17 and April 30, 2024

SELECT * FROM Books WHERE stock < 15; -- Shows books with stock less than 15

SELECT * FROM Admins WHERE role = 'Manager'; -- Shows all admins with the role "Manager"

SELECT customer_id,total_amount,Payment_status FROM Orders WHERE delivery_status = 'Delivered'; -- Shows total amount and payment status for delivered orders

SELECT title, price FROM Books; -- Shows book titles and their prices.

SELECT book_id, AVG(rating) AS avg_rating FROM Reviews GROUP BY book_id; -- Shows average rating for each book

SELECT COUNT(*) AS total_categories FROM Categories; -- Shows total number of categories.

SELECT customer_id, COUNT(*) AS total_orders FROM Orders GROUP BY customer_id; -- Shows number of orders placed by each customer.

SELECT Genre , count(Genre) as Quantity from Books GROUP BY(Genre); -- Shows number of books in each genre.

SELECT customer_id, SUM(total_amount) AS total_spent FROM Orders GROUP BY customer_id ; -- Shows total money spent by each customer.


ALTER TABLE Customers 
ADD column preferred_genre VARCHAR(50); -- Adds a new column preferred_genre to the Customers table.
UPDATE Customers SET preferred_genre = 'Fiction' WHERE customer_id = 1; -- Sets each customer's preferred genre based on their ID.
UPDATE Customers SET preferred_genre = 'Self-help' WHERE customer_id = 2;
UPDATE Customers SET preferred_genre = 'Mystery' WHERE customer_id = 3;
UPDATE Customers SET preferred_genre = 'Drama' WHERE customer_id = 4;
UPDATE Customers SET preferred_genre = 'Romance' WHERE customer_id = 5;
UPDATE Customers SET preferred_genre = 'Science' WHERE customer_id = 6;
UPDATE Customers SET preferred_genre = 'Thriller' WHERE customer_id = 7;
UPDATE Customers SET preferred_genre = 'History' WHERE customer_id = 8;
UPDATE Customers SET preferred_genre = 'Classic' WHERE customer_id = 9;
UPDATE Customers SET preferred_genre = 'Poetry' WHERE customer_id = 10;
UPDATE Customers SET preferred_genre = 'Technology' WHERE customer_id = 11;
UPDATE Customers SET preferred_genre = 'Biography' WHERE customer_id = 12;
UPDATE Customers SET preferred_genre = 'Philosophy' WHERE customer_id = 13;
UPDATE Customers SET preferred_genre = 'Dystopian' WHERE customer_id = 14;
UPDATE Customers SET preferred_genre = 'Religion' WHERE customer_id = 15;
UPDATE Customers SET preferred_genre = 'Finance' WHERE customer_id = 16;
UPDATE Customers SET preferred_genre = 'Fiction' WHERE customer_id = 17;
UPDATE Customers SET preferred_genre = 'Romance' WHERE customer_id = 18;
SELECT Name, Address as District, registration_date, preferred_genre FROM Customers; -- Shows customers' name, district, registration date, and preferred genre

SELECT * FROM Customers WHERE customer_id IN (SELECT customer_id FROM Orders); -- Shows customers who have placed at least one order

SELECT book_id,title,Genre FROM Books WHERE book_id IN (SELECT book_id FROM Reviews); -- Shows details of books that have reviews

SELECT * FROM Books WHERE price < (SELECT AVG(price) FROM Books); -- Shows books priced below the average book price.

SELECT book_id, AVG(rating) AS avg_rating 
FROM Reviews 
GROUP BY book_id 
ORDER BY avg_rating DESC
LIMIT 8; -- Shows the top 8 highest-rated books.

```
## 🧠 Conclusion
This project demonstrates the core concepts of database design and SQL querying in a real-world context. It is suitable for academic use, small business prototypes, or further development into a complete bookstore management system.
