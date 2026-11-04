# Statistics for Data Analysts  
## Day 10 — Descriptive Statistics

Descriptive statistics is the branch of statistics used to **organize, summarize, and describe data**. For a data analyst, these concepts are essential because they help transform a large dataset into meaningful insights.

For example, imagine you have sales data for 1,000 customers. Instead of examining every individual transaction, you can use statistics such as the **mean, median, range, and standard deviation** to quickly understand the data.

---

## 1. Population

A **population** is the complete group of people, objects, or observations that you want to study.

### Example
Suppose a company wants to analyze the average salary of all its employees.

- **Population:** Every employee in the company.

### Data Analyst Example
If an e-commerce company has 50,000 customers, all 50,000 customers represent the **population**.

**Key point:** A population includes **every member** of the group being studied.

---

## 2. Sample

A **sample** is a smaller group selected from a population for analysis.

Analyzing an entire population can sometimes be expensive or time-consuming. Therefore, analysts often study a sample to make conclusions about the larger population.

### Example

- **Population:** 50,000 customers
- **Sample:** 1,000 randomly selected customers

The sample should represent the population as accurately as possible.

### Why is sampling important?

Suppose you want customer feedback from millions of users. Collecting feedback from everyone may not be practical. A properly selected sample can provide useful insights more quickly.

---

## 3. Variables

A **variable** is a characteristic or piece of information that can have different values.

### Example: Employee Dataset

| Employee | Age | Department | Salary |
|---|---:|---|---:|
| A | 25 | Sales | 30,000 |
| B | 32 | IT | 50,000 |
| C | 28 | HR | 40,000 |

Here:

- **Age** is a variable.
- **Department** is a variable.
- **Salary** is a variable.

### Types of Variables

**1. Numerical (Quantitative) Variables**  
Contain numbers that can be measured or counted.

Examples:
- Sales
- Salary
- Age
- Number of customers

**2. Categorical (Qualitative) Variables**  
Contain categories or labels.

Examples:
- Gender
- Department
- Product Category
- City

---

# Measures of Central Tendency

Measures of central tendency help identify the **central or typical value** in a dataset.

The three main measures are:

1. Mean
2. Median
3. Mode

---

## 4. Mean

The **mean** is commonly known as the **average**.

### Formula

**Mean = Sum of all values ÷ Number of values**

### Example

Sales values:

`100, 200, 300, 400, 500`

Mean:

`(100 + 200 + 300 + 400 + 500) ÷ 5 = 300`

Therefore, the **average sales value is 300**.

### Excel Formula

```excel
=AVERAGE(A2:A6)
```

### When to Use Mean

The mean is useful when:

- Data is numerical.
- There are no extreme outliers.
- You want to calculate the overall average.

### Important Note

The mean can be affected by very large or very small values.

For example:

`20, 25, 30, 35, 500`

The value **500** significantly increases the mean, even though most values are between 20 and 35.

---

## 5. Median

The **median** is the middle value when data is arranged in ascending or descending order.

### Example 1: Odd Number of Values

Data:

`10, 20, 30, 40, 50`

The middle value is **30**.

Therefore:

**Median = 30**

### Example 2: Even Number of Values

Data:

`10, 20, 30, 40`

There are two middle values: 20 and 30.

Median:

`(20 + 30) ÷ 2 = 25`

### Excel Formula

```excel
=MEDIAN(A2:A6)
```

### When to Use Median

The median is especially useful when data contains **outliers**.

### Data Analyst Example

Consider employee salaries:

`25,000, 30,000, 32,000, 35,000, 500,000`

The mean will be heavily affected by the CEO's salary of 500,000. The median gives a better representation of a typical employee's salary.

---

## 6. Mode

The **mode** is the value that appears most frequently in a dataset.

### Example

Data:

`10, 20, 20, 30, 40`

The value **20** appears twice, while other values appear once.

Therefore:

**Mode = 20**

### Excel Formula

```excel
=MODE.SNGL(A2:A10)
```

### Data Analyst Applications

Mode is useful for identifying:

- Most popular product
- Most common customer age
- Most frequently purchased category

### Example

Product categories:

`Electronics, Clothing, Electronics, Food, Electronics`

The mode is **Electronics** because it occurs most frequently.

---

# Measures of Dispersion

Measures of dispersion show **how spread out the data is**.

---

## 7. Range

The **range** is the difference between the largest and smallest values.

### Formula

**Range = Maximum Value − Minimum Value**

### Example

Data:

`10, 15, 20, 25, 30`

Range:

`30 − 10 = 20`

### Excel Formula

```excel
=MAX(A2:A6)-MIN(A2:A6)
```

### Why is Range Important?

Range provides a quick understanding of how widely data values are distributed.

For example:

- Small range → values are closer together.
- Large range → values are more spread out.

---

## 8. Variance

**Variance** measures how far the data values are spread from their average.

It calculates the average of the **squared differences from the mean**.

A low variance means the values are relatively close together. A high variance means the values are more widely spread.

### Example

Consider two datasets:

**Dataset A:**  
`48, 49, 50, 51, 52`

**Dataset B:**  
`10, 30, 50, 70, 90`

Both may have a similar mean, but Dataset B is much more spread out. Therefore, Dataset B has a higher variance.

### Excel Formulas

For a **sample**:

```excel
=VAR.S(A2:A10)
```

For an entire **population**:

```excel
=VAR.P(A2:A10)
```

### Why Square the Differences?

If we simply added differences from the mean, positive and negative values would cancel each other out. Squaring the differences ensures that all deviations are positive.

\\(Var(X) = E(X^2) - [E(X)]^2\\)

For this normal curve with sigma 1.4, the identity above becomes

\\(Var(X)=\sigma^2=(\text{1.4})^2=\text{1.96}\\)

\\(\sigma\\)

μ-σ+σValue of XRelative density

Give feedback

---

## 9. Standard Deviation

**Standard deviation** measures how much individual values typically differ from the mean.

It is one of the most important statistical measures for data analysts.

### Interpretation

- **Low standard deviation:** Data points are close to the mean.
- **High standard deviation:** Data points are spread far from the mean.

### Example

Imagine two sales teams:

**Team A:**  
`95, 98, 100, 102, 105`

**Team B:**  
`50, 70, 100, 130, 150`

Both teams may have a similar average, but Team B has greater variation in performance.

Therefore, Team B has a **higher standard deviation**.

### Excel Formulas

For a **sample**:

```excel
=STDEV.S(A2:A10)
```

For a **population**:

```excel
=STDEV.P(A2:A10)
```

\\(\sigma = \sqrt{\frac{1}{N}\sum\_{i=1}^{N}(x_i-\mu)^2}\\)

The points have mean μ = 5 and σ = 1.5.

\\(\sigma\\)

Drag points

μ − σμ + σμ0246810

Give feedback

### Data Analyst Application

Standard deviation is useful for analyzing:

- Sales consistency
- Customer spending behavior
- Product quality
- Employee performance
- Financial risk

---

## 10. Percentiles

A **percentile** shows the position of a value relative to the rest of the dataset.

For example:

- **90th percentile** means the value is higher than approximately 90% of the observations.
- **50th percentile** is the same as the median.

### Example

Suppose a student's score is in the **90th percentile**.

This means the student performed better than approximately 90% of the students in the dataset.

### Excel Formula

```excel
=PERCENTILE.INC(A2:A100,0.90)
```

Here:

- `A2:A100` is the data range.
- `0.90` represents the 90th percentile.

### Data Analyst Applications

Percentiles are commonly used for:

- Customer spending analysis
- Salary analysis
- Website performance
- Employee performance

For example, an analyst may identify the **top 10% of customers** based on their total spending.

---

## 11. Quartiles

**Quartiles** divide a sorted dataset into **four equal parts**.

There are three main quartiles:

| Quartile | Meaning |
|---|---|
| Q1 | 25% of the data falls below this value |
| Q2 | 50% of the data falls below this value (Median) |
| Q3 | 75% of the data falls below this value |

### Visual Representation

```text
Minimum      Q1        Q2 (Median)       Q3       Maximum
   |----------|------------|-------------|----------|
    0%       25%          50%           75%       100%
```

### Excel Formulas

**First Quartile (Q1):**

```excel
=QUARTILE.INC(A2:A100,1)
```

**Second Quartile (Q2 / Median):**

```excel
=QUARTILE.INC(A2:A100,2)
```

**Third Quartile (Q3):**

```excel
=QUARTILE.INC(A2:A100,3)
```

### Interquartile Range (IQR)

The **Interquartile Range** measures the spread of the middle 50% of the data.

**IQR = Q3 − Q1**

### Excel Formula

```excel
=QUARTILE.INC(A2:A100,3)-QUARTILE.INC(A2:A100,1)
```

IQR is particularly useful for **detecting outliers**.

A common rule is:

- Lower Boundary = Q1 − 1.5 × IQR
- Upper Boundary = Q3 + 1.5 × IQR

Values outside these boundaries may be considered potential outliers.

---

# Summary: Mean vs Median vs Mode

| Measure | What It Shows | Best Used For |
|---|---|---|
| **Mean** | Average value | Normally distributed data without major outliers |
| **Median** | Middle value | Data with outliers or skewed distributions |
| **Mode** | Most frequent value | Finding the most common value or category |

---

# Key Takeaways for Data Analysts

- **Population** is the complete group being studied, while a **sample** is a smaller part of that group.
- **Variables** are the characteristics or columns you analyze in a dataset.
- **Mean, median, and mode** help identify the central tendency of data.
- **Range, variance, and standard deviation** measure how spread out the data is.
- **Percentiles and quartiles** help understand the position and distribution of values.
- **Median and quartiles** are particularly useful when data contains outliers.
- In Excel, functions such as `AVERAGE`, `MEDIAN`, `STDEV.S`, `VAR.S`, and `QUARTILE.INC` make statistical analysis easier.

**For a data analyst, descriptive statistics is usually the first step before creating visualizations, finding patterns, or performing more advanced statistical analysis.**
