# Day 14 — SQL Aggregation

## Introduction

In the previous lesson, you learned how to retrieve and filter data using `SELECT`, `WHERE`, `ORDER BY`, and `LIMIT`.

Now, we will learn **aggregation**, which helps a Data Analyst summarize large amounts of data.

For example, instead of looking at thousands of individual sales records, you can answer questions such as:

- How many orders were placed?
- What is the total sales amount?
- What is the average order value?
- Which product has the highest sales?
- How much sales did each category generate?

The main SQL aggregation topics are:

- `COUNT`
- `SUM`
- `AVG`
- `MIN`
- `MAX`
- `GROUP BY`
- `HAVING`
- `CASE`

---

# Sample Data for Examples

Let's use an `Orders` table throughout this lesson.

| Order_ID | Customer | Category | City | Amount |
|---|---|---|---|---:|
| 101 | Amit | Electronics | Indore | 25,000 |
| 102 | Priya | Clothing | Mumbai | 5,000 |
| 103 | Rahul | Electronics | Indore | 18,000 |
| 104 | Neha | Clothing | Delhi | 7,000 |
| 105 | Amit | Electronics | Indore | 30,000 |
| 106 | Rohit | Furniture | Mumbai | 20,000 |

---

# 1. COUNT

## Definition

The `COUNT()` function is used to **count the number of rows or non-NULL values**.

## Syntax

```sql
COUNT(column_name)
```

### Count All Rows

```sql
COUNT(*)
```

## Example

Count the total number of orders:

```sql
SELECT COUNT(*) AS Total_Orders
FROM Orders;
```

### Result

| Total_Orders |
|---:|
| 6 |

### Count Non-NULL Values

```sql
SELECT COUNT(Customer) AS Customer_Count
FROM Orders;
```

`COUNT(Customer)` counts only rows where the `Customer` value is not `NULL`.

### Business Application

A company can use `COUNT()` to find:

- Total orders
- Number of customers
- Number of employees
- Number of transactions

### Best Practice

Use:

```sql
COUNT(*)
```

when you want to count **all rows**.

Use:

```sql
COUNT(column_name)
```

when you want to count only **non-NULL values** in a specific column.

### Remember

> **COUNT = How many?**

---

# 2. SUM

## Definition

The `SUM()` function calculates the **total of numerical values**.

## Syntax

```sql
SUM(column_name)
```

## Example

Calculate total sales:

```sql
SELECT SUM(Amount) AS Total_Sales
FROM Orders;
```

### Business Example

A company wants to calculate its total revenue.

```sql
SELECT SUM(Amount) AS Total_Revenue
FROM Orders;
```

### Business Application

Use `SUM()` to calculate:

- Total sales
- Total revenue
- Total expenses
- Total quantity sold

### Best Practice

Use `SUM()` only with appropriate numerical columns. Always check for duplicate records before calculating important business totals.

### Remember

> **SUM = What is the total?**

---

# 3. AVG

## Definition

The `AVG()` function calculates the **average value** of a numerical column.

## Syntax

```sql
AVG(column_name)
```

## Example

Find the average order amount:

```sql
SELECT AVG(Amount) AS Average_Order_Value
FROM Orders;
```

### Business Example

A business wants to know the typical value of an order.

```sql
SELECT AVG(Amount) AS Average_Order_Value
FROM Orders;
```

### Business Application

`AVG()` can help analyze:

- Average customer spending
- Average employee salary
- Average order value
- Average delivery time

### Best Practice

Remember that `AVG()` ignores `NULL` values. Also check for extreme values because outliers can significantly affect the average.

### Remember

> **AVG = What is the average?**

---

# 4. MIN

## Definition

The `MIN()` function returns the **smallest value** in a column.

## Syntax

```sql
MIN(column_name)
```

## Example

Find the smallest order amount:

```sql
SELECT MIN(Amount) AS Lowest_Order
FROM Orders;
```

### Business Application

Use `MIN()` to find:

- Lowest sales amount
- Minimum salary
- Earliest date
- Lowest product price

### Example with Dates

```sql
SELECT MIN(Order_Date) AS First_Order_Date
FROM Orders;
```

This can return the earliest order date.

### Remember

> **MIN = Smallest value**

---

# 5. MAX

## Definition

The `MAX()` function returns the **largest value** in a column.

## Syntax

```sql
MAX(column_name)
```

## Example

Find the highest order amount:

```sql
SELECT MAX(Amount) AS Highest_Order
FROM Orders;
```

### Business Application

Use `MAX()` to find:

- Highest sales amount
- Maximum salary
- Latest transaction date
- Most expensive product

### Remember

> **MAX = Largest value**

---

# Summary of Aggregate Functions

| Function | Purpose | Example Question |
|---|---|---|
| `COUNT()` | Counts records | How many orders? |
| `SUM()` | Calculates total | What is total sales? |
| `AVG()` | Calculates average | What is average order value? |
| `MIN()` | Finds smallest value | What is the lowest sale? |
| `MAX()` | Finds largest value | What is the highest sale? |

---

# 6. GROUP BY

## Definition

The `GROUP BY` clause groups rows that have the same value so that aggregate functions can calculate results for each group.

### Without GROUP BY

This query calculates total sales for the entire company:

```sql
SELECT SUM(Amount) AS Total_Sales
FROM Orders;
```

### With GROUP BY

This query calculates total sales for each category:

```sql
SELECT Category,
       SUM(Amount) AS Total_Sales
FROM Orders
GROUP BY Category;
```

### Result

| Category | Total_Sales |
|---|---:|
| Electronics | 73,000 |
| Clothing | 12,000 |
| Furniture | 20,000 |

### Business Application

Use `GROUP BY` to analyze:

- Sales by category
- Customers by city
- Employees by department
- Revenue by month

### Best Practice

When using `GROUP BY`, every selected column that is **not inside an aggregate function** generally needs to be included in the `GROUP BY`.

Correct:

```sql
SELECT Category, SUM(Amount)
FROM Orders
GROUP BY Category;
```

### Remember

> **GROUP BY = Divide the data into groups before summarizing it.**

---

# 7. HAVING

## Definition

The `HAVING` clause filters **groups after aggregation**.

It is often used together with `GROUP BY`.

## Syntax

```sql
SELECT column_name,
       aggregate_function(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

## Example

Find categories with total sales greater than 20,000:

```sql
SELECT Category,
       SUM(Amount) AS Total_Sales
FROM Orders
GROUP BY Category
HAVING SUM(Amount) > 20000;
```

### Important: WHERE vs HAVING

| WHERE | HAVING |
|---|---|
| Filters individual rows | Filters grouped results |
| Used before aggregation | Used after aggregation |
| Example: `WHERE Amount > 5000` | Example: `HAVING SUM(Amount) > 50000` |

### Example

```sql
SELECT Category,
       SUM(Amount) AS Total_Sales
FROM Orders
WHERE Amount > 5000
GROUP BY Category
HAVING SUM(Amount) > 20000;
```

This query works in the following logical order:

1. `WHERE` filters individual orders.
2. `GROUP BY` creates categories.
3. `SUM()` calculates sales for each category.
4. `HAVING` filters the final groups.

### Business Application

Use `HAVING` to find:

- Categories with high sales
- Cities with more than 100 customers
- Departments with an average salary above a target

### Remember

> **WHERE filters rows. HAVING filters groups.**

---

# 8. CASE

## Definition

The `CASE` statement allows you to create **conditional logic in SQL**.

It works similarly to an `IF` statement in Excel.

## Syntax

```sql
CASE
    WHEN condition THEN result
    WHEN condition THEN result
    ELSE result
END
```

## Example: Categorize Orders

Suppose we want to classify orders based on their amount:

- Above 20,000 → High Value
- Between 10,000 and 20,000 → Medium Value
- Below 10,000 → Low Value

```sql
SELECT Order_ID,
       Amount,
       CASE
           WHEN Amount > 20000 THEN 'High Value'
           WHEN Amount >= 10000 THEN 'Medium Value'
           ELSE 'Low Value'
       END AS Order_Category
FROM Orders;
```

### Result

| Order_ID | Amount | Order_Category |
|---|---:|---|
| 101 | 25,000 | High Value |
| 102 | 5,000 | Low Value |
| 103 | 18,000 | Medium Value |

### Business Application

`CASE` is useful for:

- Customer segmentation
- Sales categorization
- Performance ratings
- Creating business rules
- Data cleaning and transformation

---

# CASE with Aggregation

You can combine `CASE` with aggregate functions.

### Example: Count High-Value Orders

```sql
SELECT
    COUNT(
        CASE
            WHEN Amount > 20000 THEN 1
        END
    ) AS High_Value_Orders
FROM Orders;
```

Another commonly used approach is:

```sql
SELECT
    SUM(
        CASE
            WHEN Amount > 20000 THEN 1
            ELSE 0
        END
    ) AS High_Value_Orders
FROM Orders;
```

This counts the number of orders above 20,000.

---

# Complete Business Example

## Business Question

> Which product categories have generated more than ₹20,000 in sales?

```sql
SELECT Category,
       COUNT(*) AS Total_Orders,
       SUM(Amount) AS Total_Sales,
       AVG(Amount) AS Average_Order_Value,
       MIN(Amount) AS Lowest_Order,
       MAX(Amount) AS Highest_Order
FROM Orders
GROUP BY Category
HAVING SUM(Amount) > 20000
ORDER BY Total_Sales DESC;
```

## What This Query Does

| SQL Component | Purpose |
|---|---|
| `COUNT(*)` | Counts orders |
| `SUM(Amount)` | Calculates total sales |
| `AVG(Amount)` | Calculates average order value |
| `MIN(Amount)` | Finds the lowest order |
| `MAX(Amount)` | Finds the highest order |
| `GROUP BY` | Creates a group for each category |
| `HAVING` | Filters categories based on total sales |
| `ORDER BY` | Sorts results from highest sales |

---

# SQL Query Structure to Remember

A typical aggregation query looks like this:

```sql
SELECT column_name,
       AGGREGATE_FUNCTION(column_name)
FROM table_name
WHERE condition
GROUP BY column_name
HAVING aggregate_condition
ORDER BY column_name;
```

### Easy Way to Remember

> **SELECT → Choose data**  
> **FROM → Choose table**  
> **WHERE → Filter rows**  
> **GROUP BY → Create groups**  
> **HAVING → Filter groups**  
> **ORDER BY → Sort results**

---

# Quick Revision

| Topic | Meaning | Remember |
|---|---|---|
| `COUNT()` | Counts records | How many? |
| `SUM()` | Adds values | What is the total? |
| `AVG()` | Calculates average | What is the average? |
| `MIN()` | Finds smallest value | What is the minimum? |
| `MAX()` | Finds largest value | What is the maximum? |
| `GROUP BY` | Groups similar values | Group before summarizing |
| `HAVING` | Filters groups | WHERE filters rows |
| `CASE` | Adds conditions | SQL's IF-like logic |

---

# Practice Tasks

Use the following `Orders` table:

| Order_ID | Customer | Category | City | Amount |
|---|---|---|---|---:|
| 101 | Amit | Electronics | Indore | 25,000 |
| 102 | Priya | Clothing | Mumbai | 5,000 |
| 103 | Rahul | Electronics | Indore | 18,000 |
| 104 | Neha | Clothing | Delhi | 7,000 |
| 105 | Amit | Electronics | Indore | 30,000 |
| 106 | Rohit | Furniture | Mumbai | 20,000 |

### Basic Practice

1. Count the total number of orders.
2. Calculate the total sales amount.
3. Find the average order amount.
4. Find the lowest and highest order amount.
5. Calculate total sales for each category.
6. Count the number of orders in each city.
7. Find categories where total sales are greater than ₹20,000.
8. Categorize orders as High, Medium, or Low value using `CASE`.

### Business Practice

**Task:** Create a sales summary by category showing:

- Category name
- Total number of orders
- Total sales
- Average order value
- Highest order value

Then display only categories with total sales above ₹15,000 and sort them by total sales from highest to lowest.

---

# Final Key Takeaway

**Aggregation helps transform raw transaction-level data into meaningful business summaries.**

As a Data Analyst, you will frequently use:

> **COUNT → How many?**  
> **SUM → How much in total?**  
> **AVG → What is the average?**  
> **MIN/MAX → What are the smallest and largest values?**  
> **GROUP BY → Compare groups.**  
> **HAVING → Filter summarized results.**  
> **CASE → Apply business logic.**

These concepts form the foundation for more advanced SQL analysis, including **JOINs, subqueries, window functions, and reporting queries**.
