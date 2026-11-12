# Day 15 — SQL Functions

## Introduction

SQL functions help Data Analysts **clean, transform, calculate, and analyze data directly inside a database**.

For example, business data may contain:

- Customer names with inconsistent capitalization
- Extra spaces in text
- Missing values (`NULL`)
- Dates that need to be grouped by month or year
- Sales data that requires calculations
- Categories that need business rules

SQL functions help solve these problems without manually changing the original data.

In this lesson, we will cover:

- String functions
- Date functions
- NULL handling
- `COALESCE`
- Conditional logic
- Business calculations

Each topic includes **definition, syntax, examples, business applications, best practices, quick revision, and practice tasks**.

> **Note:** SQL function names and syntax can vary slightly between MySQL, PostgreSQL, SQL Server, and Oracle. The concepts remain the same.

---

# 1. String Functions

## Definition

**String functions** are used to manipulate and transform text data.

They are useful for cleaning data such as:

- Customer names
- Email addresses
- Cities
- Product names
- Addresses

Let's assume we have a `Customers` table:

| Customer_ID | Customer_Name | City | Email |
|---|---|---|---|
| 101 | `amit sharma` | ` indore ` | amit@gmail.com |
| 102 | `PRIYA SINGH` | `Mumbai` | priya@gmail.com |

---

## A. UPPER()

### Definition

Converts text into **uppercase**.

### Syntax

```sql
UPPER(column_name)
```

### Example

```sql
SELECT Customer_Name,
       UPPER(Customer_Name) AS Upper_Name
FROM Customers;
```

### Result

`amit sharma` → `AMIT SHARMA`

### Business Application

Standardize customer names or city names for reporting.

### Remember

> **UPPER = Convert text to capital letters.**

---

## B. LOWER()

### Definition

Converts text into **lowercase**.

### Syntax

```sql
LOWER(column_name)
```

### Example

```sql
SELECT LOWER(Email) AS Clean_Email
FROM Customers;
```

### Business Application

Useful for standardizing email addresses before analysis.

### Remember

> **LOWER = Convert text to small letters.**

---

## C. LENGTH()

### Definition

Returns the number of characters in a text value.

### Syntax

```sql
LENGTH(column_name)
```

### Example

```sql
SELECT Customer_Name,
       LENGTH(Customer_Name) AS Name_Length
FROM Customers;
```

> In SQL Server, `LEN()` is commonly used instead of `LENGTH()`.

### Business Application

Check data quality or identify unusually short or long values.

---

## D. TRIM()

### Definition

Removes extra spaces from the beginning and end of text.

### Syntax

```sql
TRIM(column_name)
```

### Example

```sql
SELECT TRIM(City) AS Clean_City
FROM Customers;
```

`" Indore "` → `"Indore"`

### Business Application

Useful for data cleaning because extra spaces can cause duplicate categories.

For example:

```text
Indore
 Indore
Indore
```

These may be treated as different values without cleaning.

### Best Practice

Use `TRIM()` when working with imported text data.

### Remember

> **TRIM = Remove extra spaces from the beginning and end.**

---

## E. CONCAT()

### Definition

Combines two or more text values.

### Syntax

```sql
CONCAT(value1, value2, ...)
```

### Example

```sql
SELECT CONCAT(Customer_Name, ' - ', City) AS Customer_Details
FROM Customers;
```

### Result

```text
amit sharma - Indore
PRIYA SINGH - Mumbai
```

### Business Application

Create labels, descriptions, or combined fields for reports.

> Some databases use different concatenation operators, such as `||` or `+`.

---

## F. SUBSTRING()

### Definition

Extracts part of a text string.

### Syntax

```sql
SUBSTRING(column_name, start_position, length)
```

### Example

Extract the first four characters:

```sql
SELECT SUBSTRING(Customer_Name, 1, 4)
FROM Customers;
```

### Business Application

Extract information from:

- Product codes
- Employee IDs
- Postal codes
- Transaction codes

### Example

If Product_ID is:

```text
ELEC-1001
```

You may extract `ELEC` to identify the product category.

---

## G. REPLACE()

### Definition

Replaces one piece of text with another.

### Syntax

```sql
REPLACE(column_name, old_text, new_text)
```

### Example

```sql
SELECT REPLACE(Customer_Name, 'amit', 'Amit')
FROM Customers;
```

### Business Application

Correct or standardize inconsistent values.

---

## String Functions Summary

| Function | Purpose |
|---|---|
| `UPPER()` | Converts to uppercase |
| `LOWER()` | Converts to lowercase |
| `LENGTH()` | Counts characters |
| `TRIM()` | Removes extra spaces |
| `CONCAT()` | Combines text |
| `SUBSTRING()` | Extracts part of text |
| `REPLACE()` | Replaces text |

---

# 2. Date Functions

## Definition

Date functions help analysts extract and manipulate information from date values.

Assume an `Orders` table:

| Order_ID | Order_Date | Amount |
|---|---|---:|
| 1001 | 2026-01-15 | 15,000 |
| 1002 | 2026-02-20 | 20,000 |
| 1003 | 2026-03-10 | 12,000 |

---

## A. Extracting Year

### Example

```sql
SELECT EXTRACT(YEAR FROM Order_Date) AS Order_Year
FROM Orders;
```

### Business Application

Analyze sales by year.

> In MySQL, you can also use:

```sql
YEAR(Order_Date)
```

---

## B. Extracting Month

### Example

```sql
SELECT EXTRACT(MONTH FROM Order_Date) AS Order_Month
FROM Orders;
```

### Business Application

Create monthly sales reports.

---

## C. Extracting Day

```sql
SELECT EXTRACT(DAY FROM Order_Date) AS Order_Day
FROM Orders;
```

---

## D. Current Date

Many SQL databases provide a function to return the current date.

Examples include:

```sql
CURRENT_DATE
```

or database-specific functions such as:

```sql
GETDATE()
```

### Business Application

Calculate how many days have passed since an order.

---

## E. Date Difference

A date difference calculates the time between two dates.

### SQL Server Example

```sql
DATEDIFF(day, Order_Date, GETDATE())
```

This calculates the number of days between the order date and today.

### Business Application

Useful for:

- Customer retention analysis
- Delivery time analysis
- Employee tenure
- Overdue payments

---

## F. Date Addition

You can add a time period to a date.

### MySQL Example

```sql
DATE_ADD(Order_Date, INTERVAL 30 DAY)
```

### Business Example

Calculate a payment due date that is 30 days after an invoice date.

---

### Best Practice for Date Functions

Always check:

- The database system you are using.
- The date format.
- Whether the column is actually stored as a date instead of text.

### Remember

> **Date functions help answer: When did something happen?**

---

# 3. NULL Handling

## What Is NULL?

`NULL` represents a **missing, unknown, or unavailable value**.

It is not the same as:

- `0`
- An empty string `''`
- The word `"NULL"`

### Example

| Customer | Phone |
|---|---|
| Amit | 9876543210 |
| Priya | NULL |

Priya's phone number is unknown or unavailable.

---

## Finding NULL Values

### Syntax

```sql
WHERE column_name IS NULL
```

### Example

```sql
SELECT Customer_Name
FROM Customers
WHERE Phone IS NULL;
```

### Finding Non-NULL Values

```sql
SELECT Customer_Name
FROM Customers
WHERE Phone IS NOT NULL;
```

---

## Important: Do Not Use `= NULL`

This is incorrect:

```sql
WHERE Phone = NULL
```

Use:

```sql
WHERE Phone IS NULL
```

### Business Application

Analysts check `NULL` values to:

- Identify missing customer information.
- Find incomplete transactions.
- Measure data quality.

### Remember

> **NULL = Missing or unknown value.**

---

# 4. COALESCE

## Definition

`COALESCE()` returns the **first non-NULL value** from a list of values.

### Syntax

```sql
COALESCE(value1, value2, value3, ...)
```

### Example

Suppose some customers do not have a phone number.

```sql
SELECT Customer_Name,
       COALESCE(Phone, 'Not Available') AS Phone_Number
FROM Customers;
```

### Result

| Customer_Name | Phone_Number |
|---|---|
| Amit | 9876543210 |
| Priya | Not Available |

### Business Application

`COALESCE()` is often used in reports to replace missing values with:

- `0`
- `'Unknown'`
- `'Not Available'`

### Example with Sales

```sql
SELECT Product_Name,
       COALESCE(Sales, 0) AS Total_Sales
FROM Products;
```

### Best Practice

Be careful when replacing `NULL` with zero. A missing value does not always mean the actual value is zero.

### Remember

> **COALESCE = Return the first available non-NULL value.**

---

# 5. Conditional Logic

Conditional logic allows SQL to make decisions based on specific conditions.

The most commonly used tool is `CASE`.

## CASE Statement

### Syntax

```sql
CASE
    WHEN condition THEN result
    WHEN condition THEN result
    ELSE result
END
```

### Example: Categorize Sales

```sql
SELECT Order_ID,
       Amount,
       CASE
           WHEN Amount >= 50000 THEN 'High'
           WHEN Amount >= 20000 THEN 'Medium'
           ELSE 'Low'
       END AS Sales_Category
FROM Orders;
```

### Result

| Order_ID | Amount | Sales_Category |
|---|---:|---|
| 1001 | 15,000 | Low |
| 1002 | 20,000 | Medium |

### Business Application

Use `CASE` for:

- Customer segmentation
- Performance ratings
- Sales categories
- Employee performance levels
- Business rules

### Best Practice

Arrange conditions from specific to general.

For example:

```sql
CASE
    WHEN Amount >= 50000 THEN 'High'
    WHEN Amount >= 20000 THEN 'Medium'
    ELSE 'Low'
END
```

SQL checks conditions in order and stops when it finds the first matching condition.

### Remember

> **CASE = IF-THEN logic in SQL.**

---

# 6. Business Calculations

SQL allows Data Analysts to perform calculations directly in queries.

Assume an `Order_Details` table:

| Product | Quantity | Price | Discount |
|---|---:|---:|---:|
| Laptop | 2 | 50,000 | 5,000 |
| Phone | 3 | 20,000 | 3,000 |

---

## A. Basic Calculation

### Calculate Total Sales

```sql
SELECT Product,
       Quantity,
       Price,
       Quantity * Price AS Gross_Sales
FROM Order_Details;
```

### Formula

> **Gross Sales = Quantity × Price**

---

## B. Calculate Net Sales

```sql
SELECT Product,
       Quantity * Price AS Gross_Sales,
       Discount,
       (Quantity * Price) - Discount AS Net_Sales
FROM Order_Details;
```

### Formula

> **Net Sales = Gross Sales − Discount**

---

## C. Calculate Profit

Suppose you have a `Cost` column.

```sql
SELECT Product,
       Revenue,
       Cost,
       Revenue - Cost AS Profit
FROM Products;
```

### Formula

> **Profit = Revenue − Cost**

---

## D. Calculate Profit Margin

```sql
SELECT Product,
       Revenue,
       Cost,
       ((Revenue - Cost) / Revenue) * 100 AS Profit_Margin
FROM Products;
```

### Formula

> **Profit Margin % = (Profit ÷ Revenue) × 100**

### Best Practice: Avoid Division by Zero

Use `NULLIF()` when the denominator may be zero:

```sql
SELECT Product,
       ((Revenue - Cost) / NULLIF(Revenue, 0)) * 100 AS Profit_Margin
FROM Products;
```

If `Revenue` is zero, `NULLIF(Revenue, 0)` returns `NULL`, helping avoid a division-by-zero error in databases that support this behavior.

---

# Complete Business Example

## Business Question

> Create a clean monthly sales report and categorize each order based on its sales value.

```sql
SELECT
    Order_ID,
    UPPER(TRIM(Customer_Name)) AS Customer_Name,
    EXTRACT(YEAR FROM Order_Date) AS Order_Year,
    EXTRACT(MONTH FROM Order_Date) AS Order_Month,
    COALESCE(Discount, 0) AS Discount,
    Quantity * Price AS Gross_Sales,
    (Quantity * Price) - COALESCE(Discount, 0) AS Net_Sales,
    CASE
        WHEN (Quantity * Price) >= 50000 THEN 'High Value'
        WHEN (Quantity * Price) >= 20000 THEN 'Medium Value'
        ELSE 'Low Value'
    END AS Order_Category
FROM Orders;
```

### What This Query Does

| Function/Logic | Purpose |
|---|---|
| `TRIM()` | Removes extra spaces |
| `UPPER()` | Standardizes customer names |
| `EXTRACT()` | Gets year and month |
| `COALESCE()` | Handles missing discounts |
| `Quantity * Price` | Calculates gross sales |
| `CASE` | Categorizes orders |

---

# Quick Revision

| Topic | Purpose | Key Function/Concept |
|---|---|---|
| String Functions | Clean and transform text | `UPPER()`, `TRIM()` |
| Date Functions | Analyze dates | `EXTRACT()`, `DATEDIFF()` |
| NULL Handling | Work with missing data | `IS NULL` |
| COALESCE | Replace/select non-NULL values | `COALESCE()` |
| Conditional Logic | Apply business rules | `CASE` |
| Business Calculations | Calculate business metrics | `+`, `-`, `*`, `/` |

---

# Practice Tasks

Assume you have the following table:

### `Sales`

| Order_ID | Customer_Name | Order_Date | Product | Quantity | Price | Discount |
|---:|---|---|---|---:|---:|---:|
| 101 | `amit sharma` | 2026-01-15 | Laptop | 2 | 50,000 | 5,000 |
| 102 | ` PRIYA SINGH ` | 2026-02-20 | Phone | 3 | 20,000 | NULL |
| 103 | `rahul verma` | 2026-03-10 | Tablet | 5 | 15,000 | 2,000 |

### Basic Practice

1. Convert all customer names to uppercase.
2. Remove extra spaces from customer names.
3. Extract the year from `Order_Date`.
4. Extract the month from `Order_Date`.
5. Replace missing discounts with `0`.
6. Calculate gross sales for each order.
7. Calculate net sales after discount.
8. Categorize orders as:
   - High Value: Gross Sales ≥ 100,000
   - Medium Value: Gross Sales ≥ 50,000
   - Low Value: Below 50,000

### Business Practice Task

Create a **Sales Analysis Report** that displays:

- Order ID
- Clean customer name
- Order year
- Order month
- Product
- Gross sales
- Discount
- Net sales
- Order category

Use:

- `TRIM()`
- `UPPER()`
- A date function
- `COALESCE()`
- Business calculations
- `CASE`

---

# Final Key Takeaway

SQL functions allow a Data Analyst to transform **raw database data into analysis-ready information**.

The most important concepts to remember are:

> **String Functions → Clean text**  
> **Date Functions → Analyze time**  
> **NULL Handling → Manage missing data**  
> **COALESCE → Handle NULL values**  
> **CASE → Apply business logic**  
> **Calculations → Create business metrics**

### Data Analyst Mindset

When working with raw data, always ask:

**1. Does the data need cleaning?**  
**2. Are there missing values?**  
**3. Do I need to extract information from dates or text?**  
**4. What business calculation will help answer the business question?**

Answering these questions will help you write more effective SQL queries and produce meaningful business insights.
