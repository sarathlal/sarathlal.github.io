---
layout: post
title:  SQL From Basics to Mastery — A Complete, Hands-On Guide
tags:
  - SQL
  - database
---

SQL (Structured Query Language) is the standard language for working with relational databases.
Whether you’re managing application data, generating reports, or analyzing business information, SQL gives you the tools to store, retrieve, and manipulate data efficiently.

This guide takes you from the basics to advanced SQL concepts in a practical, step-by-step way.
Each section includes examples you can run immediately, so you can learn by doing. By following along, you’ll build a strong foundation and be ready to handle real-world database tasks confidently.

## Chapter 1 — Getting Started with SQL

### 1.1 — What is SQL?

SQL (**Structured Query Language**) is the language we use to:

* **Create** databases and tables.
* **Insert** new records.
* **Retrieve** data.
* **Update** existing records.
* **Delete** unwanted data.

Almost every database — MySQL, PostgreSQL, SQLite, SQL Server — uses SQL with slight variations.

---

### 1.2 — Creating a Database

```sql
CREATE DATABASE shop;
```

> Some playgrounds already have a default database — if so, skip this step.

---

### 1.3 — Creating a Table

We’ll create a `customers` table:

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50),
    age INT
);
```

**Explanation:**

* `id` → Whole number, unique for each customer (`PRIMARY KEY`).
* `name` → Up to 50 characters.
* `city` → Up to 50 characters.
* `age` → Whole number.

---

### 1.4 — Inserting Data

```sql
INSERT INTO customers (id, name, city, age)
VALUES
(1, 'John Doe', 'New York', 30),
(2, 'Mary Smith', 'London', 25),
(3, 'Ravi Kumar', 'Mumbai', 28),
(4, 'Anita Sharma', 'Mumbai', 32);
```

---

### 1.5 — Viewing Data

```sql
SELECT * FROM customers;
```

**`*`** means all columns.

---

### 1.6 — Updating Data

Let’s update a customer’s city:

```sql
UPDATE customers
SET city = 'Delhi'
WHERE id = 3;
```

---

### 1.7 — Deleting Data

Remove a customer:

```sql
DELETE FROM customers
WHERE id = 4;
```

---

### 1.8 — Dropping a Table

Delete the entire table (use with caution!):

```sql
DROP TABLE customers;
```

---

### 1.9 — Key Points

* **SQL keywords** are case-insensitive (`SELECT` = `select`), but uppercase improves readability.
* Every statement ends with a **semicolon** (`;`).
* Always use `WHERE` in `UPDATE` and `DELETE` unless you want to affect *all* rows.

---

### 1.10 — Practice Tasks

Try these in your SQL playground:

1. Create a `products` table with:

   * `id` (int, primary key)
   * `name` (varchar, 50)
   * `price` (decimal)
   * `stock` (int)
2. Insert 3–4 sample products.
3. Update the price of one product.
4. Delete one product from the table.
5. Select all products and confirm changes.

---

## Chapter 2 — Basic Data Retrieval

### 2.1 — Selecting All Columns

```sql
SELECT * FROM customers;
```

* `*` means “all columns”.
* This is fine for quick checks but not best practice in real apps (select only needed columns for performance).

---

### 2.2 — Selecting Specific Columns

```sql
SELECT name, city FROM customers;
```

* Only returns the `name` and `city` columns.

---

### 2.3 — Filtering Rows with `WHERE`

Get customers from Mumbai:

```sql
SELECT * FROM customers
WHERE city = 'Mumbai';
```

Get customers older than 27:

```sql
SELECT * FROM customers
WHERE age > 27;
```

---

### 2.4 — Comparison Operators

| Operator     | Meaning                  |
| ------------ | ------------------------ |
| `=`          | Equal to                 |
| `<>` or `!=` | Not equal to             |
| `<`          | Less than                |
| `>`          | Greater than             |
| `<=`         | Less than or equal to    |
| `>=`         | Greater than or equal to |

Example — customers not from London:

```sql
SELECT * FROM customers
WHERE city <> 'London';
```

---

### 2.5 — Filtering Text with `LIKE`

`LIKE` is used for pattern matching:

* `%` = any number of characters
* `_` = exactly one character

Example — names starting with 'M':

```sql
SELECT * FROM customers
WHERE name LIKE 'M%';
```

Example — names with 'ar' anywhere:

```sql
SELECT * FROM customers
WHERE name LIKE '%ar%';
```

---

### 2.6 — Sorting Results with `ORDER BY`

Sort customers by age (youngest first):

```sql
SELECT * FROM customers
ORDER BY age ASC;
```

Sort by name in reverse alphabetical order:

```sql
SELECT * FROM customers
ORDER BY name DESC;
```

---

### 2.7 — Limiting Results

Get the first 2 customers:

```sql
SELECT * FROM customers
LIMIT 2;
```

Get 2 customers starting from the 3rd row:

```sql
SELECT * FROM customers
LIMIT 2 OFFSET 2;
```

---

### 2.8 — Combining Filters and Sorting

```sql
SELECT name, city, age
FROM customers
WHERE city = 'Mumbai'
ORDER BY age DESC;
```

---

### 2.9 — Practice Tasks

1. Select only `name` and `age` of customers older than 28.
2. Find customers whose names contain `'it'` anywhere.
3. Get the 3 youngest customers (sorted by age).
4. List customers from Mumbai or London, sorted by name.
5. Get only the first customer in alphabetical order.

---

## Chapter 3 — Working with Conditions

### 3.1 — Combining Conditions with `AND` and `OR`

Get customers from Mumbai **and** older than 30:

```sql
SELECT * FROM customers
WHERE city = 'Mumbai' AND age > 30;
```

Get customers from Mumbai **or** London:

```sql
SELECT * FROM customers
WHERE city = 'Mumbai' OR city = 'London';
```

> **Tip:** `AND` has higher priority than `OR`, so use parentheses for clarity:

```sql
WHERE (city = 'Mumbai' OR city = 'London') AND age > 25;
```

---

### 3.2 — Matching Multiple Values with `IN` / `NOT IN`

Get customers from Mumbai, London, or New York:

```sql
SELECT * FROM customers
WHERE city IN ('Mumbai', 'London', 'New York');
```

Exclude those cities:

```sql
SELECT * FROM customers
WHERE city NOT IN ('Mumbai', 'London', 'New York');
```

---

### 3.3 — Filtering with Ranges using `BETWEEN`

Find customers aged between 25 and 30 (inclusive):

```sql
SELECT * FROM customers
WHERE age BETWEEN 25 AND 30;
```

---

### 3.4 — Handling `NULL` Values

`NULL` means "no value" — it’s **not** the same as 0 or an empty string.

Find customers with no city:

```sql
SELECT * FROM customers
WHERE city IS NULL;
```

Find customers where age is known:

```sql
SELECT * FROM customers
WHERE age IS NOT NULL;
```

---

### 3.5 — Combining Multiple Techniques

Example — customers from Mumbai or London **and** age is between 25 and 30:

```sql
SELECT * FROM customers
WHERE city IN ('Mumbai', 'London')
  AND age BETWEEN 25 AND 30;
```

---

### 3.6 — Practice Tasks

1. Find customers **not** from Mumbai or London.
2. Get customers whose city is **unknown** (`NULL`).
3. Find customers aged **greater than 27** and **not from New York**.
4. List customers aged **25 to 30** from **Mumbai or London**.
5. Show customers whose age is unknown but have a city name.

---


## Chapter 4 — Mastering JOINs

### 4.0 — Setup: Create Tables and Sample Data

#### `customers` table

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50),
    age INT
);

INSERT INTO customers (id, name, city, age) VALUES
(1, 'John Doe', 'New York', 30),
(2, 'Mary Smith', 'London', 25),
(3, 'Ravi Kumar', 'Mumbai', 28),
(4, 'Anita Sharma', 'Mumbai', 32),
(5, 'Raj Patel', NULL, NULL);
```

---

#### `orders` table

```sql
CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    product VARCHAR(50),
    price DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

INSERT INTO orders (id, customer_id, product, price) VALUES
(1, 1, 'Laptop', 800.00),
(2, 1, 'Mouse', 20.00),
(3, 2, 'Keyboard', 50.00),
(4, 3, 'Laptop', 900.00),
(5, 3, 'Mouse', 25.00),
(6, 4, 'Monitor', 300.00);
```

---

### 4.1 — INNER JOIN

Returns rows where there is a match in both tables.

```sql
SELECT customers.name, customers.city, orders.product, orders.price
FROM customers
INNER JOIN orders
ON customers.id = orders.customer_id;
```

**Result:**

| name         | city     | product  | price  |
| ------------ | -------- | -------- | ------ |
| John Doe     | New York | Laptop   | 800.00 |
| John Doe     | New York | Mouse    | 20.00  |
| Mary Smith   | London   | Keyboard | 50.00  |
| Ravi Kumar   | Mumbai   | Laptop   | 900.00 |
| Ravi Kumar   | Mumbai   | Mouse    | 25.00  |
| Anita Sharma | Mumbai   | Monitor  | 300.00 |

---

### 4.2 — LEFT JOIN

Returns **all rows** from the left table (customers), even if no matching orders exist.

```sql
SELECT customers.name, orders.product, orders.price
FROM customers
LEFT JOIN orders
ON customers.id = orders.customer_id;
```

**Note:** Raj Patel will appear with `NULL` for product & price.

---

### 4.3 — RIGHT JOIN

Returns **all rows** from the right table (orders), even if no matching customer exists.
(Not supported in SQLite — works in MySQL/PostgreSQL.)

```sql
SELECT customers.name, orders.product, orders.price
FROM customers
RIGHT JOIN orders
ON customers.id = orders.customer_id;
```

---

### 4.4 — FULL OUTER JOIN

Returns **all rows** from both tables, matched where possible.
(PostgreSQL supports it; MySQL requires `UNION` trick.)

```sql
SELECT customers.name, orders.product, orders.price
FROM customers
FULL OUTER JOIN orders
ON customers.id = orders.customer_id;
```

---

### 4.5 — SELF JOIN

A table joins with itself (e.g., employees & their managers).
Let’s make an example:

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    manager_id INT
);

INSERT INTO employees (id, name, manager_id) VALUES
(1, 'Alice', NULL),
(2, 'Bob', 1),
(3, 'Charlie', 1),
(4, 'David', 2);

SELECT e1.name AS employee, e2.name AS manager
FROM employees e1
LEFT JOIN employees e2
ON e1.manager_id = e2.id;
```

---

### 4.6 — Joining More Than Two Tables

```sql
-- Create a products table
CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(50)
);

INSERT INTO products (id, name) VALUES
(1, 'Laptop'),
(2, 'Mouse'),
(3, 'Keyboard'),
(4, 'Monitor');

-- Join customers → orders → products
SELECT customers.name, products.name AS product_name, orders.price
FROM customers
JOIN orders ON customers.id = orders.customer_id
JOIN products ON orders.product = products.name;
```

---

### 4.7 — Practice Tasks

1. List all customers and their orders, showing `NULL` if no orders exist.
2. Show only customers who have placed at least one order.
3. Find total spending **per customer** (use `SUM` with `GROUP BY`).
4. List each employee with their manager’s name.
5. Join customers, orders, and products into one result set.

---

## Chapter 5 — Aggregate Functions & Grouping (Updated)

### 5.0 — Setup: Creating Sample Tables

#### `customers` table

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50),
    age INT
);

INSERT INTO customers (id, name, city, age) VALUES
(1, 'John Doe', 'New York', 30),
(2, 'Mary Smith', 'London', 25),
(3, 'Ravi Kumar', 'Mumbai', 28),
(4, 'Anita Sharma', 'Mumbai', 32),
(5, 'Raj Patel', NULL, NULL);
```

#### `orders` table

```sql
CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    product VARCHAR(50),
    price DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

INSERT INTO orders (id, customer_id, product, price) VALUES
(1, 1, 'Laptop', 800.00),
(2, 1, 'Mouse', 20.00),
(3, 2, 'Keyboard', 50.00),
(4, 3, 'Laptop', 900.00),
(5, 3, 'Mouse', 25.00),
(6, 4, 'Monitor', 300.00);
```

---

### 5.1 — COUNT

Count rows in a table:

```sql
SELECT COUNT(*) AS total_customers
FROM customers;
```

Count orders placed:

```sql
SELECT COUNT(*) AS total_orders
FROM orders;
```

---

### 5.2 — SUM

Total sales from all orders:

```sql
SELECT SUM(price) AS total_sales
FROM orders;
```

---

### 5.3 — AVG

Average age of customers:

```sql
SELECT AVG(age) AS avg_age
FROM customers;
```

---

### 5.4 — MIN & MAX

Youngest and oldest customer:

```sql
SELECT MIN(age) AS youngest, MAX(age) AS oldest
FROM customers;
```

---

### 5.5 — GROUP BY

Total orders per customer:

```sql
SELECT customer_id, COUNT(*) AS order_count
FROM orders
GROUP BY customer_id;
```

Total sales per customer:

```sql
SELECT customer_id, SUM(price) AS total_spent
FROM orders
GROUP BY customer_id;
```

---

### 5.5.1 — Combining Values into One Cell (String Aggregation)

Sometimes we want **all products bought by a customer in one row**.
We can use:

* `GROUP_CONCAT` → MySQL/MariaDB
* `STRING_AGG` → PostgreSQL/SQL Server

**MySQL Example:**

```sql
SELECT c.name AS customer_name,
       GROUP_CONCAT(o.product ORDER BY o.product SEPARATOR ', ') AS products_bought
FROM customers c
JOIN orders o ON c.id = o.customer_id
GROUP BY c.name;
```

**PostgreSQL Example:**

```sql
SELECT c.name AS customer_name,
       STRING_AGG(o.product, ', ' ORDER BY o.product) AS products_bought
FROM customers c
JOIN orders o ON c.id = o.customer_id
GROUP BY c.name;
```

---

### 5.6 — GROUP BY with Multiple Columns

Example: total products bought per customer per city:

```sql
SELECT c.city, c.name, COUNT(*) AS total_products
FROM orders o
JOIN customers c ON c.id = o.customer_id
GROUP BY c.city, c.name;
```

---

### 5.7 — HAVING

Filter grouped results — customers who spent more than \$500:

```sql
SELECT customer_id, SUM(price) AS total_spent
FROM orders
GROUP BY customer_id
HAVING SUM(price) > 500;
```

---

### 5.8 — GROUP BY + ORDER BY

Top customers by spending:

```sql
SELECT customer_id, SUM(price) AS total_spent
FROM orders
GROUP BY customer_id
ORDER BY total_spent DESC;
```

---

### 5.9 — Practice Tasks

1. Count customers from Mumbai.
2. List all products bought by each customer (single row per customer).
3. Show total spending per city.
4. Find customers who bought more than 1 product.
5. Get the highest spending customer.

---

## Chapter 6 — Subqueries & CTEs

Subqueries and Common Table Expressions (CTEs) let you **break complex problems into smaller steps**.
Instead of writing a huge, hard-to-read query, you can:

* Use a **subquery** inside another query.
* Use a **CTE** to give a temporary name to a query result and reuse it.

---

### 6.0 — Setup: Create Tables and Data

#### `customers` table

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50),
    age INT
);

INSERT INTO customers (id, name, city, age) VALUES
(1, 'John Doe', 'New York', 30),
(2, 'Mary Smith', 'London', 25),
(3, 'Ravi Kumar', 'Mumbai', 28),
(4, 'Anita Sharma', 'Mumbai', 32),
(5, 'Raj Patel', NULL, NULL);
```

---

#### `orders` table

```sql
CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    product VARCHAR(50),
    price DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

INSERT INTO orders (id, customer_id, product, price) VALUES
(1, 1, 'Laptop', 800.00),
(2, 1, 'Mouse', 20.00),
(3, 2, 'Keyboard', 50.00),
(4, 3, 'Laptop', 900.00),
(5, 3, 'Mouse', 25.00),
(6, 4, 'Monitor', 300.00);
```

---

### 6.1 — What is a Subquery?

A subquery is a query **inside parentheses** used as part of another query.

---

#### 6.2 — Subquery in WHERE

Find customers who spent more than \$500:

```sql
SELECT name
FROM customers
WHERE id IN (
    SELECT customer_id
    FROM orders
    GROUP BY customer_id
    HAVING SUM(price) > 500
);
```

---

#### 6.3 — Subquery in SELECT

Show each customer with their total spending:

```sql
SELECT name,
       (SELECT SUM(price)
        FROM orders
        WHERE orders.customer_id = customers.id) AS total_spent
FROM customers;
```

---

#### 6.4 — Subquery in FROM

First, get total spending per customer, then filter:

```sql
SELECT *
FROM (
    SELECT customer_id, SUM(price) AS total_spent
    FROM orders
    GROUP BY customer_id
) AS spending
WHERE total_spent > 500;
```

---

### 6.5 — What is a CTE?

A **Common Table Expression** starts with `WITH`.
It creates a temporary, named result that can be used in the main query.

---

#### 6.6 — Simple CTE

```sql
WITH spending AS (
    SELECT customer_id, SUM(price) AS total_spent
    FROM orders
    GROUP BY customer_id
)
SELECT customer_id, total_spent
FROM spending
WHERE total_spent > 500;
```

---

#### 6.7 — Multiple CTEs

```sql
WITH spending AS (
    SELECT customer_id, SUM(price) AS total_spent
    FROM orders
    GROUP BY customer_id
),
customer_info AS (
    SELECT id, name, city
    FROM customers
)
SELECT c.name, c.city, s.total_spent
FROM customer_info c
JOIN spending s ON c.id = s.customer_id;
```

---

#### 6.8 — Recursive CTE

Useful for hierarchical data like categories or org charts.

Example: an employee hierarchy:

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    manager_id INT
);

INSERT INTO employees (id, name, manager_id) VALUES
(1, 'Alice', NULL),
(2, 'Bob', 1),
(3, 'Charlie', 1),
(4, 'David', 2);

WITH RECURSIVE hierarchy AS (
    SELECT id, name, manager_id, 0 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    SELECT e.id, e.name, e.manager_id, h.level + 1
    FROM employees e
    JOIN hierarchy h ON e.manager_id = h.id
)
SELECT * FROM hierarchy;
```

---

### 6.9 — Practice Tasks

1. Find customers who have **never placed an order** using a subquery.
2. Use a subquery in `SELECT` to show each customer’s **average order price**.
3. Write a CTE to get the **top 3 customers by spending**.
4. Write a CTE that lists customers **and** the number of products they bought.
5. Use a recursive CTE to find **all employees under Bob**.

---

## Chapter 7 — Data Modification

This chapter covers:

* Adding new data (**INSERT**)
* Changing existing data (**UPDATE**)
* Removing data (**DELETE**)
* Copying data between tables (**INSERT … SELECT**)
* Safeguards to prevent accidental data loss

---

### 7.0 — Setup: Create Tables and Data

#### `customers` table

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50),
    age INT
);

INSERT INTO customers (id, name, city, age) VALUES
(1, 'John Doe', 'New York', 30),
(2, 'Mary Smith', 'London', 25),
(3, 'Ravi Kumar', 'Mumbai', 28);
```

---

#### **`orders` table**

```sql
CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    product VARCHAR(50),
    price DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

INSERT INTO orders (id, customer_id, product, price) VALUES
(1, 1, 'Laptop', 800.00),
(2, 1, 'Mouse', 20.00),
(3, 2, 'Keyboard', 50.00);
```

---

### 7.1 — INSERT: Adding Data

Insert a single customer:

```sql
INSERT INTO customers (id, name, city, age)
VALUES (4, 'Anita Sharma', 'Mumbai', 32);
```

Insert multiple customers at once:

```sql
INSERT INTO customers (id, name, city, age) VALUES
(5, 'Raj Patel', 'Delhi', 29),
(6, 'Sara Khan', 'Bangalore', 27);
```

---

### 7.2 — UPDATE: Changing Data

Change a customer’s city:

```sql
UPDATE customers
SET city = 'Delhi'
WHERE id = 3;
```

Change multiple fields:

```sql
UPDATE customers
SET city = 'Chennai', age = 33
WHERE name = 'Anita Sharma';
```

Increase all product prices by 10%:

```sql
UPDATE orders
SET price = price * 1.10;
```

⚠️ Always use `WHERE` unless you truly want to update every row.

---

### 7.3 — DELETE: Removing Data

Delete one customer:

```sql
DELETE FROM customers
WHERE id = 5;
```

Delete all orders for a customer:

```sql
DELETE FROM orders
WHERE customer_id = 1;
```

⚠️ Without `WHERE`, all rows will be deleted:

```sql
DELETE FROM customers; -- removes all customers!
```

---

### 7.4 — INSERT … SELECT: Copying Data

Create an archive table:

```sql
CREATE TABLE orders_archive (
    id INT,
    customer_id INT,
    product VARCHAR(50),
    price DECIMAL(10,2)
);
```

Copy orders above \$100 into the archive:

```sql
INSERT INTO orders_archive (id, customer_id, product, price)
SELECT id, customer_id, product, price
FROM orders
WHERE price > 100;
```

---

### 7.5 — Practice Tasks

1. Add two new customers to the table.
2. Change the city for "Mary Smith" to "Paris".
3. Increase prices of all products under \$100 by 20%.
4. Delete all customers from "Delhi".
5. Create a `high_value_orders` table and copy all orders over \$500 into it.

---

## Chapter 8 — Constraints & Data Integrity

**Constraints** are rules that ensure data in your database is **valid, consistent, and reliable**.
They prevent things like:

* Duplicate entries where they shouldn’t exist
* Missing required information
* Invalid references between tables

We’ll cover:

* `PRIMARY KEY`
* `FOREIGN KEY`
* `UNIQUE`
* `NOT NULL`
* `CHECK`
* `DEFAULT`

---

### 8.0 — Setup: Creating Example Tables

#### `customers` table with constraints

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,             -- Must be unique, cannot be NULL
    name VARCHAR(50) NOT NULL,      -- Must have a value
    email VARCHAR(100) UNIQUE,      -- Must be unique
    city VARCHAR(50) DEFAULT 'Unknown',  -- Defaults if not provided
    age INT CHECK (age >= 18)       -- Must be at least 18
);

INSERT INTO customers (id, name, email, city, age) VALUES
(1, 'John Doe', 'john@example.com', 'New York', 30),
(2, 'Mary Smith', 'mary@example.com', 'London', 25);
```

---

#### `orders` table with FOREIGN KEY

```sql
CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    product VARCHAR(50) NOT NULL,
    price DECIMAL(10,2) CHECK (price > 0),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

INSERT INTO orders (id, customer_id, product, price) VALUES
(1, 1, 'Laptop', 800.00),
(2, 2, 'Mouse', 20.00);
```

---

### 8.1 — PRIMARY KEY

* Ensures each row is **unique** and **not NULL**.
* Example: `id` in both `customers` and `orders` tables.

If you try to insert a duplicate:

```sql
INSERT INTO customers (id, name, email, age)
VALUES (1, 'Duplicate ID', 'dup@example.com', 30);
-- ERROR: Duplicate entry for PRIMARY KEY
```

---

### 8.2 — UNIQUE

* Prevents duplicate values in a column.
* Example: `email` in customers table.

```sql
INSERT INTO customers (id, name, email, age)
VALUES (3, 'Ravi Kumar', 'john@example.com', 28);
-- ERROR: Duplicate email not allowed
```

---

### 8.3 — NOT NULL

* Requires a value.
* Example: `name` in customers table.

```sql
INSERT INTO customers (id, name, email, age)
VALUES (3, NULL, 'ravi@example.com', 28);
-- ERROR: name cannot be NULL
```

---

### 8.4 — DEFAULT

* Sets a value if none is given.
* Example: `city` defaults to 'Unknown'.

```sql
INSERT INTO customers (id, name, email, age)
VALUES (3, 'Ravi Kumar', 'ravi@example.com', 28);

SELECT * FROM customers WHERE id = 3;
-- city will show 'Unknown'
```

---

### 8.5 — CHECK

* Ensures a condition is met.
* Example: `age >= 18` in customers table.

```sql
INSERT INTO customers (id, name, email, city, age)
VALUES (4, 'Anita Sharma', 'anita@example.com', 'Mumbai', 15);
-- ERROR: Age must be at least 18
```

---

### 8.6 — FOREIGN KEY

* Creates a link between tables.
* Example: `customer_id` in orders must exist in customers.

```sql
INSERT INTO orders (id, customer_id, product, price)
VALUES (3, 99, 'Keyboard', 50.00);
-- ERROR: customer_id 99 does not exist in customers
```

---

### 8.7 — Practice Tasks

1. Try inserting a duplicate `id` in customers.
2. Try inserting a duplicate email in customers.
3. Insert a new customer **without** specifying the city — check the default.
4. Try inserting a customer under age 18.
5. Try inserting an order with a `customer_id` that doesn’t exist.

---

## Chapter 9 — Indexes & Performance

Indexes are **special data structures** that make queries faster — especially searches, sorting, and filtering.
They work like an index in a book: instead of scanning every page, the database jumps directly to the location of the data.

---

### 9.0 — Setup: Create Tables and Data

#### `customers` table

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50),
    age INT
);

-- Insert 10,000 sample rows for performance testing
INSERT INTO customers (id, name, city, age)
SELECT seq, CONCAT('Customer ', seq),
       CASE WHEN seq % 3 = 0 THEN 'Mumbai'
            WHEN seq % 3 = 1 THEN 'London'
            ELSE 'New York' END,
       20 + (seq % 30)
FROM generate_series(1, 10000) AS seq; -- PostgreSQL syntax
```

> **Note:** If your SQL playground doesn’t support `generate_series`,
> you can insert fewer rows manually — the indexing concept works the same.

---

### 9.1 — How Queries Work Without Indexes

If you search without an index:

```sql
SELECT * FROM customers
WHERE city = 'Mumbai';
```

The database scans **every row** — called a **full table scan**.

---

### 9.2 — Creating an Index

Create an index on `city`:

```sql
CREATE INDEX idx_customers_city
ON customers(city);
```

Now the database can **jump directly** to rows where `city = 'Mumbai'`.

---

### 9.3 — Multi-Column Index

If you often search by `city` **and** `age` together:

```sql
CREATE INDEX idx_customers_city_age
ON customers(city, age);
```

This is more efficient than two separate indexes in some cases.

---

### 9.4 — Unique Index

A `UNIQUE` constraint is actually a special type of index:

```sql
CREATE UNIQUE INDEX idx_customers_name_city
ON customers(name, city);
```

This prevents duplicate name+city combinations.

---

### 9.5 — Dropping an Index

```sql
DROP INDEX idx_customers_city;
```

*(Some databases require `DROP INDEX ON customers idx_name` syntax.)*

---

### 9.6 — Viewing Indexes

* **PostgreSQL**:

```sql
\d customers;
```

* **MySQL**:

```sql
SHOW INDEXES FROM customers;
```

---

### 9.7 — When NOT to Use Indexes

* On small tables (overhead may outweigh speed benefit)
* On columns with very few distinct values (e.g., a boolean field)
* On frequently updated columns (indexes slow down `INSERT`/`UPDATE`/`DELETE`)

---

### 9.8 — Practice Tasks

1. Create an index on `age` and test queries before & after.
2. Create a multi-column index on `city` and `name`.
3. Drop an index you created.
4. Try running a search with and without an index and compare execution speed (if your playground supports `EXPLAIN`).
5. Create a unique index to prevent duplicate customers in the same city.

---


## Chapter 10 — Advanced SQL with Window Functions

**Window functions** let you perform calculations **across a set of rows** that are related to the current row, without collapsing them into a single result like `GROUP BY` does.
They’re very useful for:

* Ranking
* Running totals
* Moving averages
* Percentiles

---

### 10.0 — Setup: Create Tables and Data

#### `orders` table

```sql
CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_name VARCHAR(50),
    order_date DATE,
    amount DECIMAL(10,2)
);

INSERT INTO orders (id, customer_name, order_date, amount) VALUES
(1, 'John Doe', '2024-01-05', 500.00),
(2, 'Mary Smith', '2024-01-06', 300.00),
(3, 'John Doe', '2024-01-10', 200.00),
(4, 'Mary Smith', '2024-01-15', 450.00),
(5, 'Ravi Kumar', '2024-01-16', 700.00),
(6, 'John Doe', '2024-01-20', 150.00),
(7, 'Ravi Kumar', '2024-01-22', 100.00);
```

---

### 10.1 — ROW\_NUMBER

Gives each row a unique number **within a partition** (group), ordered by some column.

```sql
SELECT customer_name, order_date, amount,
       ROW_NUMBER() OVER (PARTITION BY customer_name ORDER BY order_date) AS order_number
FROM orders;
```

💡 This shows **which order number** each customer placed chronologically.

---

### 10.2 — RANK

Ranks rows but **gives the same rank for ties**.

```sql
SELECT customer_name, amount,
       RANK() OVER (ORDER BY amount DESC) AS rank_amount
FROM orders;
```

---

### 10.3 — DENSE\_RANK

Like `RANK`, but without gaps in ranking numbers.

```sql
SELECT customer_name, amount,
       DENSE_RANK() OVER (ORDER BY amount DESC) AS dense_rank_amount
FROM orders;
```

---

### 10.4 — Running Total

Cumulative sum of amounts per customer.

```sql
SELECT customer_name, order_date, amount,
       SUM(amount) OVER (PARTITION BY customer_name ORDER BY order_date) AS running_total
FROM orders;
```

---

### 10.5 — Moving Average

Average of the **current and previous row** (based on date).

```sql
SELECT customer_name, order_date, amount,
       AVG(amount) OVER (PARTITION BY customer_name ORDER BY order_date ROWS BETWEEN 1 PRECEDING AND CURRENT ROW) AS moving_avg
FROM orders;
```

---

### 10.6 — Percent Rank

Shows where a row stands **between 0 and 1** relative to others.

```sql
SELECT customer_name, amount,
       PERCENT_RANK() OVER (ORDER BY amount DESC) AS pct_rank
FROM orders;
```

---

### 10.7 — NTILE

Splits rows into **n buckets**.

Example — split into 3 revenue groups:

```sql
SELECT customer_name, amount,
       NTILE(3) OVER (ORDER BY amount DESC) AS revenue_group
FROM orders;
```

---

### 10.8 — Practice Tasks

1. Show each customer’s order list with `ROW_NUMBER` for order sequence.
2. Rank orders by `amount` for each customer using `RANK`.
3. Calculate a running total of `amount` for all customers combined.
4. Find the **moving average** of each customer’s spending over their last 2 orders.
5. Split all orders into 4 revenue quartiles using `NTILE`.

---

## Chapter 11 — Views & Stored Routines

**Views**

* A **saved query** that behaves like a virtual table.
* You can `SELECT` from it just like a normal table.
* Useful for simplifying complex queries and improving code readability.

**Stored Routines**

* **Stored Procedures** → reusable blocks of SQL code you can run with parameters.
* **Stored Functions** → like procedures, but return a single value.

---

### 11.0 — Setup: Create Tables and Data

```sql
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50)
);

CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    product VARCHAR(50),
    price DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

INSERT INTO customers (id, name, city) VALUES
(1, 'John Doe', 'New York'),
(2, 'Mary Smith', 'London'),
(3, 'Ravi Kumar', 'Mumbai');

INSERT INTO orders (id, customer_id, product, price) VALUES
(1, 1, 'Laptop', 800.00),
(2, 1, 'Mouse', 20.00),
(3, 2, 'Keyboard', 50.00),
(4, 3, 'Laptop', 900.00),
(5, 3, 'Mouse', 25.00);
```

---

### 11.1 — Creating a View

Example: total spending per customer.

```sql
CREATE VIEW customer_spending AS
SELECT c.id, c.name, c.city, SUM(o.price) AS total_spent
FROM customers c
JOIN orders o ON c.id = o.customer_id
GROUP BY c.id, c.name, c.city;
```

---

### 11.2 — Using a View

```sql
SELECT * FROM customer_spending;
```

This query is now simple because the complex join is inside the view.

---

### 11.3 — Updating a View

```sql
CREATE OR REPLACE VIEW customer_spending AS
SELECT c.id, c.name, c.city, SUM(o.price) AS total_spent, COUNT(o.id) AS order_count
FROM customers c
JOIN orders o ON c.id = o.customer_id
GROUP BY c.id, c.name, c.city;
```

---

### 11.4 — Dropping a View

```sql
DROP VIEW customer_spending;
```

---

### 11.5 — Stored Procedure *(MySQL syntax — PostgreSQL uses `CREATE PROCEDURE` with different calling syntax)*

Example: Get all orders for a given customer.

```sql
DELIMITER //
CREATE PROCEDURE GetCustomerOrders(IN cust_id INT)
BEGIN
    SELECT * FROM orders
    WHERE customer_id = cust_id;
END //
DELIMITER ;
```

Call the procedure:

```sql
CALL GetCustomerOrders(1);
```

---

### 11.6 — Stored Function

Example: Get total spending for a given customer.

```sql
DELIMITER //
CREATE FUNCTION TotalSpent(cust_id INT)
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    DECLARE total DECIMAL(10,2);
    SELECT SUM(price) INTO total
    FROM orders
    WHERE customer_id = cust_id;
    RETURN total;
END //
DELIMITER ;
```

Call the function:

```sql
SELECT TotalSpent(1) AS total_spent_by_customer;
```

---

### 11.7 — Practice Tasks

1. Create a view showing **city-wise total spending**.
2. Update the view to also show **number of customers in that city**.
3. Create a stored procedure that takes a **city name** and lists all customers from that city.
4. Create a stored function that returns the **average order price** for a given customer.
5. Drop a view you created.

---

## Chapter 12 — Transactions & Locks

### **What is a Transaction?**

A **transaction** is a group of SQL statements that run together as a single unit.
They follow the **ACID** principles:

* **A**tomic → all succeed or all fail
* **C**onsistent → keep data valid
* **I**solated → one transaction doesn’t affect another in progress
* **D**urable → changes are saved permanently once committed

---

### 12.0 — Setup: Create Tables and Data

```sql
CREATE TABLE accounts (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    balance DECIMAL(10,2)
);

INSERT INTO accounts (id, name, balance) VALUES
(1, 'John Doe', 1000.00),
(2, 'Mary Smith', 1500.00);
```

---

### 12.1 — Basic Transaction Example

We’ll transfer money from **John** to **Mary**.

```sql
START TRANSACTION;

UPDATE accounts
SET balance = balance - 200
WHERE id = 1;

UPDATE accounts
SET balance = balance + 200
WHERE id = 2;

COMMIT;
```

💡 If both updates succeed, we `COMMIT` to save changes.

---

### 12.2 — Rolling Back on Error

If something goes wrong, cancel all changes:

```sql
START TRANSACTION;

UPDATE accounts
SET balance = balance - 500
WHERE id = 1;

-- Simulating an error
UPDATE accounts
SET balance = balance + 500
WHERE id = 999; -- no such account

ROLLBACK;
```

💡 After `ROLLBACK`, balances stay the same as before the transaction.

---

### 12.3 — Savepoints

You can mark a point inside a transaction and roll back to it:

```sql
START TRANSACTION;

UPDATE accounts SET balance = balance - 100 WHERE id = 1;
SAVEPOINT after_first_update;

UPDATE accounts SET balance = balance + 100 WHERE id = 2;
-- If this update is wrong:
ROLLBACK TO after_first_update;

COMMIT;
```

---

### 12.4 — Locks

Locks prevent other transactions from changing the same data until you’re done.

Example: lock a row for update:

```sql
START TRANSACTION;

SELECT * FROM accounts
WHERE id = 1
FOR UPDATE;

-- Now update safely
UPDATE accounts SET balance = balance - 50 WHERE id = 1;

COMMIT;
```

💡 Other transactions trying to update `id = 1` will wait until this one finishes.

---

### 12.5 — Isolation Levels

Determines how transactions affect each other.

Common levels:

* **READ UNCOMMITTED** → can see uncommitted changes (dirty reads)
* **READ COMMITTED** → only see committed changes
* **REPEATABLE READ** → same result for repeated queries in one transaction
* **SERIALIZABLE** → highest isolation, transactions run one after another logically

Example in MySQL:

```sql
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
START TRANSACTION;
-- Your queries here
COMMIT;
```

---

### 12.6 — Practice Tasks

1. Transfer 300 from Mary to John inside a transaction and commit.
2. Transfer 100 from John to Mary but rollback instead of committing.
3. Use a savepoint to undo only part of a transaction.
4. Lock a customer record before updating it.
5. Experiment with different isolation levels and observe changes.

---

## Chapter 13 — Real-World Project: Mini E-commerce Database

In this chapter, we’ll:

1. **Design** a relational database for a small online store.
2. **Insert realistic sample data**.
3. **Write real-world queries** for reporting and analytics.

---

### 13.0 — Step 1: Create the Database Schema

```sql
-- Customers
CREATE TABLE customers (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    city VARCHAR(50),
    join_date DATE
);

-- Products
CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    category VARCHAR(50),
    price DECIMAL(10,2) CHECK (price > 0),
    stock INT CHECK (stock >= 0)
);

-- Orders
CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

-- Order Items (to handle multiple products per order)
CREATE TABLE order_items (
    id INT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT CHECK (quantity > 0),
    price DECIMAL(10,2) CHECK (price > 0),
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

---

### 13.1 — Step 2: Insert Sample Data

```sql
-- Customers
INSERT INTO customers (id, name, email, city, join_date) VALUES
(1, 'John Doe', 'john@example.com', 'New York', '2024-01-10'),
(2, 'Mary Smith', 'mary@example.com', 'London', '2024-02-15'),
(3, 'Ravi Kumar', 'ravi@example.com', 'Mumbai', '2024-03-05');

-- Products
INSERT INTO products (id, name, category, price, stock) VALUES
(1, 'Laptop', 'Electronics', 800.00, 10),
(2, 'Mouse', 'Electronics', 20.00, 100),
(3, 'Keyboard', 'Electronics', 50.00, 50),
(4, 'Monitor', 'Electronics', 300.00, 20),
(5, 'Desk Chair', 'Furniture', 150.00, 15);

-- Orders
INSERT INTO orders (id, customer_id, order_date) VALUES
(1, 1, '2024-03-10'),
(2, 1, '2024-03-15'),
(3, 2, '2024-03-20'),
(4, 3, '2024-03-25');

-- Order Items
INSERT INTO order_items (id, order_id, product_id, quantity, price) VALUES
(1, 1, 1, 1, 800.00),
(2, 1, 2, 2, 20.00),
(3, 2, 4, 1, 300.00),
(4, 3, 3, 1, 50.00),
(5, 4, 1, 1, 900.00),
(6, 4, 5, 2, 150.00);
```

---

### 13.2 — Step 3: Real-World Queries

#### 1. Sales Report per Product

```sql
SELECT p.name AS product_name,
       SUM(oi.quantity) AS total_sold,
       SUM(oi.quantity * oi.price) AS total_revenue
FROM order_items oi
JOIN products p ON oi.product_id = p.id
GROUP BY p.name
ORDER BY total_revenue DESC;
```

---

#### 2. Top Customers by Spending

```sql
SELECT c.name AS customer_name,
       SUM(oi.quantity * oi.price) AS total_spent
FROM customers c
JOIN orders o ON c.id = o.customer_id
JOIN order_items oi ON o.id = oi.order_id
GROUP BY c.name
ORDER BY total_spent DESC
LIMIT 5;
```

---

#### 3. Inventory Alert (Low Stock)

```sql
SELECT name, stock
FROM products
WHERE stock < 20
ORDER BY stock ASC;
```

---

#### 4. Monthly Sales Summary

```sql
SELECT DATE_FORMAT(o.order_date, '%Y-%m') AS month,
       SUM(oi.quantity * oi.price) AS monthly_revenue
FROM orders o
JOIN order_items oi ON o.id = oi.order_id
GROUP BY month
ORDER BY month;
```

*(Use `TO_CHAR(o.order_date, 'YYYY-MM')` in PostgreSQL.)*

---

#### 5. Customer Purchase History

```sql
SELECT c.name AS customer_name,
       o.order_date,
       p.name AS product_name,
       oi.quantity,
       oi.price
FROM customers c
JOIN orders o ON c.id = o.customer_id
JOIN order_items oi ON o.id = oi.order_id
JOIN products p ON oi.product_id = p.id
WHERE c.id = 1
ORDER BY o.order_date;
```

---

#### 6. Best-Selling Category

```sql
SELECT p.category,
       SUM(oi.quantity) AS total_sold
FROM order_items oi
JOIN products p ON oi.product_id = p.id
GROUP BY p.category
ORDER BY total_sold DESC
LIMIT 1;
```

---

### 13.3 — Step 4: Practice Tasks

1. Find the **average order value** for each customer.
2. List the **top 3 products** by quantity sold.
3. Show **total revenue per city**.
4. Get the **number of orders** each customer placed.
5. Find customers who bought products **from more than one category**.

You’ve now worked through SQL from the ground up — starting with simple queries and building up to joins, aggregations, subqueries, transactions, and real-world scenarios.

Along the way, you’ve learned how to combine, filter, and summarize data, as well as apply techniques to make queries faster and more reliable.

The best way to keep improving is to practice regularly.
Use these techniques on real data, try new query combinations, and explore the features of your database system. With consistent use, SQL will become a natural and powerful tool in your problem-solving toolkit.
