# Day 16 — SQL JOINs

## Introduction to JOINs

In real-world databases, business data is usually stored in **multiple related tables**. For example, customer information, orders, and products are often stored separately.

A **JOIN** is used to combine data from two or more tables based on a related column.

For a Data Analyst, JOINs are essential because business questions often require data from multiple tables.

### Example Database Structure

```text
CUSTOMERS
│ customer_id (Primary Key)
│
↓
ORDERS
│ order_id (Primary Key)
│ customer_id (Foreign Key)
│
↓
ORDER_ITEMS
│ order_item_id (Primary Key)
│ order_id (Foreign Key)
│ product_id (Foreign Key)
│
↓
PRODUCTS
   product_id (Primary Key)
```

This structure represents a typical e-commerce database.

---

# 1. Understanding the Tables

Before learning JOINs, let's understand our sample data.

## CUSTOMERS

| customer_id | customer_name | city |
|---:|---|---|
| 101 | Amit | Indore |
| 102 | Priya | Mumbai |
| 103 | Rahul | Delhi |
| 104 | Neha | Pune |

**Primary Key:** `customer_id`

---

## ORDERS

| order_id | customer_id | order_date |
|---:|---:|---|
| 1001 | 101 | 2026-01-10 |
| 1002 | 102 | 2026-01-12 |
| 1003 | 101 | 2026-01-15 |
| 1004 | 105 | 2026-01-20 |

**Primary Key:** `order_id`  
**Foreign Key:** `customer_id`

Notice that customer `105` does not exist in our sample `CUSTOMERS` table. This will help us understand different JOIN types.

---

## ORDER_ITEMS

| order_item_id | order_id | product_id | quantity |
|---:|---:|---:|---:|
| 1 | 1001 | 501 | 2 |
| 2 | 1001 | 502 | 1 |
| 3 | 1002 | 503 | 3 |
| 4 | 1003 | 501 | 1 |

**Foreign Keys:**

- `order_id`
- `product_id`

---

## PRODUCTS

| product_id | product_name | price |
|---:|---|---:|
| 501 | Laptop | 50,000 |
| 502 | Mouse | 1,000 |
| 503 | Keyboard | 2,000 |
| 504 | Monitor | 15,000 |

**Primary Key:** `product_id`

---

# Why Do We Need JOINs?

Suppose a manager asks:

> **Which customer bought which product?**

The information is spread across multiple tables:

- Customer name → `CUSTOMERS`
- Order information → `ORDERS`
- Items purchased → `ORDER_ITEMS`
- Product name and price → `PRODUCTS`

We need JOINs to combine this information.

---

# 2. INNER JOIN

## Definition

An **INNER JOIN** returns only the rows that have matching values in **both tables**.

### Syntax

```sql
SELECT columns
FROM table1
INNER JOIN table2
    ON table1.common_column = table2.common_column;
```

### Example

Get customers and their orders:

```sql
SELECT
    c.customer_name,
    o.order_id,
    o.order_date
FROM customers AS c
INNER JOIN orders AS o
    ON c.customer_id = o.customer_id;
```

### Result

| customer_name | order_id | order_date |
|---|---:|---|
| Amit | 1001 | 2026-01-10 |
| Priya | 1002 | 2026-01-12 |
| Amit | 1003 | 2026-01-15 |

Customer `104` is not included because they have no matching order.

Order `1004` is not included because customer `105` does not exist in the `CUSTOMERS` table.

### Business Application

Use an INNER JOIN when you only want **valid matching records**.

For example:

- Customers who have placed orders
- Employees assigned to departments
- Products that have been sold

### Best Practice

Always understand the relationship and verify the JOIN condition:

```sql
ON c.customer_id = o.customer_id
```

A wrong JOIN condition can create incorrect or duplicate results.

### Remember

> **INNER JOIN = Only matching records from both tables.**

---

# 3. LEFT JOIN

## Definition

A **LEFT JOIN** returns:

- All records from the **left table**
- Matching records from the **right table**
- `NULL` values when no match exists

### Syntax

```sql
SELECT columns
FROM table1
LEFT JOIN table2
    ON table1.common_column = table2.common_column;
```

### Example

Show all customers and their orders:

```sql
SELECT
    c.customer_name,
    o.order_id
FROM customers AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id;
```

### Result

| customer_name | order_id |
|---|---:|
| Amit | 1001 |
| Amit | 1003 |
| Priya | 1002 |
| Rahul | NULL |
| Neha | NULL |

### Business Application

A LEFT JOIN is useful for finding missing relationships.

For example:

> Find customers who have never placed an order.

```sql
SELECT
    c.customer_name
FROM customers AS c
LEFT JOIN orders AS o
    ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;
```

### Best Practice

Use a LEFT JOIN when the table on the left contains the **complete list you want to preserve**.

### Remember

> **LEFT JOIN = Keep everything from the left table.**

---

# 4. RIGHT JOIN

## Definition

A **RIGHT JOIN** returns:

- All records from the **right table**
- Matching records from the **left table**
- `NULL` values when no match exists

### Syntax

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
    ON table1.common_column = table2.common_column;
```

### Example

Show all orders, including orders without a valid customer:

```sql
SELECT
    c.customer_name,
    o.order_id
FROM customers AS c
RIGHT JOIN orders AS o
    ON c.customer_id = o.customer_id;
```

### Result

| customer_name | order_id |
|---|---:|
| Amit | 1001 |
| Priya | 1002 |
| Amit | 1003 |
| NULL | 1004 |

### Business Application

RIGHT JOIN can help identify:

- Orders with missing customer information
- Records that exist in the second table but have no match in the first table

### Best Practice

Many analysts prefer using LEFT JOIN instead of RIGHT JOIN for better readability.

You can often rewrite a RIGHT JOIN by switching the table order.

### Remember

> **RIGHT JOIN = Keep everything from the right table.**

---

# 5. FULL JOIN Concept

## Definition

A **FULL OUTER JOIN** returns:

- All matching records
- All records from the left table
- All records from the right table

When there is no match, the missing side contains `NULL`.

### Conceptual Syntax

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
    ON table1.common_column = table2.common_column;
```

### Conceptual Result

Using Customers and Orders:

| customer_name | order_id |
|---|---:|
| Amit | 1001 |
| Amit | 1003 |
| Priya | 1002 |
| Rahul | NULL |
| Neha | NULL |
| NULL | 1004 |

### Business Application

A FULL JOIN is useful for **data reconciliation**.

For example:

- Compare customer records from two systems
- Find missing records in either dataset
- Identify unmatched transactions

### Important Note

Not every database supports `FULL OUTER JOIN` directly. For example, MySQL traditionally requires alternative approaches, such as combining LEFT and RIGHT JOIN results.

### Remember

> **FULL JOIN = Keep all records from both tables.**

---

# 6. SELF JOIN

## Definition

A **SELF JOIN** joins a table with itself.

It is useful when records in the same table are related to other records in that table.

### Example: Employees and Managers

| employee_id | employee_name | manager_id |
|---:|---|---:|
| 1 | Amit | 3 |
| 2 | Priya | 3 |
| 3 | Rahul | NULL |

We can join the `employees` table to itself.

### Query

```sql
SELECT
    e.employee_name AS employee,
    m.employee_name AS manager
FROM employees AS e
LEFT JOIN employees AS m
    ON e.manager_id = m.employee_id;
```

### Result

| employee | manager |
|---|---|
| Amit | Rahul |
| Priya | Rahul |
| Rahul | NULL |

### Business Application

SELF JOINs are useful for:

- Employee-manager hierarchies
- Referral relationships
- Parent-child categories
- Comparing records within the same table

### Remember

> **SELF JOIN = A table joined to itself.**

---

# 7. One-to-One Relationship

## Definition

In a **one-to-one relationship**, one record in Table A is connected to exactly one record in Table B.

### Example

```text
EMPLOYEES
    │
    │ One Employee
    ↓
EMPLOYEE_DETAILS
    │
    │ One Detail Record
```

For example:

- One employee → One employee profile
- One customer → One loyalty account

### Database Design

One-to-one relationships are less common because related information can sometimes be stored in the same table.

### Remember

> **One record ↔ One record**

---

# 8. One-to-Many Relationship

## Definition

In a **one-to-many relationship**, one record in the first table can be related to multiple records in another table.

### Example

```text
One CUSTOMER
     │
     ├── Order 1001
     ├── Order 1003
     └── Order 1005
```

A customer can place many orders.

However, each order belongs to one customer.

### In Our Database

```text
CUSTOMERS
customer_id
     │
     ↓
ORDERS
customer_id
```

### Business Application

One-to-many relationships are extremely common:

- One customer → Many orders
- One department → Many employees
- One category → Many products

### Remember

> **One parent record → Many related records.**

---

# 9. Many-to-Many Relationship

## Definition

In a **many-to-many relationship**, multiple records in one table can be related to multiple records in another table.

### Example: Orders and Products

- One order can contain many products.
- One product can appear in many orders.

To manage this relationship, we use an intermediate table.

```text
ORDERS
   │
   │
   ↓
ORDER_ITEMS
   ↑
   │
PRODUCTS
```

### Why ORDER_ITEMS Is Important

`ORDER_ITEMS` acts as a **junction table**.

It connects:

- `order_id`
- `product_id`

### Example

| order_id | product_id | quantity |
|---:|---:|---:|
| 1001 | 501 | 2 |
| 1001 | 502 | 1 |
| 1002 | 501 | 1 |

This means:

- Order 1001 contains Laptop and Mouse.
- Product 501 appears in multiple orders.

### Business Application

Many-to-many relationships are common in:

- Orders and products
- Students and courses
- Employees and projects

### Remember

> **Many-to-many relationships usually require a junction table.**

---

# Complete Database Relationship

Here is the complete structure again:

```text
CUSTOMERS
────────────────────
customer_id (PK)
customer_name
city
        │
        │ One customer
        │
        ▼
ORDERS
────────────────────
order_id (PK)
customer_id (FK)
order_date
        │
        │ One order
        │
        ▼
ORDER_ITEMS
────────────────────
order_item_id (PK)
order_id (FK)
product_id (FK)
quantity
        │
        ▼
PRODUCTS
────────────────────
product_id (PK)
product_name
price
```

---

# Complete Multi-Table JOIN Example

## Business Question

> Show each customer, their orders, the products they purchased, and the quantity purchased.

```sql
SELECT
    c.customer_name,
    o.order_id,
    p.product_name,
    oi.quantity,
    p.price,
    oi.quantity * p.price AS total_sales
FROM customers AS c
INNER JOIN orders AS o
    ON c.customer_id = o.customer_id
INNER JOIN order_items AS oi
    ON o.order_id = oi.order_id
INNER JOIN products AS p
    ON oi.product_id = p.product_id;
```

## How the JOIN Works

```text
CUSTOMERS
    ↓ customer_id
ORDERS
    ↓ order_id
ORDER_ITEMS
    ↓ product_id
PRODUCTS
```

The query combines information from all four tables.

### Business Application

This type of query can help answer:

- Which products did customers purchase?
- What is the total sales amount?
- Which customers generate the most revenue?
- Which products are most frequently sold?

---

# JOIN Types Quick Comparison

| JOIN Type | Returns |
|---|---|
| `INNER JOIN` | Only matching records |
| `LEFT JOIN` | All left records + matching right records |
| `RIGHT JOIN` | All right records + matching left records |
| `FULL OUTER JOIN` | All records from both tables |
| `SELF JOIN` | A table joined with itself |

---

# Best Practices for SQL JOINs

## 1. Always Understand the Relationship

Before joining tables, identify:

- Primary key
- Foreign key
- Relationship type

For example:

```text
customers.customer_id → orders.customer_id
```

---

## 2. Use Table Aliases

Instead of writing long table names repeatedly:

```sql
FROM customers AS c
INNER JOIN orders AS o
```

This makes the query shorter and easier to read.

---

## 3. Avoid Duplicate Columns

Do not automatically use:

```sql
SELECT *
```

Instead, select only the columns needed.

---

## 4. Check for Duplicate Rows

A one-to-many relationship naturally creates multiple rows after a JOIN.

For example:

- One customer with three orders will appear three times.

This is not necessarily an error. Understand the **level of detail (granularity)** before performing calculations.

---

## 5. Use the Correct JOIN Type

Ask:

> **Do I need only matching records, or do I need to keep unmatched records too?**

This helps determine whether to use:

- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL JOIN

---

# Quick Revision

| Topic | Meaning | Remember |
|---|---|---|
| JOIN | Combines tables | Connect related data |
| INNER JOIN | Matching records only | Intersection |
| LEFT JOIN | Keep all left records | Left table is preserved |
| RIGHT JOIN | Keep all right records | Right table is preserved |
| FULL JOIN | Keep all records | Everything from both sides |
| SELF JOIN | Join a table to itself | Same table, different aliases |
| One-to-One | One ↔ One | One matching record |
| One-to-Many | One → Many | Customer → Orders |
| Many-to-Many | Many ↔ Many | Orders ↔ Products via junction table |

---

# Practice Tasks

Use the following tables:

- `customers`
- `orders`
- `order_items`
- `products`

## Basic Practice

1. Use an `INNER JOIN` to display customers and their orders.
2. Use a `LEFT JOIN` to display all customers, including those without orders.
3. Find customers who have never placed an order.
4. Use a `RIGHT JOIN` to display all orders, including orders without matching customers.
5. Join `orders` with `order_items`.
6. Join `order_items` with `products`.

---

## Business Practice

### Task 1: Customer Purchase Report

Create a report showing:

- Customer name
- Order ID
- Product name
- Quantity
- Product price
- Total sales

Use all four tables.

---

### Task 2: Find Inactive Customers

Find customers who have never placed an order.

**Hint:** Use:

```sql
LEFT JOIN
```

and:

```sql
WHERE order_id IS NULL
```

---

### Task 3: Product Sales Analysis

Create a report showing:

- Product name
- Total quantity sold
- Total sales

This requires:

1. Joining `ORDER_ITEMS` and `PRODUCTS`
2. Using `SUM()`
3. Using `GROUP BY`

---

# Final Key Takeaway

JOINs are essential because real-world business data is rarely stored in a single table.

The key concept is:

> **Understand the tables → Identify Primary and Foreign Keys → Understand the relationship → Choose the correct JOIN → Check the resulting rows.**

For a Data Analyst, one of the most important skills is understanding how data flows through related tables:

**CUSTOMERS → ORDERS → ORDER_ITEMS → PRODUCTS**

Once you master JOINs, you can combine data from different parts of a business and answer much more complex analytical questions.
