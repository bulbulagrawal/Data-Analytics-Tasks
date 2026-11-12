# Day 17 — Subqueries, UNION & CTEs

## Introduction

As a Data Analyst, you will often need to solve business problems that cannot be answered with a single simple `SELECT` statement.

For example:

- Which customers spend more than the average customer?
- Which products have never been sold?
- How can we combine sales data from two regions?
- How can we break a complex analysis into smaller, readable steps?

SQL provides several powerful tools for these situations:

- `UNION`
- `UNION ALL`
- Subqueries
- Correlated subqueries
- CTEs (Common Table Expressions)
- Multiple CTEs

---

# Sample Tables

We will use the following examples throughout this lesson.

## Customers

| customer_id | customer_name | city |
|---:|---|---|
| 101 | Amit | Indore |
| 102 | Priya | Mumbai |
| 103 | Rahul | Delhi |
| 104 | Neha | Pune |

## Orders

| order_id | customer_id | amount |
|---:|---:|---:|
| 1001 | 101 | 25,000 |
| 1002 | 102 | 15,000 |
| 1003 | 101 | 30,000 |
| 1004 | 103 | 10,000 |

## Products

| product_id | product_name | category |
|---:|---|---|
| 501 | Laptop | Electronics |
| 502 | Mouse | Electronics |
| 503 | Chair | Furniture |

---

# 1. UNION

## Definition

`UNION` combines the results of two or more `SELECT` queries and **removes duplicate rows**.

### Syntax

```sql
SELECT column1, column2
FROM table1

UNION

SELECT column1, column2
FROM table2;
```

---

## Example

Suppose a company has customers from two regional tables:

### North_Customers

| customer_name |
|---|
| Amit |
| Priya |
| Rahul |

### South_Customers

| customer_name |
|---|
| Priya |
| Neha |
| Rohit |

Query:

```sql
SELECT customer_name
FROM north_customers

UNION

SELECT customer_name
FROM south_customers;
```

### Result

| customer_name |
|---|
| Amit |
| Priya |
| Rahul |
| Neha |
| Rohit |

`Priya` appears only once because `UNION` removes duplicates.

---

### Business Application

Use `UNION` when combining similar data from:

- Different regions
- Different departments
- Archived and current datasets
- Multiple business branches

### Best Practice

The `SELECT` statements should generally have:

1. The same number of columns.
2. Compatible data types.
3. Columns in the same logical order.

### Remember

> **UNION = Combine results and remove duplicates.**

---

# 2. UNION ALL

## Definition

`UNION ALL` combines results from multiple queries but **keeps duplicate rows**.

### Syntax

```sql
SELECT column1
FROM table1

UNION ALL

SELECT column1
FROM table2;
```

---

## Example

```sql
SELECT customer_name
FROM north_customers

UNION ALL

SELECT customer_name
FROM south_customers;
```

### Result

| customer_name |
|---|
| Amit |
| Priya |
| Rahul |
| Priya |
| Neha |
| Rohit |

`Priya` appears twice.

---

## UNION vs UNION ALL

| Feature | UNION | UNION ALL |
|---|---|---|
| Combines results | Yes | Yes |
| Removes duplicates | Yes | No |
| Usually faster | No | Yes |
| Keeps all rows | No | Yes |

### Business Application

Use `UNION ALL` when every record is important.

For example, when combining:

- Monthly sales transactions
- Daily transaction files
- Data from multiple stores

### Best Practice

Use `UNION ALL` unless you specifically need to remove duplicates. Removing duplicates requires additional processing and may hide valid repeated transactions.

### Remember

> **UNION ALL = Combine everything, including duplicates.**

---

# 3. Subqueries

## Definition

A **subquery** is a query written inside another SQL query.

The inner query produces a result that is used by the outer query.

### Basic Structure

```sql
SELECT columns
FROM table
WHERE column operator (
    SELECT column
    FROM another_table
);
```

---

## Example: Products Above Average Price

### Business Question

> Find products that cost more than the average product price.

```sql
SELECT product_name, price
FROM products
WHERE price > (
    SELECT AVG(price)
    FROM products
);
```

### How It Works

**Step 1: Inner query**

```sql
SELECT AVG(price)
FROM products;
```

Calculates the average price.

**Step 2: Outer query**

Compares each product's price with the average.

### Business Application

Subqueries can help answer questions such as:

- Employees earning above average salary
- Products priced above average
- Customers with high spending
- Orders larger than average order value

### Remember

> **Subquery = A query inside another query.**

---

# 4. Types of Subqueries

Subqueries can be used in different places.

## A. Subquery in WHERE

Example:

```sql
SELECT customer_name
FROM customers
WHERE customer_id IN (
    SELECT customer_id
    FROM orders
);
```

This finds customers who have placed at least one order.

---

## B. Subquery in SELECT

You can use a subquery to create a calculated value.

```sql
SELECT
    product_name,
    price,
    (
        SELECT AVG(price)
        FROM products
    ) AS average_price
FROM products;
```

The average price will appear alongside each product.

---

## C. Subquery in FROM

A subquery in the `FROM` clause is often called a **derived table**.

```sql
SELECT AVG(total_sales) AS average_customer_sales
FROM (
    SELECT
        customer_id,
        SUM(amount) AS total_sales
    FROM orders
    GROUP BY customer_id
) AS customer_sales;
```

### How It Works

First:

- Calculate total sales for each customer.

Then:

- Calculate the average of those customer totals.

---

# 5. Correlated Subquery Concept

## Definition

A **correlated subquery** depends on the current row of the outer query.

Unlike a regular subquery, it uses values from the outer query.

### Example

Suppose we want to find orders that are greater than the **average order amount for the same customer**.

```sql
SELECT
    o1.order_id,
    o1.customer_id,
    o1.amount
FROM orders AS o1
WHERE o1.amount > (
    SELECT AVG(o2.amount)
    FROM orders AS o2
    WHERE o2.customer_id = o1.customer_id
);
```

### How It Works

For each row in `o1`:

1. The subquery finds orders for the same customer.
2. It calculates that customer's average order amount.
3. The outer query compares the current order with the average.

### Business Application

Correlated subqueries are useful for:

- Comparing an employee with their department average
- Comparing a product with its category average
- Finding customer transactions above their personal average

### Best Practice

Correlated subqueries can be slower on large datasets. For complex or large-scale analysis, consider using:

- CTEs
- JOINs
- Window functions

### Remember

> **Correlated subquery = The inner query depends on the outer query's current row.**

---

# 6. CTE (Common Table Expression)

## Definition

A **CTE** is a temporary named result set that exists only for the query being executed.

CTEs make complex SQL queries easier to read and organize.

### Syntax

```sql
WITH cte_name AS (
    SELECT columns
    FROM table
)
SELECT *
FROM cte_name;
```

---

## Example: Customer Sales

### Business Question

> Calculate total sales for each customer.

```sql
WITH customer_sales AS (
    SELECT
        customer_id,
        SUM(amount) AS total_sales
    FROM orders
    GROUP BY customer_id
)
SELECT *
FROM customer_sales;
```

The CTE creates a temporary result called `customer_sales`.

---

## CTE vs Subquery

| Feature | Subquery | CTE |
|---|---|---|
| Written inside another query | Yes | No |
| Has a temporary name | Usually no | Yes |
| Readability | Can become complex | Usually easier to read |
| Reusable within the same query | Limited | Yes |

### Business Application

Use CTEs when:

- Breaking a complex analysis into steps
- Improving query readability
- Creating intermediate calculations
- Performing multi-step business analysis

### Remember

> **CTE = A temporary named result used inside one SQL statement.**

---

# 7. Multiple CTEs

You can create multiple CTEs in one query.

Each CTE can build upon the previous result.

## Example: Customer Sales Analysis

### Business Question

> Identify customers whose total sales are above the average customer sales.

```sql
WITH customer_sales AS (
    SELECT
        customer_id,
        SUM(amount) AS total_sales
    FROM orders
    GROUP BY customer_id
),

average_sales AS (
    SELECT
        AVG(total_sales) AS avg_customer_sales
    FROM customer_sales
)

SELECT
    c.customer_name,
    cs.total_sales,
    a.avg_customer_sales
FROM customer_sales AS cs
INNER JOIN customers AS c
    ON cs.customer_id = c.customer_id
CROSS JOIN average_sales AS a
WHERE cs.total_sales > a.avg_customer_sales;
```

### Step-by-Step Explanation

**CTE 1: `customer_sales`**

Calculates total sales for each customer.

**CTE 2: `average_sales`**

Calculates the average sales using the first CTE.

**Final Query**

Displays customers whose sales are above the average.

---

# 8. Business Analysis Problems

Let's combine everything we have learned.

---

## Business Problem 1: Find High-Spending Customers

### Question

> Which customers have spent more than the average customer?

```sql
WITH customer_sales AS (
    SELECT
        customer_id,
        SUM(amount) AS total_sales
    FROM orders
    GROUP BY customer_id
)

SELECT
    c.customer_name,
    cs.total_sales
FROM customer_sales AS cs
JOIN customers AS c
    ON cs.customer_id = c.customer_id
WHERE cs.total_sales > (
    SELECT AVG(total_sales)
    FROM customer_sales
);
```

### Business Insight

This identifies high-value customers who may be suitable for:

- Loyalty programs
- Premium offers
- Personalized marketing

---

## Business Problem 2: Find Customers Without Orders

### Question

> Which customers have never placed an order?

```sql
SELECT
    customer_name
FROM customers
WHERE customer_id NOT IN (
    SELECT customer_id
    FROM orders
);
```

### Better Practice with NULL Values

In real-world SQL, `NOT IN` can behave unexpectedly if the subquery contains `NULL`. A safer approach is often `NOT EXISTS`:

```sql
SELECT
    c.customer_name
FROM customers AS c
WHERE NOT EXISTS (
    SELECT 1
    FROM orders AS o
    WHERE o.customer_id = c.customer_id
);
```

---

## Business Problem 3: Combine Regional Sales

### Question

> Combine sales data from North and South regions.

```sql
SELECT order_id, customer_id, amount
FROM north_sales

UNION ALL

SELECT order_id, customer_id, amount
FROM south_sales;
```

### Why `UNION ALL`?

Each sales transaction is important. We do not want to accidentally remove valid duplicate transactions.

---

## Business Problem 4: Products Above Average Price

```sql
SELECT
    product_name,
    price
FROM products
WHERE price > (
    SELECT AVG(price)
    FROM products
);
```

### Business Application

This can support:

- Premium product analysis
- Pricing strategy
- Product segmentation

---

# Subquery vs CTE vs UNION — When to Use What?

| Situation | Recommended Tool |
|---|---|
| Compare with a single calculated value | Subquery |
| Break a complex query into steps | CTE |
| Combine rows from similar datasets | UNION / UNION ALL |
| Inner query depends on outer row | Correlated Subquery |
| Multi-step business analysis | Multiple CTEs |

---

# Best Practices

## 1. Prefer Readability

For complex queries, use meaningful CTE names:

```sql
WITH monthly_sales AS (...)
```

instead of:

```sql
WITH data1 AS (...)
```

---

## 2. Use UNION ALL Carefully

Use `UNION ALL` when duplicates are valid business records.

Use `UNION` only when you specifically need duplicate removal.

---

## 3. Check Subquery Results Separately

Before using a subquery inside a large query, run it separately to verify its output.

For example:

```sql
SELECT AVG(price)
FROM products;
```

Then use it in the main query.

---

## 4. Avoid Unnecessary Complexity

If a simple `JOIN` solves the problem clearly, do not use multiple nested subqueries.

---

# Quick Revision

| Topic | Meaning | Key Point |
|---|---|---|
| `UNION` | Combines query results | Removes duplicates |
| `UNION ALL` | Combines query results | Keeps duplicates |
| Subquery | Query inside another query | Inner result helps outer query |
| Correlated Subquery | Depends on outer query | Runs in relation to each outer row |
| CTE | Temporary named result | Improves readability |
| Multiple CTEs | Multiple analysis steps | CTEs can build on each other |

---

# Easy Way to Remember

> **UNION → Combine rows**  
> **Subquery → Query inside a query**  
> **Correlated Subquery → Inner query depends on outer row**  
> **CTE → Name a temporary result and simplify the query**

---

# Practice Tasks

Use these tables:

### `Customers`

| customer_id | customer_name | city |
|---:|---|---|
| 101 | Amit | Indore |
| 102 | Priya | Mumbai |
| 103 | Rahul | Delhi |
| 104 | Neha | Pune |

### `Orders`

| order_id | customer_id | amount |
|---:|---:|---:|
| 1001 | 101 | 25,000 |
| 1002 | 102 | 15,000 |
| 1003 | 101 | 30,000 |
| 1004 | 103 | 10,000 |

## Basic Practice

1. Combine two customer lists using `UNION`.
2. Combine two customer lists using `UNION ALL`.
3. Find products priced above the average price using a subquery.
4. Find customers who have placed an order using a subquery.
5. Create a CTE to calculate total sales for each customer.
6. Use two CTEs to find customers whose sales are above average.

---

## Business Practice Challenge

### Problem

The sales manager wants to identify **high-value customers**.

Create a query that:

1. Calculates total sales for each customer.
2. Calculates the average customer sales.
3. Displays customers whose total sales are above the average.
4. Shows the customer name and total sales.
5. Sorts the results from highest to lowest sales.

**Hint:** Use:

- A CTE for customer sales
- A second CTE for average sales
- A JOIN with the `Customers` table
- `ORDER BY`

---

# Final Key Takeaway

Day 17 introduces important tools for solving complex SQL business problems.

The key idea is:

> **UNION combines results → Subqueries create nested analysis → Correlated subqueries compare related rows → CTEs organize complex logic into clear steps.**

As a Data Analyst, these concepts will help you move from writing simple SQL queries to solving **real-world, multi-step business analysis problems**.

Your SQL learning journey is now building toward more advanced topics such as **Window Functions, Advanced SQL Analysis, and Performance Optimization**.
