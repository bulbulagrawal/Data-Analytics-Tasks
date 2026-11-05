# Day 11

# Daily Task

# Distribution, Outliers & Relationships for Data Analysts

This topic helps a data analyst understand **how data is spread, identify unusual values, and find relationships between variables**.

---

# 1. Distribution

A **distribution** describes how values are spread across a dataset.

For example, consider the daily sales of a store:

`100, 120, 125, 130, 135, 140, 150, 300`

A distribution helps us understand:

- Where most values are located
- How spread out the data is
- Whether the data is symmetrical
- Whether unusual values (outliers) exist

### Common ways to visualize distribution

- Histogram
- Box plot
- Frequency table
- Scatter plot (for relationships between two variables)

### Business Example

A company can analyze the distribution of customer spending to determine whether:

- Most customers spend a similar amount.
- A small number of customers spend significantly more.
- There are unusual transactions that need investigation.

---

# 2. Normal Distribution

A **normal distribution** is a symmetrical, bell-shaped distribution.

In a perfectly normal distribution:

- Most values are close to the mean.
- Fewer values occur as you move away from the mean.
- **Mean = Median = Mode** at the center.

### Simple Representation

```text
                /\
              /    \
            /        \
___________/__________\___________
          Mean = Median = Mode
```

### Business Example

Suppose employee performance scores are approximately normally distributed. Most employees may have average scores, while only a few have extremely high or low scores.

### Why It Matters

Normal distribution is important because many statistical techniques assume that data is normally distributed.

---

# 3. Skewness

**Skewness** describes whether a distribution is symmetrical or tilted toward one side.

## A. Positive Skew (Right Skew)

The long tail extends toward the **right**.

```text
   /\
  /  \______
 /          \________
```

Usually:

**Mean > Median**

### Example

Customer income often has a positive skew because most people earn moderate incomes while a small number earn extremely high incomes.

---

## B. Negative Skew (Left Skew)

The long tail extends toward the **left**.

```text
          /\
     ____/  \
____/        \
```

Usually:

**Mean < Median**

### Excel Formula for Skewness

```excel
=SKEW(A2:A100)
```

### Data Analyst Tip

When data is highly skewed, the **median** may provide a better representation of a typical value than the mean.

---

# 4. Outliers

An **outlier** is a value that is significantly different from most other values in a dataset.

### Example

Sales data:

`100, 110, 115, 120, 125, 130, 1000`

The value **1000** may be an outlier.

However, an outlier is not always an error. It could represent:

- A data entry mistake
- An unusual event
- A fraudulent transaction
- A high-value customer
- A genuine extreme observation

### Business Example

If most customers spend between ₹500 and ₹5,000 but one transaction is ₹500,000, an analyst should investigate whether it is:

- A genuine bulk purchase
- A data entry error
- Potential fraud

**Important:** Never remove an outlier automatically without understanding its business context.

---

# 5. IQR (Interquartile Range)

The **Interquartile Range (IQR)** measures the spread of the middle **50% of the data**.

### Formula

**IQR = Q3 − Q1**

Where:

- **Q1** = First Quartile (25th percentile)
- **Q3** = Third Quartile (75th percentile)

### Identifying Outliers Using IQR

The commonly used boundaries are:

**Lower Bound = Q1 − 1.5 × IQR**

**Upper Bound = Q3 + 1.5 × IQR**

Any value below the lower bound or above the upper bound can be considered a **potential outlier**.

### Excel Formulas

**Q1:**

```excel
=QUARTILE.INC(A2:A100,1)
```

**Q3:**

```excel
=QUARTILE.INC(A2:A100,3)
```

**IQR:**

```excel
=QUARTILE.INC(A2:A100,3)-QUARTILE.INC(A2:A100,1)
```

### Example of Lower and Upper Bound

If:

- Q1 = 20
- Q3 = 50

Then:

- IQR = 50 − 20 = 30
- Lower Bound = 20 − (1.5 × 30) = **−25**
- Upper Bound = 50 + (1.5 × 30) = **95**

Values below **−25** or above **95** are potential outliers.

---

# 6. Correlation

**Correlation** measures the strength and direction of the relationship between two numerical variables.

The correlation coefficient usually ranges from **−1 to +1**.

| Correlation | Meaning |
|---|---|
| +1 | Perfect positive relationship |
| Between 0 and +1 | Positive relationship |
| 0 | No linear relationship |
| Between −1 and 0 | Negative relationship |
| −1 | Perfect negative relationship |

### Example

Suppose advertising expenditure increases and sales also increase. This indicates a **positive correlation**.

Drag points

2468102468\\(X\\)\\(Y\\)

Linear correlation is positive (r = 0.98).

NegativeNear zeroPositive

Give feedback

### Excel Formula

```excel
=CORREL(A2:A100,B2:B100)
```

### Important Rule

**Correlation does not mean causation.**

For example, ice cream sales and cold drink sales may both increase during summer. This does not necessarily mean one causes the other.

---

# 7. Covariance

**Covariance** shows the direction in which two variables move together.

### Interpretation

- **Positive covariance:** Both variables tend to move in the same direction.
- **Negative covariance:** One variable tends to increase while the other decreases.
- **Covariance close to zero:** No strong directional relationship.

### Example

| Advertising Spend | Sales |
|---:|---:|
| 10 | 100 |
| 20 | 150 |
| 30 | 200 |

As advertising spend increases, sales also increase. Therefore, the covariance is likely **positive**.

### Excel Formulas

For a sample:

```excel
=COVARIANCE.S(A2:A100,B2:B100)
```

For a population:

```excel
=COVARIANCE.P(A2:A100,B2:B100)
```

### Correlation vs Covariance

| Feature | Covariance | Correlation |
|---|---|---|
| Shows direction | Yes | Yes |
| Shows strength clearly | No | Yes |
| Range | No fixed range | −1 to +1 |
| Affected by units | Yes | No |
| Easy to compare | Less easy | Easier |

**For most business analysis, correlation is easier to interpret than covariance.**

---

# 8. Scatter Plots

A **scatter plot** displays the relationship between two numerical variables.

Each dot represents one observation.

For example:

- X-axis → Advertising Spend
- Y-axis → Sales Revenue

Advertising spend vs sales

Illustrative monthly observations showing a positive relationship.

Ad Spend	Sales
10	95
15	120
20	145
25	155
30	190
35	210

### How to Create a Scatter Plot in Excel

1. Select two columns containing numerical data.
2. Go to **Insert**.
3. Select **Scatter Chart**.
4. Choose the appropriate scatter chart type.
5. Add chart titles and axis labels.

### How to Interpret a Scatter Plot

- Points moving upward → Positive relationship
- Points moving downward → Negative relationship
- Randomly scattered points → Little or no relationship
- A point far from other points → Possible outlier

---

# 9. Business Interpretation

Statistics are valuable only when they help answer a **business question**.

Here are some practical examples:

### Example 1: Customer Spending

**Observation:** The data is positively skewed.

**Business Interpretation:** Most customers spend relatively small amounts, while a few high-value customers spend significantly more.

**Action:** Create a loyalty program for high-value customers while developing strategies to increase spending among regular customers.

---

### Example 2: Sales and Advertising

**Observation:** Advertising spend and sales have a strong positive correlation.

**Business Interpretation:** Higher advertising expenditure is associated with higher sales.

**Action:** Investigate which advertising channels provide the best return on investment before increasing the budget.

---

### Example 3: Outlier Detection

**Observation:** A transaction is significantly larger than other transactions.

**Business Interpretation:** It could be a high-value sale, a data error, or potential fraud.

**Action:** Investigate the transaction before removing it from the dataset.

---

# Key Takeaways

- **Distribution** shows how data values are spread.
- A **normal distribution** is symmetrical and bell-shaped.
- **Skewness** shows whether data is tilted to the left or right.
- **Outliers** are unusual observations that require investigation.
- **IQR** helps measure the middle 50% of data and identify potential outliers.
- **Correlation** measures the strength and direction of a relationship.
- **Covariance** shows whether two variables move together.
- **Scatter plots** visually show relationships and possible outliers.
- Most importantly, a data analyst must connect statistical findings to **business decisions and actions**.
