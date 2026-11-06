# Day 13 — Database Fundamentals + SELECT

## Introduction

Databases are the foundation of modern business data. Companies store information such as **customers, products, sales, employees, and transactions** in databases.

# Part 1: Database Fundamentals

## 1. Database

### Definition

A **database** is an organized collection of data stored electronically so that it can be easily accessed, managed, updated, and analyzed.

### Example

A retail company may have one database containing:

```text
Retail Database
│
├── Customers
├── Products
├── Orders
├── Employees
└── Payments
```

Each category of information is usually stored in a separate table.

### Business Example

An e-commerce company stores:

- Customer details
- Product information
- Orders
- Payment transactions

Instead of maintaining hundreds of separate Excel files, the company can store and manage this information in a database.

### Business Application

Data analysts use databases to:

- Analyze sales performance.
- Find top customers.
- Track inventory.
- Analyze customer behavior.
- Create business reports and dashboards.

### Best Practice

- Organize related data logically.
- Avoid unnecessary duplicate data.
- Use meaningful table and column names.
- Maintain data security and access controls.

### Remember

> **Database = A complete organized collection of related data.**

---

# 2. Tables

### Definition

A **table** is a structured collection of related data organized into **rows and columns**.

You can think of a database table as being similar to an Excel worksheet.

### Example: Customers Table

| Customer_ID | Customer_Name | City | Age |
|---|---|---|---:|
| 101 | Amit | Indore | 25 |
| 102 | Priya | Mumbai | 30 |
| 103 | Rahul | Delhi | 28 |

### Business Example

A retail database may contain:

- `customers`
- `orders`
- `products`
- `employees`

Each table stores data about one specific business entity.

### Business Application

Tables allow analysts to organize and retrieve specific types of business information.

For example:

- Customer analysis → `customers` table
- Sales analysis → `orders` table
- Product analysis → `products` table

### Best Practice

Keep each table focused on a specific subject. Avoid storing unrelated information in the same table.

### Remember

> **Table = A collection of related data arranged in rows and columns.**

---

# 3. Rows

### Definition

A **row** represents one individual record in a table.

A row is also called a **record**.

### Example

| Customer_ID | Customer_Name | City |
|---|---|---|
| **101** | **Amit** | **Indore** |
| 102 | Priya | Mumbai |

The first line of customer information represents **one row**.

### Business Example

In an `orders` table, each row may represent one customer order.

| Order_ID | Customer_ID | Order_Amount |
|---|---:|---:|
| 1001 | 101 | 2,500 |
| 1002 | 102 | 1,800 |

### Business Application

Analysts often count, filter, and aggregate rows to answer questions such as:

- How many orders were placed?
- How many customers are active?
- Which transactions occurred last month?

### Best Practice

Ensure that each row represents one consistent unit of information.

For example, if one row represents an order, do not mix order-level and customer-level information unnecessarily.

### Remember

> **Row = One complete record or observation.**

---

# 4. Columns

### Definition

A **column** represents a specific type of information stored for every row.

### Example

| Customer_ID | Customer_Name | City | Age |
|---|---|---|---:|
| 101 | Amit | Indore | 25 |

The columns are:

- `Customer_ID`
- `Customer_Name`
- `City`
- `Age`

### Data Types

Columns usually have a defined data type.

| Data Type | Example |
|---|---|
| Integer | 101, 25 |
| Text / VARCHAR | Amit, Indore |
| Decimal | 1250.50 |
| Date | 2026-11-06 |
| Boolean | TRUE / FALSE |

### Business Application

Columns help analysts select exactly the information needed for analysis.

For example:

```sql
SELECT Customer_Name, City
FROM Customers;
```

### Best Practice

- Use clear column names.
- Use the correct data type.
- Avoid storing multiple pieces of information in one column.

### Remember

> **Column = One type of information about a record.**

---

# 5. Primary Keys

### Definition

A **primary key** is a column, or combination of columns, that **uniquely identifies each row** in a table.

### Example

| Customer_ID | Customer_Name | City |
|---|---|---|
| **101** | Amit | Indore |
| **102** | Priya | Mumbai |
| **103** | Rahul | Delhi |

`Customer_ID` is the primary key.

### Important Characteristics

A primary key must:

- Be unique.
- Not contain duplicate values.
- Not contain `NULL` values.

### Business Application

Primary keys ensure that analysts and systems can identify the correct record.

For example, two customers may have the same name, but they should have different customer IDs.

### Best Practice

Use stable identifiers such as:

- Customer_ID
- Order_ID
- Product_ID

Avoid using names or email addresses as primary keys when they may change.

### Remember

> **Primary Key = Unique identifier for each row.**

---

# 6. Foreign Keys

### Definition

A **foreign key** is a column that creates a connection between two tables.

Usually, it refers to the primary key of another table.

### Example

#### Customers Table

| Customer_ID | Customer_Name |
|---|---|
| **101** | Amit |
| **102** | Priya |

`Customer_ID` is the primary key.

#### Orders Table

| Order_ID | Customer_ID | Amount |
|---|---:|---:|
| 1001 | **101** | 2,500 |
| 1002 | **102** | 1,800 |
| 1003 | **101** | 3,200 |

In the `Orders` table, `Customer_ID` is a **foreign key**.

### Business Application

Foreign keys allow analysts to connect data.

For example:

> Which customers placed which orders?

The relationship can be established using `Customer_ID`.

### Best Practice

Make sure foreign key values match valid primary key values in the related table.

### Remember

> **Foreign Key = A column used to connect one table with another table.**

---

# 7. Relationships

### Definition

A **relationship** describes how tables are connected to each other.

## A. One-to-One

One record in Table A is connected to one record in Table B.

**Example:** One employee → One employee ID card.

## B. One-to-Many

One record in one table can be connected to many records in another table.

**Example:**

```text
One Customer → Many Orders
```

This is one of the most common database relationships.

## C. Many-to-Many

Multiple records in one table can relate to multiple records in another table.

**Example:**

```text
Students ←→ Courses
```

This is usually managed through a third table called a **junction table**.

### Business Application

Relationships allow businesses to connect information without repeating the same data multiple times.

### Best Practice

Understand the relationship between tables before joining or analyzing data. Incorrect relationships can lead to duplicate rows and incorrect calculations.

### Remember

> **Relationships connect tables and explain how their data is related.**

---

# Part 2: SQL SELECT Fundamentals

## 8. SELECT

### Definition

The `SELECT` statement is used to **retrieve data from a database table**.

It is one of the most important SQL commands for a Data Analyst.

### Syntax

```sql
SELECT column_name
FROM table_name;
```

### Example

Retrieve customer names:

```sql
SELECT Customer_Name
FROM Customers;
```

### Select Multiple Columns

```sql
SELECT Customer_ID, Customer_Name, City
FROM Customers;
```

### Select All Columns

```sql
SELECT *
FROM Customers;
```

### Business Example

A sales manager wants a list of customer names and cities.

```sql
SELECT Customer_Name, City
FROM Customers;
```

### Business Application

Use `SELECT` to:

- Retrieve sales data.
- View customer information.
- Analyze product performance.
- Prepare data for reports and dashboards.

### Best Practice

Avoid `SELECT *` in large production tables. Select only the columns you need.

### Remember

> **SELECT = What data do I want to see?**

---

# 9. DISTINCT

### Definition

The `DISTINCT` keyword removes duplicate values from the result.

### Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

### Example

Suppose the customer table contains:

| City |
|---|
| Indore |
| Mumbai |
| Indore |
| Delhi |
| Mumbai |

Query:

```sql
SELECT DISTINCT City
FROM Customers;
```

### Result

| City |
|---|
| Indore |
| Mumbai |
| Delhi |

### Business Example

A company wants to know all the cities where it has customers.

### Business Application

Use `DISTINCT` to find:

- Unique cities
- Unique product categories
- Unique departments
- Unique customer segments

### Best Practice

Remember that `DISTINCT` applies to the **combination of all selected columns**.

```sql
SELECT DISTINCT City, Age
FROM Customers;
```

This finds unique combinations of City and Age.

### Remember

> **DISTINCT = Remove duplicate results.**

---

# 10. Aliases

### Definition

An **alias** is a temporary name given to a column or table.

Aliases make query results easier to understand.

### Syntax

```sql
SELECT column_name AS alias_name
FROM table_name;
```

### Example

```sql
SELECT Customer_Name AS Customer
FROM Customers;
```

The output column will be displayed as `Customer`.

### Alias for Calculations

```sql
SELECT Product_Name,
       Price * Quantity AS Total_Sales
FROM Orders;
```

Here, `Total_Sales` is an alias for the calculated result.

### Table Alias

```sql
SELECT c.Customer_Name, c.City
FROM Customers AS c;
```

Here, `c` is an alias for the `Customers` table.

### Business Application

Aliases make reports and dashboards more readable.

For example:

```sql
SELECT Revenue AS Monthly_Revenue
FROM Sales;
```

### Best Practice

Use clear and meaningful aliases, especially for calculated columns.

### Remember

> **Alias = A temporary name used to make SQL easier to read.**

---

# 11. WHERE

### Definition

The `WHERE` clause filters records based on a specified condition.

### Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition;
```

### Example

Find customers from Indore:

```sql
SELECT Customer_Name, City
FROM Customers
WHERE City = 'Indore';
```

### Numerical Example

Find orders greater than ₹2,000:

```sql
SELECT Order_ID, Amount
FROM Orders
WHERE Amount > 2000;
```

### Common Operators

| Operator | Meaning |
|---|---|
| `=` | Equal to |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal to |
| `<=` | Less than or equal to |
| `<>` | Not equal to |

### Multiple Conditions

Using `AND`:

```sql
SELECT *
FROM Customers
WHERE City = 'Indore'
  AND Age >= 25;
```

Using `OR`:

```sql
SELECT *
FROM Customers
WHERE City = 'Indore'
   OR City = 'Mumbai';
```

### Business Example

Find all high-value orders above ₹10,000:

```sql
SELECT Order_ID, Customer_ID, Amount
FROM Orders
WHERE Amount > 10000;
```

### Business Application

`WHERE` is used to:

- Filter a specific time period.
- Find customers from a particular location.
- Analyze high-value transactions.
- Identify inactive customers.

### Best Practice

Always check your filter conditions carefully. A small mistake in `WHERE` can produce incorrect analysis.

### Remember

> **WHERE = Which records do I want?**

---

# 12. ORDER BY

### Definition

The `ORDER BY` clause sorts query results.

### Syntax

```sql
SELECT column_name
FROM table_name
ORDER BY column_name ASC;
```

### Ascending Order

```sql
SELECT Customer_Name, Age
FROM Customers
ORDER BY Age ASC;
```

`ASC` means **ascending order**.

It is often the default.

### Descending Order

```sql
SELECT Customer_Name, Age
FROM Customers
ORDER BY Age DESC;
```

`DESC` means **descending order**.

### Multiple Column Sorting

```sql
SELECT Customer_Name, City, Age
FROM Customers
ORDER BY City ASC, Age DESC;
```

This query:

1. Sorts customers by City.
2. Within each city, sorts customers by Age from highest to lowest.

### Business Example

Find products with the highest sales first:

```sql
SELECT Product_Name, Sales
FROM Products
ORDER BY Sales DESC;
```

### Business Application

Use `ORDER BY` to:

- Find top-performing products.
- Identify highest-value customers.
- Sort employees by salary.
- View recent transactions.

### Best Practice

Always specify `ASC` or `DESC` when the sorting direction is important. This makes your SQL easier to understand.

### Remember

> **ORDER BY = How do I want to sort the results?**

---

# 13. LIMIT

### Definition

The `LIMIT` clause restricts the number of rows returned by a query.

### Syntax

```sql
SELECT column_name
FROM table_name
LIMIT number;
```

### Example

Return only five records:

```sql
SELECT *
FROM Customers
LIMIT 5;
```

### Business Example: Top 5 Products

```sql
SELECT Product_Name, Sales
FROM Products
ORDER BY Sales DESC
LIMIT 5;
```

This query:

1. Retrieves product names and sales.
2. Sorts sales from highest to lowest.
3. Returns the top 5 products.

### Business Application

Use `LIMIT` when:

- Previewing a large dataset.
- Finding top-performing records.
- Testing a query before retrieving millions of rows.

### Best Practice

When using `LIMIT` to find the "top" records, always combine it with `ORDER BY`.

For example:

```sql
SELECT Product_Name, Sales
FROM Products
ORDER BY Sales DESC
LIMIT 10;
```

Without `ORDER BY`, the returned rows may not represent the actual top 10.

### Remember

> **LIMIT = How many records do I want to return?**

### Database Note

`LIMIT` is commonly used in **MySQL** and **PostgreSQL**. Other databases may use different syntax:

```sql
-- SQL Server
SELECT TOP 5 *
FROM Customers;
```

---

# Complete Business Example

## Business Question

> Find the top 5 customers from Indore based on their total purchase amount.

A simple query might look like:

```sql
SELECT Customer_ID AS Customer_ID,
       Customer_Name AS Customer,
       Total_Purchase AS Total_Spent
FROM Customers
WHERE City = 'Indore'
ORDER BY Total_Purchase DESC
LIMIT 5;
```

### Understanding the Query

| SQL Clause | Purpose |
|---|---|
| `SELECT` | Choose the columns |
| `AS` | Give columns meaningful names |
| `FROM` | Identify the table |
| `WHERE` | Filter customers from Indore |
| `ORDER BY DESC` | Sort from highest to lowest spending |
| `LIMIT 5` | Return only five customers |

---

# Quick Revision

| Topic | Quick Meaning | Key Point |
|---|---|---|
| Database | Collection of organized data | Contains tables |
| Table | Data organized in rows and columns | Similar to an Excel sheet |
| Row | One record | One customer or order |
| Column | One type of information | Name, City, Amount |
| Primary Key | Unique row identifier | No duplicates or NULL values |
| Foreign Key | Connects tables | References another table |
| Relationship | Connection between tables | One-to-many is common |
| SELECT | Retrieves data | Choose columns |
| DISTINCT | Removes duplicates | Returns unique values |
| Alias | Temporary name | Improves readability |
| WHERE | Filters rows | Applies conditions |
| ORDER BY | Sorts results | ASC or DESC |
| LIMIT | Restricts results | Returns a specific number of rows |

---

# SQL Query Structure to Remember

A common basic SQL query follows this structure:

```sql
SELECT column_name
FROM table_name
WHERE condition
ORDER BY column_name DESC
LIMIT number;
```

### Easy Way to Remember

> **SELECT → What**  
> **FROM → Where from**  
> **WHERE → Which records**  
> **ORDER BY → How to sort**  
> **LIMIT → How many**

---

# Practice Tasks

Assume you have the following table:

### `Employees`

| Employee_ID | Employee_Name | Department | City | Salary |
|---:|---|---|---|---:|
| 101 | Amit | Sales | Indore | 45,000 |
| 102 | Priya | HR | Mumbai | 55,000 |
| 103 | Rahul | Sales | Indore | 50,000 |
| 104 | Neha | IT | Delhi | 70,000 |
| 105 | Rohit | IT | Indore | 65,000 |
| 106 | Anjali | HR | Mumbai | 52,000 |

## Basic Practice

1. Select all columns from the `Employees` table.
2. Display only `Employee_Name` and `Salary`.
3. Find all unique departments.
4. Display employee names using the alias `Name`.
5. Find employees who live in Indore.
6. Find employees with a salary greater than 50,000.
7. Sort employees by salary from highest to lowest.
8. Display only the top 3 highest-paid employees.

## Business-Based Practice

### Task 1: HR Analysis

Find all employees from the IT department.

### Task 2: Salary Analysis

Find the top 5 employees with the highest salary.

### Task 3: Location Analysis

Find all unique cities where the company has employees.

### Task 4: Management Report

Display employee name, department, and salary for employees earning more than 50,000, sorted by salary from highest to lowest.

---

# Final Key Takeaway

For a Data Analyst, understanding databases is the first step toward working with real business data.

The most important concept to remember is:

> **Data is stored in tables → Tables contain rows and columns → Keys connect tables → SQL helps retrieve and analyze the data.**

Once you are comfortable with **SELECT, WHERE, ORDER BY, DISTINCT, aliases, and LIMIT**, you have built a strong foundation for the next SQL topics such as **aggregate functions, GROUP BY, JOINs, and subqueries**.
