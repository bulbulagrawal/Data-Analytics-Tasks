# Day 12

# Daily Task

# Probability & Statistical Inference for Data Analysts

**Probability and statistical inference** help data analysts make decisions using data when it is not practical to study every member of a population.

For example, instead of asking **all customers** whether they like a product, a company can survey a **sample** and use statistical methods to draw conclusions about the larger customer population.

---

# 1. Probability Basics

**Probability** measures the likelihood that an event will occur.

Probability ranges from **0 to 1**:

| Probability | Meaning |
|---|---|
| 0 | Impossible event |
| 0.5 | 50% chance |
| 1 | Certain event |

### Basic Formula

**Probability = Number of favorable outcomes ÷ Total number of possible outcomes**

### Example: Tossing a Coin

There are two possible outcomes:

- Heads
- Tails

Probability of getting Heads:

**P(Heads) = 1 ÷ 2 = 0.5 = 50%**

### Business Example

Suppose 200 out of 1,000 customers make a repeat purchase.

The probability that a randomly selected customer makes a repeat purchase is:

**200 ÷ 1,000 = 0.20 = 20%**

### Excel Formula

```excel
=200/1000
```

---

# 2. Sampling

**Sampling** is the process of selecting a smaller group from a larger population.

### Example

A company has **100,000 customers** but wants feedback about its service.

Instead of surveying all customers:

- **Population:** 100,000 customers
- **Sample:** 2,000 selected customers

The company can analyze the sample and use the results to make inferences about the population.

### Common Sampling Methods

| Method | Description |
|---|---|
| Simple Random Sampling | Every member has an equal chance of selection |
| Systematic Sampling | Select every nth observation |
| Stratified Sampling | Divide the population into groups and sample from each group |
| Convenience Sampling | Select easily available participants |

**For data analysis, a representative sample is important because poor sampling can produce misleading results.**

---

# 3. Sampling Bias

**Sampling bias** occurs when the selected sample does not properly represent the population.

### Example

A company wants to measure customer satisfaction but surveys only its premium customers.

The results may be overly positive because regular customers are not represented properly.

### Common Causes of Sampling Bias

- Selecting only one group
- Using convenience sampling
- Excluding important customer segments
- Low survey response rates

### Business Impact

Sampling bias can lead to **incorrect business decisions** because the conclusions may not represent the entire population.

---

# 4. Confidence Intervals

A **confidence interval (CI)** provides a range of values that is likely to contain the true population value.

Instead of saying:

> The average customer satisfaction score is exactly 8.2.

An analyst may say:

> Based on our sample, we estimate that the population's average satisfaction score falls within a certain range.

### Example

Suppose a survey produces:

**Average satisfaction score = 8.2**

A 95% confidence interval is:

**7.9 to 8.5**

This means the sample provides an estimated range for the unknown population value.

### Important Note

A **95% confidence level** does not mean there is a 95% probability that the specific population value is inside one already-calculated interval. Instead, if the same sampling process were repeated many times, approximately 95% of the calculated intervals would contain the true population parameter.

### Business Use

Confidence intervals help analysts understand the **uncertainty** around an estimate.

A narrow interval generally provides a more precise estimate than a wide interval.

---

# 5. Hypothesis Testing

**Hypothesis testing** is a statistical method used to make decisions based on sample data.

It helps answer questions such as:

- Did a new marketing campaign increase sales?
- Does a new website design improve conversion rates?
- Is there a significant difference between two products?

### Basic Process

1. Define the hypotheses.
2. Collect sample data.
3. Perform a statistical test.
4. Calculate the p-value.
5. Compare the p-value with the significance level.
6. Make a conclusion.

A common significance level is **0.05 (5%)**.

---

# 6. Null Hypothesis (H₀)

The **null hypothesis** represents the assumption that there is **no effect, no difference, or no relationship**.

### Example: A/B Testing

A company tests a new website design.

**H₀:** The new design does not change the conversion rate.

The null hypothesis is the starting assumption that any observed difference happened due to random chance.

---

# 7. Alternative Hypothesis (H₁ or Hₐ)

The **alternative hypothesis** represents what the analyst is investigating.

It usually states that there **is an effect, difference, or relationship**.

### Example

**H₀:** The new website design does not change the conversion rate.

**H₁:** The new website design changes the conversion rate.

The data is then used to determine whether there is enough evidence to reject the null hypothesis.

---

# 8. p-value

A **p-value** helps measure how compatible the observed data is with the null hypothesis.

A smaller p-value indicates that the observed result would be less expected if the null hypothesis were true.

### Common Decision Rule

Using a significance level of **0.05**:

| p-value | Interpretation |
|---|---|
| p < 0.05 | Reject the null hypothesis |
| p ≥ 0.05 | Fail to reject the null hypothesis |

### Example

Suppose an A/B test gives:

**p-value = 0.03**

Since:

**0.03 < 0.05**

There is statistically significant evidence against the null hypothesis at the 5% significance level, so we **reject H₀**.

> **Important:** A p-value does not tell you the probability that the null hypothesis is true.

---

# 9. Statistical Significance

A result is **statistically significant** when the evidence from the data is strong enough, according to a chosen significance threshold, to reject the null hypothesis.

### Example

A company tests a new email campaign.

| Campaign | Conversion Rate |
|---|---:|
| Old Campaign | 10.0% |
| New Campaign | 10.5% |

Suppose the statistical test gives:

**p-value = 0.02**

At a 5% significance level, the difference is statistically significant.

However, statistical significance alone does **not** tell us whether the improvement is important for the business.

This leads to the next concept.

---

# 10. Practical vs Statistical Significance

## Statistical Significance

Answers:

> **Is the observed result unlikely to be due to random chance alone, based on the chosen statistical model and assumptions?**

It is usually evaluated using a p-value and significance level.

## Practical Significance

Answers:

> **Is the size of the effect large enough to matter to the business?**

### Example

A website's conversion rate increases:

- From **10.00%**
- To **10.05%**

With millions of users, even this very small difference might produce a very small p-value and be **statistically significant**.

But the business still needs to ask:

- Does the increase generate enough additional revenue?
- Is the new design expensive to implement?
- Is the improvement meaningful compared with the cost?

### Comparison

| Feature | Statistical Significance | Practical Significance |
|---|---|---|
| Main Question | Is the result supported by statistical evidence? | Does the result matter in the real world? |
| Focus | Probability and evidence | Business impact |
| Common Measure | p-value | Effect size, cost, revenue, ROI |
| Can exist alone? | Yes | Yes, but evidence should be evaluated |

---

# A Complete Business Example: A/B Testing

A company wants to test whether a new checkout page improves conversions.

### Step 1: Define Hypotheses

**H₀:** The new checkout page has no effect on the conversion rate.

**H₁:** The new checkout page changes the conversion rate.

### Step 2: Collect Data

| Version | Visitors | Purchases | Conversion Rate |
|---|---:|---:|---:|
| Old Page (A) | 10,000 | 1,000 | 10% |
| New Page (B) | 10,000 | 1,100 | 11% |

### Step 3: Perform a Statistical Test

The analyst performs an appropriate test and obtains a p-value.

Suppose:

**p-value = 0.03**

### Step 4: Make a Statistical Decision

Since:

**0.03 < 0.05**

The analyst rejects the null hypothesis at the 5% significance level.

### Step 5: Check Practical Significance

The conversion rate increased from **10% to 11%**.

The business should now evaluate:

- Additional revenue generated
- Cost of implementing the new page
- Customer experience
- Long-term business impact

This is how a data analyst combines **statistics with business decision-making**.

---

# Key Takeaways

- **Probability** measures the likelihood of an event.
- **Sampling** allows analysts to study a smaller group and make inferences about a population.
- **Sampling bias** occurs when a sample does not properly represent the population.
- **Confidence intervals** show the uncertainty around an estimated population value.
- **Hypothesis testing** helps evaluate claims using sample data.
- **Null hypothesis (H₀)** usually represents no effect or no difference.
- **Alternative hypothesis (H₁)** represents the effect or difference being investigated.
- A **p-value** helps assess how compatible the data is with the null hypothesis.
- **Statistical significance** does not automatically mean the result is important for the business.
- **Practical significance** focuses on real-world impact, such as revenue, cost, and ROI.

### Data Analyst Mindset

**Don't stop at "Is the result statistically significant?"**

Also ask:

> **"Is this result meaningful enough to make a business decision?"**
