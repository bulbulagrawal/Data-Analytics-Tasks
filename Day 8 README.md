#Day 8

# Pivot Tables & Pivot Charts – Detailed Notes

These notes cover Pivot Tables, Grouping, Calculated Fields, Filters, Slicers, Pivot Charts, and Business Reporting in Microsoft Excel, with definitions, syntax, examples, uses, and a key takeaway at the end.

## 1. Pivot Tables

A Pivot Table is an Excel tool used to summarize, organize, analyze, and compare large amounts of data without changing the original dataset. It allows users to calculate totals, counts, averages, and other summaries by arranging fields into rows, columns, values, and filters.

### Main components

- **Rows**: Display categories vertically, such as product names or employee names.
- **Columns**: Display categories horizontally, such as years or regions.
- **Values**: Show calculations, such as Sum of Sales or Average of Profit.
- **Filters**: Filter the entire Pivot Table based on a selected field.

### Example

Suppose your dataset contains the following sales records:
-----------------------------
| Region | Product |  Sales |
|  ---   |   ---   |  ---   |
| North  | Laptop  | 50,000 |
| South  | Laptop  | 40,000 |
| North  | Mobile  | 20,000 |
| South  | Mobile  | 30,000 |

A Pivot Table can summarize total sales by region:

|       Region    |   Total Sales |
|        ---      |     ---       |
|       North     |    70,000     |
|       South     |    70,000     |
| **Grand Total** | **1,40,000**  |

### Syntax / procedure

Pivot Tables do not use a formula syntax. They are created through Excel's interface.

1. Select the dataset, including column headers.
2. Go to Insert → PivotTable.
3. Choose the data source and where to place the Pivot Table.
4. Drag fields into Rows, Columns, Values, or Filters.
5. Change the calculation using Value Field Settings if necessary.

### Common calculations

| Calculation | Purpose |
| --- | --- |
| Sum | Calculates the total |
| Count | Counts records or values |
| Average | Calculates the mean |
| Max | Finds the highest value |
| Min | Finds the lowest value |
| % of Grand Total | Shows each item's share of the total |

Uses: Sales analysis, expense summaries, employee reports, inventory analysis, and performance tracking.

## 2. Grouping in Pivot Tables

How to Group Dates in Excel Pivot Tables - Xelplus - Leila Gharani

[xelplus.com](<https://www.xelplus.com/pivottable-dates-grouping/?utm_source=chatgpt.com>)

### Definition

Grouping combines related items into larger categories in a Pivot Table. It helps make reports easier to read and analyze by grouping dates, numbers, or selected text items.

### Types of grouping

- Date grouping: Groups dates by months, quarters, or years.
- Numeric grouping: Groups numbers into ranges, such as 0–100, 101–200, and so on.
- Manual grouping: Combines selected items into custom categories.

### Example 1: Grouping dates

Suppose the dataset contains daily sales dates. Instead of displaying every date separately, Excel can group them by month.

|   Date      | Sales |
|   ---       | ---   |
| 05-Jan-2026 | 10,000 |
| 15-Jan-2026 | 15,000 |
| 10-Feb-2026 | 20,000 |

After grouping by month:

|   Month   | Total Sales |
|    ---    |      ---    |
| January   |    25,000   |
| February  |    20,000   |

### Example 2: Grouping numbers

Student marks can be grouped into ranges:

| Marks Range | Students |
|    ---      |   ---    |
|   0–49      |    5     |
|   50–69     |    12    |
|   70–89     |    18    |
|   90–100    |    5     |

### Syntax / procedure

There is no formula syntax for Pivot Table grouping.

1. Place the date, number, or category field in Rows.
2. Right-click an item in the Pivot Table.
3. Select Group.
4. Choose the grouping interval or categories.
5. Click OK.

For dates, select Months, Quarters, Years, or other available intervals. For numeric data, specify the starting value, ending value, and interval size.

Uses: Monthly sales reports, yearly comparisons, age groups, salary ranges, and marks distribution.

Note: Date grouping may fail if the source column contains blank cells or values that Excel does not recognize as valid dates.

## 3. Calculated Fields and Calculated Concepts

### Definition

A Calculated Field is a custom field created inside a Pivot Table by using a formula based on other fields in the source data.

It allows you to perform additional calculations without manually adding the calculation to every row of the original dataset.

### Example: Calculate profit

Suppose your source data contains:

- Sales
- Cost

You want to calculate Profit.

The formula is:

$$
\text{Profit}=\text{Sales}-\text{Cost}
$$

**Example data:**

| Product |  Sales |  Cost  |
|   ---   |   ---  |  ---   |
| Laptop  | 50,000 | 35,000 |
| Mobile  | 30,000 | 20,000 |

The calculated profits are:

| Product | Profit |
|   ---   |   ---  |
| Laptop  | 15,000 |
| Mobile  | 10,000 |

A calculated field uses a formula beginning with `=` and references field names.

**Syntax** : =Sales-Cost

**Another example** is calculating a profit margin:
**Syntax** =(Sales-Cost)/Sales

Format the resulting field as a percentage when appropriate.

### Steps to create a calculated field

1. Select a cell inside the Pivot Table.
2. Go to PivotTable Analyze → Fields, Items & Sets → Calculated Field.
3. Enter a name, such as `Profit`.
4. Enter the formula.
5. Click Add or OK.

Menu availability can vary by Excel version and Pivot Table source.

### Calculated Field vs. Calculated Item

|    Feature   |               Calculated Field          |                       Calculated Item                               |
|      ---     |                     ---                 |                               ---                                   |
|   Definition | Creates a calculation using data fields |       Creates a calculation involving items within a field          |  
|    Example   |              Sales − Cost               |         Combining or comparing selected product items               |
|  Typical use |      Profit and other business metrics  |             Custom calculations between categories                  |
| Availability |  Supported in traditional Pivot Tables  | Supported in some traditional Pivot Table fields, with restrictions |

### Important concepts

- Calculated fields operate on source fields and are generally evaluated using the underlying records.
- A calculated field such as `Sales-Cost` is not necessarily the same as subtracting two displayed subtotals in a report.
- Calculated fields have limitations with certain data models and OLAP-based Pivot Tables; Power Pivot measures may be needed instead.

Uses: Profit calculations, profit margin, commission, revenue metrics, and performance analysis.

## 4. Filters in Pivot Tables

How to add conditional formatting a Microsoft Excel PivotTable without expressions - TechRepublic

[techrepublic.com](<https://www.techrepublic.com/article/add-conditional-formatting-pivottable-excel/?utm_source=chatgpt.com>)

### Definition

A Filter displays only the data that meets specified conditions. In Pivot Tables, filters help users focus on selected categories, values, or periods without deleting the underlying records.

### Types of filters

1. Report Filter: Filters the entire Pivot Table using a field placed in the Filters area.
2. Label Filter: Filters text labels based on conditions, such as Begins With or Contains.
3. Value Filter: Filters items based on calculations, such as sales greater than ₹50,000.
4. Date Filter: Filters dates by periods, such as This Month or Between two dates.
5. Manual Filter: Selects or deselects specific items from a dropdown list.

### Example

Suppose a sales report contains data for North, South, East, and West regions.

If you select North in the Region report filter, the Pivot Table displays only the North region's results.

| Region | Sales |
| --- | --- |
| North | 70,000 |

### Syntax / procedure

Pivot Table filters do not require formula syntax.

1. Drag a field into the Filters area, or use a field's dropdown.
2. Open the filter dropdown.
3. Select the required items or filtering condition.
4. Click OK.

For example, use a Value Filter to display products with sales greater than ₹50,000.

**Uses**: Finding top-performing products, analyzing a particular region, filtering reporting periods, and identifying low-performing categories.

## 5. Slicers

[py.aprender21.com](<https://py.aprender21.com/blog/excel-tablas-dinamicas-guia?utm_source=chatgpt.com>)

### Definition

A Slicer is a visual filtering control that displays selectable buttons for Pivot Tables. Instead of opening dropdown menus, users can click a button to filter data quickly.

Slicers make Excel dashboards more interactive and user-friendly.

### Example

A sales dashboard has a Region slicer with four buttons:

- North
- South
- East
- West

Clicking North filters the connected Pivot Table and Pivot Chart to show North region data.

### Syntax / procedure

Slicers do not use formula syntax.

1. Select a Pivot Table.
2. Go to PivotTable Analyze → Insert Slicer.
3. Select fields such as Region, Product, or Salesperson.
4. Click OK.
5. Select buttons in the slicer to filter the report.

For date-based filtering, Excel also offers a Timeline, which provides a visual control for selecting date periods.

### Slicer vs. Filter

|        Feature        |             Filter                  |                     Slicer                     |
|          ---          |               ---                   |                       ---                      |
|       Appearance      |            Dropdown menu            |                Clickable buttons               |
|       Ease of use     |       Requires opening a menu       |              Direct visual selection           |
| Dashboard suitability |      Useful for compact reports     |       Excellent for interactive dashboards     |
|   Multiple selections |   Usually through dropdown options  |  Often supported through multi-select controls |
|       Connections     | Applied to the relevant Pivot Table |   Can control multiple compatible Pivot Tables |

**Important**: To control multiple Pivot Tables with one slicer, use Slicer → Report Connections or PivotTable Connections. The Pivot Tables generally need to share the same compatible data source or pivot cache.

**Uses**: Interactive dashboards, regional reports, product analysis, and management reporting.

## 6. Pivot Charts

A Complete Guide To: Insert Pivotchart In Excel

[simplesheets.co](<https://www.simplesheets.co/blog/a-complete-guide-to-insert-pivotchart-in-excel?utm_source=chatgpt.com>)

### Definition

A Pivot Chart is a chart connected to a Pivot Table. It presents summarized data visually and allows users to explore the report using chart field buttons, filters, and connected slicers.

When the Pivot Table changes, the Pivot Chart updates to reflect the corresponding summary.

### Common types of Pivot Charts

- Column Chart: Compares sales across categories.
- Bar Chart: Compares categories using horizontal bars.
- Line Chart: Shows trends over time.
- Pie Chart: Shows the proportion of a whole, best for a small number of categories.
- Area Chart: Shows changes in totals over time.
- Combo Chart: Compares different measures, such as sales and profit, using different chart types.

### Example

Suppose a Pivot Table summarizes monthly sales.

|  Month   |  Sales |
|   ---    |   ---  |
| January  | 50,000 |
| February | 70,000 |
|  March   | 90,000 |

A column Pivot Chart displays one column for each month, making it easy to see that March has the highest sales.

### Syntax / procedure

Pivot Charts do not require formula syntax.

1. Select a cell inside the Pivot Table.
2. Go to Insert → PivotChart (or the PivotTable Analyze menu, depending on Excel version).
3. Choose the chart type.
4. Add a title and format the chart.
5. Use connected slicers or chart filters to explore the data.

### Pivot Chart vs. Normal Chart

|       Feature    |                 Pivot Chart                 |               Normal Chart               |
|        ---       |                     ---                     |                     ---                  |
|    Data source   |        Connected to a Pivot Table           | Usually references a cell range or table |
|    Interactivity | Supports Pivot filtering and field controls |   Depends on the chart and data setup    |
|       Updates    |         Follows Pivot Table summaries       |     Follows its referenced data range    |
|  Best suited for |             Interactive data analysis       |   Fixed charts and custom visualizations |

**Uses**: Sales trend analysis, regional comparisons, profit analysis, and executive dashboards.

## 7. Business Reporting

[rowspeak.ai](<https://rowspeak.ai/ja/blog/how-to-build-excel-dashboards/?utm_source=chatgpt.com>)

### Definition

Business Reporting is the process of collecting, organizing, summarizing, and presenting business data so that managers and stakeholders can monitor performance and make informed decisions.

In Excel, Pivot Tables and Pivot Charts are commonly used to turn raw transaction data into meaningful reports.

### Objectives of business reporting

- Monitor business performance.
- Track sales, expenses, revenue, and profit.
- Compare results across regions, products, and employees.
- Identify trends and unusual results.
- Support data-driven decision-making.

### Example: Sales performance report

Suppose a company records sales transactions throughout the year. A business report could contain:

|      KPI      |          Definition              |  Example  |
|      ---      |             ---                  |    ---    |
|   Total Sales |      Total value of sales        | ₹5,00,000 |
|   Total Cost  |     Total cost of goods sold     | ₹3,50,000 |
|  Gross Profit |         Sales minus cost         | ₹1,50,000 |
| Profit Margin |    Gross profit divided by sales |    30%    |
|   Top Product |   Product with the highest sales |   Laptop  |

### Useful formulas for reporting

1\. Total Sales

```
=SUM(SalesRange)
```

2\. Profit

```
=Sales-Cost
```

For a row-by-row calculation in a worksheet, if Sales is in B2 and Cost is in C2:

```
=B2-C2
```

3\. Profit Margin

```
=IFERROR((Sales-Cost)/Sales,0)
```

4\. Sales Growth Percentage

```
=IFERROR((CurrentSales-PreviousSales)/PreviousSales,0)
```

Format the profit margin and growth results as percentages.

### Steps to create an Excel business report

1. Collect data: Gather sales, cost, product, region, and date information.
2. Clean data: Remove duplicate records, correct errors, and ensure consistent column names and data types.
3. Create a Pivot Table: Summarize sales, costs, or profit by product, region, or month.
4. Add calculated metrics: Calculate profit, margins, and growth where appropriate.
5. Create Pivot Charts: Visualize trends and comparisons.
6. Add slicers: Let users filter by region, product, or other relevant categories.
7. Design a dashboard: Arrange KPIs, charts, and filters clearly.
8. Refresh the report: Refresh Pivot Tables after the source data changes.

### Best practices for business reporting

- Use clear titles, labels, and consistent number formats.
- Choose chart types that match the business question.
- Avoid unnecessary colors and too many charts.
- Keep the underlying source data organized in an Excel Table.
- Ensure totals and percentages are calculated correctly.
- Include a reporting period and define each KPI clearly.
- Refresh the report and verify results before sharing it.

**Uses**: Management dashboards, monthly sales reports, financial summaries, inventory reports, and employee performance reports.

## Quick revision table

|       Topic        |       Definition in brief           |               Main purpose                  |
|       ---          |               ---                   |                     ---                     |
|    Pivot Table     |   Summarizes and analyzes data      |     Fast calculations and summaries         |
|     Grouping       |   Combines items into categories    |     Easier analysis of dates and ranges     |
|   Calculated Field |   Adds a formula-based field        |       Derives metrics such as profit        |
|     Filters        |    Displays selected data           |       Focuses on specific conditions        |
|     Slicers        |   Visual filtering buttons          |           Interactive reporting             |
|     Pivot Charts   |   Charts connected to Pivot Tables  |               Visual analysis               |
| Business Reporting |    Presents business information    | Better decisions and performance monitoring |

## Key Takeaways

1. Pivot Tables convert large datasets into meaningful summaries without manually calculating every total.
2. Grouping organizes dates, numbers, and selected items into useful categories.
3. Calculated Fields create additional metrics, such as profit and profit margin, from existing fields.
4. Filters narrow the report to the data you need, while Slicers provide a visual and interactive way to do so.
5. Pivot Charts turn summarized information into charts that respond to Pivot Table filtering.
6. Business Reporting combines clean data, accurate KPIs, Pivot Tables, charts, and interactive filters to support decision-making.
7. The overall workflow is: Clean data → Create Pivot Table → Add calculations → Apply grouping and filters → Create Pivot Charts → Build a       dashboard → Refresh and verify.

**Remember**: Pivot Tables summarize data, grouping organizes it, calculated fields derive new metrics, filters and slicers control what you see, Pivot Charts visualize it, and business reporting turns the results into actionable information.
