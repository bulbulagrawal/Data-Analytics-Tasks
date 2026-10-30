# Day 9
# Data Analytics – Daily Task Update
## Day 9: Dashboard Principles, KPI Cards, Power Query & Data Preparation

## 1. Introduction to Excel Dashboards

An Excel Dashboard is a visual representation of important business information in one place. It converts raw data into meaningful insights using KPI cards, charts, tables, filters, and interactive reports.

A dashboard helps management understand business performance and make better decisions without manually analyzing thousands of rows.

### Example: Sales Dashboard

Suppose a company has raw sales data containing:

| Date   | Region | Product | Sales  | Profit |
| ------ | ------ | ------- | ------ | ------ |
| 01-Jan | North  | Laptop  | 50,000 | 8,000  |
| 02-Jan | South  | Mobile  | 30,000 | 5,000  |
| 03-Jan | East   | Laptop  | 40,000 | 7,000  |
| 04-Jan | West   | Tablet  | 25,000 | 4,000  |

Using this data, we can create a dashboard displaying:

- Total Sales
- Total Profit
- Total Orders
- Average Sales
- Region-wise Sales
- Product-wise Performance
- Monthly Sales Trends

(https://images.openai.com/static-rsc-4/G99WX3ZfTwuAYbYXw6CGtFvLgsMiFL9XHuPoJJw9WidHMjL1m7D0WUdJEYL7TkZVj6oQ8PdRJq-TGwdEiw9NM5dynEEmZmftkQvI9SwwlQAmrCG7NVemfL5P8K9kxqP8RdzEDIiAlCXljlzDs03Hdre7-Zk82jYcO3IinOpgYt0?purpose=inline)

[rowspeak.ai](https://rowspeak.ai/ja/blog/how-to-build-excel-dashboards/?utm_source=chatgpt.com)

**Objective**: Convert raw business data into an easy-to-understand visual report.

## 2. Dashboard Principles

Dashboard principles are the guidelines used to design a professional, understandable, and effective dashboard.

### A. Simplicity

A dashboard should be simple and easy to understand.

- Avoid unnecessary information.
- Use clear headings.
- Avoid too many colors.
- Display only relevant KPIs and charts.

### B. Consistency

Maintain a consistent design throughout the dashboard.

- Use the same font style.
- Maintain consistent colors.
- Keep chart formats similar.
- Align objects properly.

### C. Data Accuracy

The dashboard should display correct and updated information.

- Check for duplicate records.
- Remove incorrect values.
- Verify formulas.
- Ensure data sources are correct.

### D. Visual Hierarchy

Important information should be displayed prominently.

**For example:**

1. Total Revenue
2. Total Profit
3. Total Orders
4. Sales Trends
5. Detailed Analysis

### E. Interactivity

Users should be able to filter and analyze information.

**Examples:**

- Select a particular region.
- Select a product category.
- Filter sales by month.
- Compare yearly performance.

### F. Proper Chart Selection

Choose charts according to the type of information.

| Chart        | Purpose                         |
| ------------ | ------------------------------- |
| Column Chart | Compare sales across regions    |
| Bar Chart    | Compare product performance     |
| Line Chart   | Show monthly sales trends       |
| Pie Chart    | Show percentage contribution    |
| Donut Chart  | Show category-wise contribution |
| Area Chart   | Show trends over time           |

Best practice: A dashboard should answer three questions:

1. What happened?
2. Where did it happen?
3. How is the business performing?

## 3. KPI Cards (Key Performance Indicators)

A KPI is a measurable value that helps an organization evaluate its performance against business objectives.

KPI Cards are visual boxes that display important business metrics.

[Crear paneles de excel automatizados usando macros y vba](https://images.openai.com/static-rsc-4/b5vOG2x0_3eY8us5MXmt-3QUTmETVRnTW0GFLe5ZDN2nAV_kPlbw7UfNnZYDBTBLRLpZAfOgj_uCukFzFDEqQ2-A6UwPstNjpBdeXRvNHp5NVD_om1QbVvscKwsXN4u3_vy2UoS09FQxt1DwaNIHna6j1vSxh1DtxpZ6y4Srn0U?purpose=inline)

[es.fiverr.com](https://es.fiverr.com/hanzala_shahid/create-interactive-excel-dashboard-using-macros-and-vba?utm_source=chatgpt.com)

### Common KPI Cards

| KPI           | Meaning                                  |
| ------------- | ---------------------------------------- |
| Total Sales   | Total revenue generated                  |
| Total Profit  | Total profit earned                      |
| Total Orders  | Number of orders received                |
| Average Sales | Average sales value                      |
| Profit Margin | Percentage of revenue retained as profit |
| Growth Rate   | Percentage increase or decrease in sales |

### Important Excel Formulas for KPI Cards

Assume:

- Column A = Order ID
- Column B = Region
- Column C = Product
- Column D = Sales
- Column E = Profit

1\. Total Sales

```
=SUM(D2:D100)
```

Adds all sales values.

2\. Total Profit

```
=SUM(E2:E100)
```

Calculates total profit.

3\. Total Orders

```
=COUNTA(A2:A100)
```

Counts non-empty order IDs.

If each order ID is unique, this gives the order count. Otherwise, use a distinct count through a PivotTable or Data Model.

4\. Average Sales

```
=AVERAGE(D2:D100)
```

Calculates average sales.

5\. Maximum Sales

```
=MAX(D2:D100)
```

Returns the highest sales value.

6\. Minimum Sales

```
=MIN(D2:D100)
```

Returns the lowest sales value.

7\. Profit Margin

```
=IFERROR(SUM(E2:E100)/SUM(D2:D100),0)
```

Format the result as a percentage.

8\. Sales Growth

Suppose:

- B2 = Current Month Sales
- C2 = Previous Month Sales

```
=IFERROR((B2-C2)/C2,0)
```

Format as a percentage.

### How to Create KPI Cards

1. Calculate KPI values using formulas or PivotTables.
2. Go to Insert.
3. Select Shapes.
4. Insert a rectangle.
5. Add a KPI heading.
6. Link the displayed value to a cell.

Example:

```
="Total Sales: "&TEXT(B2,"₹#,##0")
```

This displays the value from B2 in a currency format.

Important: KPI cards should display meaningful business indicators, not just numbers.

## 4. Charts in Excel

Charts convert numerical data into visual information.

They make it easier to identify trends, comparisons, patterns, and business performance.

[Clustered Column Chart example: Quarterly sales by clustered region | Exceljet](https://images.openai.com/static-rsc-4/VLWgi_bnCGXDToYu1ZX3YA58AdgNuSn76ptLT7hWN43EDz7XNUSgLXMslpiwMHfzfUS_qaogTDeXB0oTB7Xa91NstcxDUwjnwTAS2oGvU2-VPOEhHnqRwwab-LBYm4h6MV4jbUdGpAAVfIJGhT_Q_7-wnAxA-PpEool2JY2hrdI?purpose=inline)

[Excel-User.com: Excel Charts — Use an Image as Line Chart Markers](https://images.openai.com/static-rsc-4/SJ6jrX1HJLmpzUVA4nr7K5tGfXqwAScRLkmUIeJnTTigsE7gX5Gp6Gui7RvjPGbVBrtankHxssVWgWWVRdp95VjrlaWIyOpbvHUkdwCzhfxHg-AqJtfTmNdZ_-wBi6CFISxWbE1tRKW8YFFYfBpmyAbkMViSucIN0VmriTl4sIo?purpose=inline)

[Learn Pie and Doughnut Charts | Core Chart Types in Practice](https://images.openai.com/static-rsc-4/WInf0SS1_7DqkVqX30KQ0FJHjcPsI-CeG92ybQjHot9zZf2l_4uH9PA2JJ06zqDiefraLkUm6A9fVnP9AYbGSynkwEiYIB94KhiBuLjLgtVpye129hqGxD1C8ajd9DU91POMVon3zP8oA3FdY0Be7UdujvgV-MTeoIw0_6-Q5ds?purpose=inline)

### A. Column Chart

Purpose: Compare values across different categories.

Example: Region-wise Sales.

| Region | Sales  |
| ------ | ------ |
| North  | 50,000 |
| South  | 40,000 |
| East   | 60,000 |
| West   | 30,000 |

**Steps:**

1. Select the data.
2. Go to Insert.
3. Select Column Chart.
4. Choose Clustered Column.
5. Add chart title and data labels.

### B. Bar Chart

Purpose: Compare different products or categories.

Example: Product-wise Sales.

Useful when category names are long.

### C. Line Chart

Purpose: Display trends over time.

Example: Monthly Sales.

| Month    | Sales  |
| -------- | ------ |
| January  | 40,000 |
| February | 50,000 |
| March    | 65,000 |
| April    | 55,000 |

A line chart helps identify whether sales are increasing or decreasing.

### D. Pie Chart

Purpose: Display percentage contribution of categories.

Example: Sales contribution by region.

Limitation: Avoid using too many categories because the chart becomes difficult to read.

### E. Donut Chart

Similar to a pie chart but includes a blank center.

Useful for displaying category contribution and percentages.

### F. Combo Chart

Combines two chart types, such as:

- Column Chart: Total Sales
- Line Chart: Profit Margin

Useful when comparing two different business measures.

### Important Chart Formatting Options

- Chart Title
- Axis Titles
- Data Labels
- Legend
- Gridlines
- Chart Colors
- Number Formatting

Best practice: Use the right chart for the right business question.

## 5. Interactive Reports in Excel

An interactive report allows users to explore data by applying filters without changing the original dataset.

Interactive reports are commonly created using:

1. PivotTables
2. PivotCharts
3. Slicers
4. Timelines
5. Drop-down lists

[Sales Performance Dashboard | Excel Project by Marwa Ali on Dribbble](https://images.openai.com/static-rsc-4/QyCjRM5Wa-wJLLirXcuTpbFIg5gHBzvnT-tAqao02wg6TUI2g1JbG3AbJBB8KBnjZIfFJLOZQSW0DwAizju_0roJNAT1Kc9hIlQCy-2dB8UCwN-YCmcFKSUfv9bk_DI-2NoUB4lwrPUhEUNDTokm8FD8Bce-FQl3u8i1qM7aGwI?purpose=inline)

[dribbble.com](https://dribbble.com/shots/26312286-Sales-Performance-Dashboard-Excel-Project?utm_source=chatgpt.com)

### A. PivotTable

A PivotTable summarizes large datasets quickly.

Example: Region-wise Sales Summary.

| Region | Total Sales |
| ------ | ----------- |
| North  | 50,000      |
| South  | 40,000      |
| East   | 60,000      |
| West   | 30,000      |

Steps:

1. Select the dataset.
2. Go to Insert.
3. Select PivotTable.
4. Choose New Worksheet.
5. Drag Region into Rows.
6. Drag Sales into Values.
7. Ensure the calculation is Sum of Sales.

### B. Slicers

Slicers are visual buttons that allow users to filter PivotTables and PivotCharts.

Example:

- North
- South
- East
- West

Steps:

1. Select the PivotTable.
2. Go to PivotTable Analyze.
3. Click Insert Slicer.
4. Select Region.
5. Click OK.
6. Select a region to filter the report.

### C. Timeline

A Timeline is a visual date filter for PivotTables.

Steps:

1. Select the PivotTable.
2. Go to PivotTable Analyze.
3. Click Insert Timeline.
4. Select the Date field.
5. Choose Year, Quarter, Month, or Day.

### D. Data Validation Drop-down

Used to create a drop-down list for selecting categories.

**Example:**

```
=UNIQUE(B2:B100)
```

This formula generates a unique list of regions in modern Excel.

To create a drop-down:

1. Select a cell.
2. Go to Data.
3. Select Data Validation.
4. Choose List.
5. Select the source range containing region names.
6. Click OK.

### E. Conditional Formatting

Highlights important values using colors, data bars, or icons.

**Example:**

```
=D2>50000
```

This condition can be used in Conditional Formatting to highlight sales greater than 50,000.

Business use: Identify high-performing products and low-performing regions quickly.

# 6. Introduction to Power Query

Power Query is an Excel tool used to import, clean, transform, and combine data from different sources.

It helps automate repetitive data-cleaning activities.

Instead of manually cleaning data every time, users can create a transformation process once and refresh it whenever new data arrives.

[Power Query For Data Preparation In Excel: An Introduction And Walk-Through For Beginners — Eval Academy](https://images.openai.com/static-rsc-4/8VzgKYCZhbf-6oZju_jRLu4-vGvwsUcf5Cmr90V3ynQQ-pv5GL0UvK4cA4mqkRs9ZI8WO4tIfhSZLVA5_2SKCZ1fSKAXgTsZ-hHMEKhgFAnascLzrr4bEYr2Q2EW-5AQptRJSwDt1Pe5JaAgfvysvmUZyggQD_kbi6LduaW_ClA?purpose=inline)

[evalacademy.com](https://www.evalacademy.com/articles/power-query-for-data-preparation-in-excel-an-introduction-and-walk-through-for-beginners?utm_source=chatgpt.com)

### Why Do We Use Power Query?

Suppose a company receives sales data every month.

The raw data contains:

- Duplicate records
- Blank rows
- Incorrect date formats
- Extra spaces
- Inconsistent product names
- Unnecessary columns

Cleaning this data manually every month takes time.

Power Query solves this problem by recording the cleaning steps.

### Main Features

1. Import data from multiple sources.
2. Remove duplicates.
3. Handle missing values.
4. Change data types.
5. Split and merge columns.
6. Append multiple files.
7. Merge different tables.
8. Refresh transformed data.

### Power Query Workflow

Raw Data

Excel, CSV, Text, Database

Import Data

Get Data

Clean & Transform

Remove duplicates, change types, replace values

Load Data

Excel Table or Data Model

PivotTables + Dashboard

Analytical reporting

## 7. Importing Data Using Power Query

Power Query supports data import from various sources.

### Common Data Sources

| Data Source     | Purpose                                |
| --------------- | -------------------------------------- |
| Excel Workbook  | Import Excel files                     |
| CSV File        | Import comma-separated data            |
| Text File       | Import text-based records              |
| Folder          | Combine multiple files                 |
| SQL Server      | Import database records                |
| Web             | Import data from supported web sources |
| Other Databases | Connect to supported database systems  |

### Steps to Import an Excel File

1. Open Excel.
2. Go to the Data tab.
3. Click Get Data.
4. Select From File.
5. Choose From Excel Workbook.
6. Browse and select the file.
7. Select the required sheet or table.
8. Click Transform Data.

This opens the Power Query Editor.

### Steps to Import a CSV File

1. Go to Data.
2. Click From Text/CSV.
3. Select the CSV file.
4. Check the data preview.
5. Click Transform Data.

### Steps to Import Multiple Files from a Folder

1. Go to Data.
2. Select Get Data.
3. Choose From File.
4. Select From Folder.
5. Browse the folder containing files with the same structure.
6. Click Combine and Transform.
7. Review the combined data.

Business example: Combining January, February, March, and April sales files into one master dataset.

## 8. Cleaning Data Using Power Query

Data cleaning means identifying and correcting inaccurate, incomplete, inconsistent, or duplicate information.

[Power Query For Data Preparation In Excel: An Introduction And Walk-Through For Beginners — Eval Academy](https://images.openai.com/static-rsc-4/Sts5B9cX17iw952GZ8OR9OlQ-tGIjOX2SWrq14pqZn7MuLMm2OUOzaVu1oU5O3OogF6Wr5CwLt6gj4gEmbsvuiYHzrjrnBU4ZFae4Fh3lVcLZNt7tKIg9G7edB2UWhQTja7tzpcVYbGazF7J0E3G_E2FdCIqQ5m0JLK8j6-5uxU?purpose=inline)

[evalacademy.com](https://www.evalacademy.com/articles/power-query-for-data-preparation-in-excel-an-introduction-and-walk-through-for-beginners?utm_source=chatgpt.com)

### A. Remove Duplicates

Duplicate records can affect calculations and business reporting.

Steps:

1. Select the required column or columns.
2. Go to Home.
3. Select Remove Rows.
4. Click Remove Duplicates.

M Language Syntax:

```
Table.Distinct(Source)
```

Removes duplicate rows from a table.

### B. Remove Blank Rows

Steps:

1. Open Power Query Editor.
2. Go to Home.
3. Select Remove Rows.
4. Click Remove Blank Rows.

M Language Syntax:

```
Table.SelectRows(Source, each not List.IsEmpty(List.RemoveMatchingItems(Record.FieldValues(_), {"", null})))
```

This filters out rows containing only blank or null values.

### C. Remove Extra Spaces

Sometimes data contains unnecessary spaces.

**Example:**

`"  Rahul  "` becomes `"Rahul"`.

Steps:

1. Select the column.
2. Go to Transform.
3. Select Format.
4. Click Trim.

M Language Syntax:

```
Text.Trim([Customer_Name])
```

### D. Clean Text

Removes non-printable characters.

```
Text.Clean([Customer_Name])
```

### E. Replace Values

**Example:**

Replace `Ind` with `India`.

Steps:

1. Select the column.
2. Go to Transform.
3. Click Replace Values.
4. Enter the old and new values.

M Language Syntax:

```
Table.ReplaceValue(Source, "Ind", "India", Replacer.ReplaceText, {"Country"})
```

### F. Handle Null Values

Null represents missing data.

**Example**: If the Region column contains null, replace it with "Unknown" when appropriate.

```
Table.ReplaceValue(Source, null, "Unknown", Replacer.ReplaceValue, {"Region"})
```

**Important**: Do not replace missing values blindly. Understand why the data is missing before deciding how to handle it.

### G. Change Data Types

Correct data types are important for calculations.

| Column        | Correct Data Type |
| ------------- | ----------------- |
| Order Date    | Date              |
| Sales         | Decimal Number    |
| Quantity      | Whole Number      |
| Customer Name | Text              |
| Profit        | Decimal Number    |

**Steps**:

1. Select the column.
2. Click the Data Type icon.
3. Choose the correct data type.

**M Language Syntax**:

```
Table.TransformColumnTypes(
    Source,
    {
        {"Order Date", type date},
        {"Sales", type number},
        {"Quantity", Int64.Type}
    }
)
```

## 9. Data Transformations in Power Query

Data transformation means modifying the structure or format of raw data to make it suitable for analysis.

### A. Remove Columns

Used to remove unnecessary information.

**Steps**:

1. Select the unwanted column.
2. Right-click.
3. Select Remove.

**M Syntax**:

```
Table.RemoveColumns(Source, {"Column1", "Column2"})
```

### B. Rename Columns

**Example**:

`Cust_Name` → `Customer Name`

**M Syntax**:

```
Table.RenameColumns(Source, {{"Cust_Name", "Customer Name"}})
```

### C. Split Columns

Used to divide one column into multiple columns.

**Example**:

| Full Name    |
| ------------ |
| Rahul Sharma |
| Priya Verma  |

After splitting:

| First Name | Last Name |
| ---------- | --------- |
| Rahul      | Sharma    |
| Priya      | Verma     |

**Steps**:

1. Select the Full Name column.
2. Go to Transform.
3. Click Split Column.
4. Select By Delimiter.
5. Choose Space.
6. Click OK.

**M Syntax**:

```
Table.SplitColumn(
    Source,
    "Full Name",
    Splitter.SplitTextByDelimiter(" ", QuoteStyle.Csv),
    {"First Name", "Last Name"}
)
```

### D. Merge Columns

Combines two or more columns into one.

**Example**:

First Name + Last Name = Full Name.

**Steps**:

1. Select both columns.
2. Go to Transform.
3. Click Merge Columns.
4. Select a separator.
5. Click OK.

**M Syntax**:

```
Table.CombineColumns(
    Source,
    {"First Name", "Last Name"},
    Combiner.CombineTextByDelimiter(" ", QuoteStyle.None),
    "Full Name"
)
```

### E. Add Custom Column

Used to create a new column using a formula.

**Example**:

Sales = 50,000
Cost = 35,000
Profit = 15,000

**Steps**:

1. Go to Add Column.
2. Select Custom Column.
3. Enter the column name.
4. Enter the formula.

**M Formula**:

```
[Sales] - [Cost]
```

**New column name: `Profit`**

### F. Conditional Column

Creates a new column based on conditions.

**Example**:

| Sales  | Performance |
| ------ | ----------- |
| 60,000 | High        |
| 35,000 | Medium      |
| 10,000 | Low         |

**M Formula**:

```
if [Sales] >= 50000 then "High"
else if [Sales] >= 20000 then "Medium"
else "Low"
```

### G. Group By

Used to summarize data based on categories.

**Example**:

**Raw data**:

| Region | Sales  |
| ------ | ------ |
| North  | 20,000 |
| North  | 30,000 |
| South  | 25,000 |
| South  | 15,000 |

**Grouped result**:

| Region | Total Sales |
| ------ | ----------- |
| North  | 50,000      |
| South  | 40,000      |

**Steps**:

1. Select Region.
2. Go to Home.
3. Click Group By.
4. Select Sum.
5. Select Sales.
6. Click OK.

**M Syntax**:

```
Table.Group(
    Source,
    {"Region"},
    {{"Total Sales", each List.Sum([Sales]), type number}}
)
```

### H. Append Queries

Append combines rows from multiple tables.

**Example**:

- January Sales
- February Sales
- March Sales

All three tables are combined into one table.

**M Syntax**:

```
Table.Combine({January, February, March})
```

Use case: Combining monthly sales reports.

### I. Merge Queries

Merge combines columns from two tables based on a common field.

## Example:

**Sales Table**

| Product ID | Sales  |
| ---------- | ------ |
| P101       | 50,000 |
| P102       | 30,000 |

**Product Table**

| Product ID | Product Name |
| ---------- | ------------ |
| P101       | Laptop       |
| P102       | Mobile       |

**After merging:**

| Product ID | Sales  | Product Name |
| ---------- | ------ | ------------ |
| P101       | 50,000 | Laptop       |
| P102       | 30,000 | Mobile       |

**M Syntax:**

```
Table.NestedJoin(
    Sales,
    {"Product ID"},
    Products,
    {"Product ID"},
    "Product Details",
    JoinKind.LeftOuter
)
```

Expand the nested Product Details column to display Product Name.

### Append vs Merge

| Append                                | Merge                            |
| ------------------------------------- | -------------------------------- |
| Combines rows                         | Combines columns                 |
| Tables should have similar structures | Tables need matching key columns |
| Used for monthly files                | Used to connect related datasets |
| Similar to stacking tables            | Similar to joining tables        |

## 10. Refresh Concept in Power Query

Refresh is the process of updating the Power Query output when the source data changes.

One of the biggest advantages of Power Query is that it saves the transformation steps.

You do not need to clean the data again manually every time.

[How To Refresh Data In Excel | SpreadCheaters](https://images.openai.com/static-rsc-4/wWgh-HSg8FwbEbwUwturXmzgqMDlJ6QIbXeNxpTJtLUek0WSWWlm0KZo88MW-7ArK0SFzDE6xGrKBnLaV6-W-FXrVBhqtJIUQFrfu6jQ2YVl3Zz-nkED7xtuRDuqhWYiMf881l4UhXpF4Sx97MC1aoiS4_ZbZR5nUW-OFxv3sgA?purpose=inline)

[spreadcheaters.com](https://spreadcheaters.com/how-to-refresh-data-in-excel/?utm_source=chatgpt.com)

### Example

Suppose you have a sales file containing January sales.

You import the data into Power Query and perform these steps:

1. Remove duplicates.
2. Remove blank rows.
3. Correct date formats.
4. Remove unnecessary columns.
5. Calculate profit.
6. Load the cleaned data into Excel.

Now, in February, you add new records to the source file.

Instead of repeating all the steps:

1. Update the source data.
2. Open Excel.
3. Go to Data.
4. Click Refresh All.
5. Power Query runs the saved transformation steps.
6. The output table gets updated.

### Refresh Options

| Option           | Meaning                                     |
| ---------------- | ------------------------------------------- |
| Refresh          | Refreshes the selected query or connection  |
| Refresh All      | Refreshes all relevant workbook connections |
| Query Properties | Controls refresh behavior                   |
| Refresh on Open  | Updates data when the workbook opens        |

### Important Refresh Settings

In Query Properties, you can configure:

- Refresh data when opening the file.
- Refresh every specified number of minutes.
- Enable background refresh where supported.

**Important**: Refresh updates the data using the saved steps. It does not automatically fix new errors, changed column names, or broken source paths. The source must remain accessible and compatible.

# 11. Key Takeaways

## What you should remember

1. **Dashboard**: Converts raw business data into meaningful visual insights.
2. **Dashboard Principles**: Simplicity, consistency, accuracy, visual hierarchy, and interactivity are essential.
3. **KPI Cards**: Display important metrics such as Total Sales, Profit, Orders, and Growth.
4. **Charts**: Help compare categories, identify trends, and understand performance.
5. **Interactive Reports**: PivotTables, PivotCharts, Slicers, and Timelines make reports dynamic.
6. **Power Query**: Automates data import, cleaning, transformation, and combining.
7. **Importing Data**: Power Query can connect to Excel, CSV, folders, databases, and other supported sources.
8. **Data Cleaning**: Removes duplicates, handles missing values, corrects data types, and cleans text.
9. **Transformations**: Split, merge, append, group, filter, and create custom columns.
10. **Refresh**: Reapplies saved transformation steps to updated source data.

**Most Important Workflow to Remember**

    RAW DATA
        |
IMPORT USING POWER QUERY
        |
  CLEAN & TRANSFORM
        |
  LOAD INTO EXCEL
        |
PIVOTTABLES & CHARTS
        |
INTERACTIVE DASHBOARD
        |
 BUSINESS INSIGHTS

## Final Learning Outcome

By the end of this phase, you should be able to take an unstructured raw business spreadsheet, import it into Power Query, clean and transform the data, calculate important KPIs, create PivotTables and charts, build an interactive Excel dashboard, and refresh the report whenever new data becomes available.

My recommendation: Practise this entire phase using one real-world Sales dataset. The most important skill is not just knowing formulas or creating charts; it is understanding how to convert raw data into accurate, automated, and decision-ready business insights.
