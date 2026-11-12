# Day 18 — Advanced SQL for Data Analysts

## Introduction

Welcome to **Day 18 — Advanced SQL**.

So far, you have learned how to:

- Retrieve and filter data using `SELECT` and `WHERE`
- Summarize data using aggregate functions
- Combine tables using `JOINs`
- Use SQL functions for cleaning and calculations
- Solve complex problems using `UNION`, subqueries, and CTEs

Now, we move to **Advanced SQL**, especially **Window Functions**.

Window functions are extremely useful for Data Analysts because they allow you to perform calculations across related rows **without collapsing the individual rows**.

This lesson covers:

- Window functions
- `ROW_NUMBER()`
- `RANK()`
- `DENSE_RANK()`
- `LEAD()`
- `LAG()`
- Running totals
- Moving calculations
- Month-over-month analysis
- Top-N analysis
- Customer segmentation
- SQL optimization basics
- Index fundamentals

---

# Sample Data

We will use the following `Sales` table for most examples.

| Order_ID | Customer_ID | Order_Date | Category | Amount |
|---:|---:|---|---|---:|
| 1001 | C101 | 2026-01-05 | Electronics | 10,000 |
| 1002 | C102 | 2026-01-10 | Clothing | 8,000 |
| 1003 | C101 | 2026-02-05 | Electronics | 15,000 |
| 1004 | C103 | 2026-02-15 | Furniture | 20,000 |
| 1005 | C102 | 2026-03-05 | Clothing | 12,000 |
| 1006 | C101 | 2026-03-20 | Electronics | 25,000 |

---

# 1. Window Functions

## Definition

A **window function** performs a calculation across a set of related rows while keeping each individual row in the result.

This is the major difference between a window function and `GROUP BY`.

### Example: GROUP BY

```sql
SELECT Customer_ID,
       SUM(Amount) AS Total_Sales
FROM Sales
GROUP BY Customer_ID;
```

This produces **one row per customer**.

### Example: Window Function

```sql
SELECT
    Order_ID,
    Customer_ID,
    Amount,
    SUM(Amount) OVER (
        PARTITION BY Customer_ID
    ) AS Customer_Total
FROM Sales;
```

This keeps every order while also showing the customer's total sales.

---

## Basic Syntax

```sql
FUNCTION_NAME() OVER (
    PARTITION BY column_name
    ORDER BY column_name
)
```

### Important Components

#### `OVER()`

Tells SQL that the function is a window function.

#### `PARTITION BY`

Divides rows into groups.

For example:

```text
Customer A → Calculate separately
Customer B → Calculate separately
Customer C → Calculate separately
```

#### `ORDER BY`

Defines the sequence of rows inside the window.

### Remember

> **Window Function = Calculate across related rows without combining them into one row.**

---

# 2. ROW_NUMBER()

## Definition

`ROW_NUMBER()` assigns a unique sequential number to each row.

### Syntax

```sql
ROW_NUMBER() OVER (
    PARTITION BY column_name
    ORDER BY column_name
)
```

---

## Example: Number Orders for Each Customer

```sql
SELECT
    Customer_ID,
    Order_ID,
    Order_Date,
    ROW_NUMBER() OVER (
        PARTITION BY Customer_ID
        ORDER BY Order_Date
    ) AS Order_Number
FROM Sales;
```

### Result Concept

| Customer_ID | Order_ID | Order_Date | Order_Number |
|---|---:|---|---:|
| C101 | 1001 | 2026-01-05 | 1 |
| C101 | 1003 | 2026-02-05 | 2 |
| C101 | 1006 | 2026-03-20 | 3 |

### Business Application

Use `ROW_NUMBER()` to:

- Identify a customer's first purchase
- Remove duplicate records
- Number transactions
- Select the latest record for each customer

### Remember

> **ROW_NUMBER = Every row gets a unique number.**

---

# 3. RANK()

## Definition

`RANK()` assigns a rank based on a specified order.

If two rows have the same value, they receive the same rank, but **the next rank is skipped**.

### Example

Suppose sales are:

| Product | Sales |
|---|---:|
| Laptop | 100 |
| Phone | 90 |
| Tablet | 90 |
| Mouse | 80 |

Query:

```sql
SELECT
    Product,
    Sales,
    RANK() OVER (
        ORDER BY Sales DESC
    ) AS Sales_Rank
FROM Product_Sales;
```

### Result

| Product | Sales | Rank |
|---|---:|---:|
| Laptop | 100 | 1 |
| Phone | 90 | 2 |
| Tablet | 90 | 2 |
| Mouse | 80 | 4 |

Notice that rank **3 is skipped**.

### Business Application

Use `RANK()` when tied positions should affect the next rank.

### Remember

> **RANK = Ties share rank, gaps appear afterward.**

---

# 4. DENSE_RANK()

## Definition

`DENSE_RANK()` also assigns the same rank to tied values.

However, it **does not skip the next rank**.

### Example

```sql
SELECT
    Product,
    Sales,
    DENSE_RANK() OVER (
        ORDER BY Sales DESC
    ) AS Sales_Rank
FROM Product_Sales;
```

### Result

| Product | Sales | Dense Rank |
|---|---:|---:|
| Laptop | 100 | 1 |
| Phone | 90 | 2 |
| Tablet | 90 | 2 |
| Mouse | 80 | 3 |

---

## ROW_NUMBER vs RANK vs DENSE_RANK

| Function | Ties | Skips Rank? |
|---|---|---|
| `ROW_NUMBER()` | Gives different numbers | Not applicable |
| `RANK()` | Same rank | Yes |
| `DENSE_RANK()` | Same rank | No |

### Easy Example

```text
Values: 100, 90, 90, 80

ROW_NUMBER:  1, 2, 3, 4
RANK:        1, 2, 2, 4
DENSE_RANK:  1, 2, 2, 3
```

### Remember

> **ROW_NUMBER = Unique position**  
> **RANK = Ties with gaps**  
> **DENSE_RANK = Ties without gaps**

---

# 5. LAG()

## Definition

`LAG()` accesses a value from a **previous row**.

### Syntax

```sql
LAG(column_name) OVER (
    ORDER BY column_name
)
```

### Example

Compare each month's sales with the previous month.

| Month | Sales |
|---|---:|
| January | 100,000 |
| February | 120,000 |
| March | 150,000 |

```sql
SELECT
    Month,
    Sales,
    LAG(Sales) OVER (
        ORDER BY Month
    ) AS Previous_Month_Sales
FROM Monthly_Sales;
```

### Result

| Month | Sales | Previous_Month_Sales |
|---|---:|---:|
| January | 100,000 | NULL |
| February | 120,000 | 100,000 |
| March | 150,000 | 120,000 |

### Business Application

Use `LAG()` for:

- Month-over-month comparisons
- Previous transaction analysis
- Customer purchase comparisons
- Sales trend analysis

### Remember

> **LAG = Look backward.**

---

# 6. LEAD()

## Definition

`LEAD()` accesses a value from a **future or next row**.

### Syntax

```sql
LEAD(column_name) OVER (
    ORDER BY column_name
)
```

### Example

```sql
SELECT
    Month,
    Sales,
    LEAD(Sales) OVER (
        ORDER BY Month
    ) AS Next_Month_Sales
FROM Monthly_Sales;
```

### Result

| Month | Sales | Next_Month_Sales |
|---|---:|---:|
| January | 100,000 | 120,000 |
| February | 120,000 | 150,000 |
| March | 150,000 | NULL |

### Business Application

Use `LEAD()` to:

- Compare current performance with the next period
- Identify the next customer activity
- Analyze time gaps between events

### Remember

> **LEAD = Look forward.**

---

# 7. Running Totals

## Definition

A **running total** is a cumulative total that increases as new rows are added.

### Example Data

| Month | Sales |
|---|---:|
| January | 100,000 |
| February | 120,000 |
| March | 150,000 |

### Query

```sql
SELECT
    Month,
    Sales,
    SUM(Sales) OVER (
        ORDER BY Month
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
    ) AS Running_Total
FROM Monthly_Sales;
```

### Result

| Month | Sales | Running_Total |
|---|---:|---:|
| January | 100,000 | 100,000 |
| February | 120,000 | 220,000 |
| March | 150,000 | 370,000 |

### Business Application

Running totals are useful for:

- Year-to-date sales
- Cumulative revenue
- Cumulative expenses
- Inventory tracking

### Simplified Syntax

In many databases:

```sql
SUM(Sales) OVER (ORDER BY Month)
```

may also create a running total, but explicitly defining the window frame is often clearer and more predictable.

### Remember

> **Running Total = Current value + all previous values.**

---

# 8. Moving Calculations

## Definition

A **moving calculation** analyzes a limited range of nearby rows.

The most common example is a **moving average**.

### Example: 3-Month Moving Average

```sql
SELECT
    Month,
    Sales,
    AVG(Sales) OVER (
        ORDER BY Month
        ROWS BETWEEN 2 PRECEDING AND CURRENT ROW
    ) AS Three_Month_Moving_Average
FROM Monthly_Sales;
```

### How It Works

For March:

```text
January + February + March
─────────────────────────
            3
```

### Business Application

Moving averages help:

- Identify sales trends
- Reduce the effect of short-term fluctuations
- Forecast business performance

### Remember

> **Moving Average = Average of a recent group of rows.**

---

# 9. Month-over-Month (MoM) Analysis

## Definition

Month-over-month analysis compares performance in one month with the previous month.

### Step 1: Calculate Monthly Sales

```sql
WITH monthly_sales AS (
    SELECT
        DATE_TRUNC('month', Order_Date) AS Month,
        SUM(Amount) AS Total_Sales
    FROM Sales
    GROUP BY DATE_TRUNC('month', Order_Date)
)
SELECT *
FROM monthly_sales;
```

> `DATE_TRUNC()` is commonly used in PostgreSQL. Other databases use different date functions.

---

### Step 2: Use LAG()

```sql
WITH monthly_sales AS (
    SELECT
        DATE_TRUNC('month', Order_Date) AS Month,
        SUM(Amount) AS Total_Sales
    FROM Sales
    GROUP BY DATE_TRUNC('month', Order_Date)
)
SELECT
    Month,
    Total_Sales,
    LAG(Total_Sales) OVER (
        ORDER BY Month
    ) AS Previous_Month_Sales
FROM monthly_sales;
```

---

### Step 3: Calculate MoM Growth Percentage

```sql
WITH monthly_sales AS (
    SELECT
        DATE_TRUNC('month', Order_Date) AS Month,
        SUM(Amount) AS Total_Sales
    FROM Sales
    GROUP BY DATE_TRUNC('month', Order_Date)
),
sales_comparison AS (
    SELECT
        Month,
        Total_Sales,
        LAG(Total_Sales) OVER (
            ORDER BY Month
        ) AS Previous_Month_Sales
    FROM monthly_sales
)
SELECT
    Month,
    Total_Sales,
    Previous_Month_Sales,
    ROUND(
        (
            Total_Sales - Previous_Month_Sales
        ) * 100.0 /
        NULLIF(Previous_Month_Sales, 0),
        2
    ) AS MoM_Growth_Percentage
FROM sales_comparison;
```

### Formula

> **MoM Growth % = ((Current Month − Previous Month) / Previous Month) × 100**

### Business Application

MoM analysis helps businesses monitor:

- Sales growth
- Customer growth
- Website traffic
- Revenue trends

---

# 10. Top-N Analysis

## Definition

Top-N analysis identifies the best-performing **N records**.

Examples:

- Top 5 customers
- Top 10 products
- Top 3 employees in each department

---

## Example: Top 3 Products Overall

```sql
SELECT
    Product_Name,
    Total_Sales
FROM Product_Sales
ORDER BY Total_Sales DESC
LIMIT 3;
```

---

## Advanced Example: Top 3 Products in Each Category

```sql
WITH ranked_products AS (
    SELECT
        Category,
        Product_Name,
        Total_Sales,
        DENSE_RANK() OVER (
            PARTITION BY Category
            ORDER BY Total_Sales DESC
        ) AS Product_Rank
    FROM Product_Sales
)
SELECT *
FROM ranked_products
WHERE Product_Rank <= 3;
```

### Business Application

Top-N analysis helps management identify:

- Best-selling products
- Highest-value customers
- Top-performing regions

### Remember

> **PARTITION BY = Top N within each group.**

---

# 11. Customer Segmentation

## Definition

**Customer segmentation** means dividing customers into groups based on their behavior or value.

### Example

We can classify customers according to total spending.

```sql
WITH customer_sales AS (
    SELECT
        Customer_ID,
        SUM(Amount) AS Total_Spending
    FROM Sales
    GROUP BY Customer_ID
)
SELECT
    Customer_ID,
    Total_Spending,
    CASE
        WHEN Total_Spending >= 50000 THEN 'High Value'
        WHEN Total_Spending >= 20000 THEN 'Medium Value'
        ELSE 'Low Value'
    END AS Customer_Segment
FROM customer_sales;
```

### Business Application

Customer segmentation supports:

- Personalized marketing
- Loyalty programs
- Customer retention
- Targeted promotions

---

## Advanced Segmentation with NTILE

Some SQL databases support `NTILE()`.

For example, divide customers into four groups:

```sql
SELECT
    Customer_ID,
    Total_Spending,
    NTILE(4) OVER (
        ORDER BY Total_Spending DESC
    ) AS Customer_Quartile
FROM Customer_Sales;
```

This can divide customers into quartiles based on spending.

---

# 12. SQL Optimization Basics

## Definition

**SQL optimization** means writing queries that return the correct results efficiently.

This becomes very important when working with large datasets containing millions of rows.

---

## A. Select Only Required Columns

Avoid:

```sql
SELECT *
FROM Sales;
```

Prefer:

```sql
SELECT
    Order_ID,
    Customer_ID,
    Amount
FROM Sales;
```

### Why?

Retrieving unnecessary columns can increase:

- Processing time
- Memory usage
- Network usage

---

## B. Filter Early

Use `WHERE` to reduce the number of rows being processed.

```sql
SELECT
    Customer_ID,
    Amount
FROM Sales
WHERE Order_Date >= '2026-01-01';
```

---

## C. Be Careful with Large JOINs

Before joining large tables:

1. Understand the relationship.
2. Check for duplicate rows.
3. Select only required columns.
4. Filter data when appropriate.

---

## D. Avoid Unnecessary DISTINCT

`DISTINCT` can require additional processing.

Do not use it simply to hide duplicates caused by an incorrect JOIN.

Instead, first ask:

> Why are duplicate rows appearing?

---

## E. Check Query Execution Plans

Most database systems provide tools such as:

```sql
EXPLAIN
```

or execution plan features.

These help analysts and developers understand:

- How tables are accessed
- Whether indexes are being used
- Which operations consume the most resources

---

# 13. Index Fundamentals

## What Is an Index?

An **index** is a database structure that helps the database find data more quickly.

Think of it like the index at the end of a book.

Without an index, you may need to search through every page.

With an index, you can quickly find the required topic.

---

## Example

Suppose a company has millions of customer records.

This query searches by customer ID:

```sql
SELECT *
FROM Customers
WHERE Customer_ID = 101;
```

An index on `Customer_ID` can make searching faster.

---

## Common Columns for Indexing

Indexes are often useful for columns frequently used in:

- `WHERE`
- `JOIN`
- `ORDER BY`

For example:

```text
Customer_ID
Order_Date
Product_ID
```

---

## Important Trade-Off

Indexes improve **reading and searching** performance.

However, too many indexes can slow down:

- `INSERT`
- `UPDATE`
- `DELETE`

because indexes also need to be maintained.

### Best Practice

Do not create indexes on every column.

Consider:

- How frequently the column is searched
- Table size
- Query patterns
- Database workload

> Index design is usually handled by database administrators or data engineers, but Data Analysts should understand the fundamentals.

---

# Complete Business Analysis Example

## Business Question

> Analyze monthly sales performance and identify the top customers.

The analysis should include:

1. Monthly sales
2. Previous month sales
3. MoM growth
4. Running total

```sql
WITH monthly_sales AS (
    SELECT
        DATE_TRUNC('month', Order_Date) AS Month,
        SUM(Amount) AS Total_Sales
    FROM Sales
    GROUP BY DATE_TRUNC('month', Order_Date)
),

sales_analysis AS (
    SELECT
        Month,
        Total_Sales,

        LAG(Total_Sales) OVER (
            ORDER BY Month
        ) AS Previous_Month_Sales,

        SUM(Total_Sales) OVER (
            ORDER BY Month
            ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
        ) AS Running_Total
    FROM monthly_sales
)

SELECT
    Month,
    Total_Sales,
    Previous_Month_Sales,
    Running_Total,
    ROUND(
        (
            Total_Sales - Previous_Month_Sales
        ) * 100.0 /
        NULLIF(Previous_Month_Sales, 0),
        2
    ) AS MoM_Growth_Percentage
FROM sales_analysis
ORDER BY Month;
```

---

# Understanding the Query

| Feature | Purpose |
|---|---|
| CTE | Breaks analysis into steps |
| `SUM()` | Calculates monthly sales |
| `LAG()` | Gets previous month sales |
| Window `SUM()` | Calculates running total |
| `NULLIF()` | Prevents division by zero |
| `ROUND()` | Formats MoM percentage |

---

# Quick Revision

| Topic | Meaning | Remember |
|---|---|---|
| Window Function | Calculates across related rows | Keeps individual rows |
| `ROW_NUMBER()` | Unique row numbering | No ties |
| `RANK()` | Ranking with gaps | Ties skip ranks |
| `DENSE_RANK()` | Ranking without gaps | Ties do not skip ranks |
| `LAG()` | Previous row value | Look backward |
| `LEAD()` | Next row value | Look forward |
| Running Total | Cumulative value | Previous + current |
| Moving Average | Average over recent rows | Smooth trends |
| MoM Analysis | Compare with previous month | Use `LAG()` |
| Top-N | Find top performers | Use ranking |
| Segmentation | Divide customers into groups | Use `CASE` |
| Optimization | Improve query efficiency | Filter and select carefully |
| Index | Speeds up data retrieval | Like a book index |

---

# Practice Tasks

Use a `Sales` table containing:

- `Order_ID`
- `Customer_ID`
- `Order_Date`
- `Category`
- `Amount`

## Basic Practice

1. Assign a unique row number to every order.
2. Rank customers based on their total sales.
3. Compare `RANK()` and `DENSE_RANK()` using products with equal sales.
4. Use `LAG()` to display the previous order amount.
5. Use `LEAD()` to display the next order amount.
6. Calculate a running total of sales.
7. Calculate a 3-row moving average.

---

## Business Practice

### Task 1: Top Customers

Find the **top 3 customers based on total spending**.

### Task 2: Monthly Sales Growth

Create a report showing:

- Month
- Total sales
- Previous month sales
- MoM growth percentage

### Task 3: Customer Segmentation

Classify customers as:

- **High Value:** Total spending ≥ ₹50,000
- **Medium Value:** ₹20,000 to ₹49,999
- **Low Value:** Below ₹20,000

### Task 4: Top Products by Category

Find the **top 3 products within each category**.

**Hint:** Use:

```sql
DENSE_RANK() OVER (
    PARTITION BY Category
    ORDER BY Total_Sales DESC
)
```

---

# Final Key Takeaway

Day 18 completes the core SQL journey by introducing **advanced analytical SQL techniques**.

The most important concept is:

> **Window functions allow you to analyze relationships between rows while keeping the original detail of the data.**

### SQL Learning Journey

```text
Day 13 → Database Fundamentals + SELECT
Day 14 → Aggregation
Day 15 → SQL Functions
Day 16 → JOINs
Day 17 → Subqueries, UNION & CTEs
Day 18 → Advanced SQL
```

By completing these topics, you now have a strong SQL foundation for Data Analytics, including:

**SELECT → Filtering → Aggregation → Functions → JOINs → CTEs → Subqueries → Window Functions → Ranking → Running Totals → MoM Analysis**

These skills are widely used in real-world business analysis, dashboards, reporting, and data-driven decision-making.
