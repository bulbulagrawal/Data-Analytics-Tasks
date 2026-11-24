# **PHASE 5 — PYTHON FOUNDATIONS (Days 19–21)**

## **Day 19 — Python Basics for Analytics**

**Objective:** Understand Python fundamentals and learn how to write basic Python programs for data analytics. By the end of this day, you should be able to create variables, work with different data types, perform calculations, manipulate strings, and use Python's built-in data structures.

## **1. Python Environment**

### **Definition**

A Python environment is the setup required to write, execute, and manage Python programs.

Python is a high-level, interpreted programming language widely used in:

- Data Analytics
- Data Science
- Machine Learning
- Automation
- Data Visualization
- Artificial Intelligence

### **Popular Python environments**

[Part II: AI — Chapter 3.1: Familiarisation with Python | Solutions for Class 9 ICSE Exploring Robotics & Artificial Intelligence | KnowledgeBoat](https://images.openai.com/static-rsc-4/-e04Bxey6vqUTFrO88fANCW1nPXeVIFiPNJeo6Kw8yPQZ8Q41SilqpodpSdyFJhWy2EVXNyL1Xn_4x8Hnn34Rk2Hv8hJgvDJ1ojmNcpBGJ90THGWn9ocNm2NADt_jIt0C2obkoNJmYls0vCArCmkfyXoXKalMJnhwArBGP-BUV8?purpose=inline)

**Python**

The programming language used to write and execute instructions.

Website: [python.org](https://www.python.org/?utm_source=chatgpt.com)

[Jupyter PNG Logo — Download Free Transparent Logo](https://images.openai.com/static-rsc-4/EhcZB4ZOJ5P1Jy8ABr9Ft2CP6wyQF_h54vDoM4r1ErKhwu2kocgCCjaha0TjPH0f0g3LEmTBPOWP0-ry8w4CILRzhYmkxa0K_3wRmM2GTILbRmF7FKc9YPfhQCcRKxvTc7aSGvl5kdN8fj2GxXTZpQWRhUmesNW3t7qbsSlYsng?purpose=inline)

**Jupyter Notebook**

An interactive environment where you can write code, execute it cell by cell, and display results.

Website: [jupyter.org](https://jupyter.org/?utm_source=chatgpt.com)

[File:Visual Studio Code 1.35 icon.svg - Wikimedia Commons](https://images.openai.com/static-rsc-4/bwltRsn8xFpdSRcYQ3DdHauINNG_Ll8uEuWak3gU_Cd8IQKU8JMwJXvDy7WOSMXzw_LreGtysSFaVMfFopIshhFxhhA7optqpzdDNA41Fr3DZ8RT6oELKwe8M8zFoIi4_H68G4UOg124XH5x4eObz-mHD-E9xY_6m_hLlZ275hc?purpose=inline)

**Visual Studio Code**

A code editor used to write, debug, and manage Python programs.

Website: [Download VS Code](https://code.visualstudio.com/?utm_source=chatgpt.com)

### **Installing Python**

1. Visit python.org.
2. Download the latest stable Python version.
3. Run the installer.
4. Select **Add Python to PATH**.
5. Complete installation.

Verify installation using CMD:

```
python --version
```

Check pip:

```
pip --version
```

Install Jupyter Notebook:

```
pip install notebook
```

Launch Jupyter:

```
jupyter notebook
```

**Remember:** Python is the programming language; Jupyter Notebook is an environment in which you can write and execute Python code.

**Business Example:** A data analyst installs Python and Jupyter Notebook to analyze monthly sales data and generate business reports.

## **2. Jupyter Notebook**

### **Definition**

Jupyter Notebook is an interactive web-based development environment that allows users to write and execute Python code in separate cells.

It is especially useful for data analysts because it supports:

- Writing Python code.
- Executing code step by step.
- Displaying tables and charts.
- Adding explanations using Markdown.
- Performing data analysis.

### **Important Jupyter components**

| Component     | Description                            |
| ------------- | -------------------------------------- |
| Code Cell     | Used to write and execute Python code  |
| Markdown Cell | Used to write headings and notes       |
| Kernel        | Executes Python code                   |
| Output        | Displays execution results             |
| Notebook      | File containing code, output and notes |

### **Example**

```
# Calculate total salessales = 5000expenses = 2000profit = sales - expensesprint(profit)
```

**Output:**

```
3000
```

### **Useful keyboard shortcuts**

| Shortcut      | Function                         |
| ------------- | -------------------------------- |
| Shift + Enter | Run cell and move to next        |
| Ctrl + Enter  | Run current cell                 |
| A             | Insert cell above (command mode) |
| B             | Insert cell below (command mode) |
| M             | Convert cell to Markdown         |
| Y             | Convert cell to Code             |
| DD            | Delete selected cell             |

**Remember:** Jupyter Notebook is widely used for experimenting with data and documenting analytical results.

**Business Example:** An analyst uses Jupyter to calculate monthly revenue, visualize sales trends, and explain findings in the same notebook.

## **3. Variables**

### **Definition**

A variable is a named storage location used to store data in a Python program.

Variables allow us to store information and reuse it whenever required.

### **Syntax**

```
variable_name = value
```

### **Example**

```
company = "ABC Electronics"sales = 50000expenses = 20000profit = sales - expensesprint(company)print(sales)print(expenses)print(profit)
```

**Output:**

```
ABC Electronics
50000
20000
30000
```

### **Rules for naming variables**

1. A variable name must start with a letter or underscore.
2. It cannot start with a number.
3. Spaces are not allowed.
4. Variable names are case-sensitive.
5. Python keywords cannot be used as variable names.

**Valid variable names:**

```
sales = 5000total_sales = 10000_sales = 2000sales2026 = 15000
```

**Invalid variable names:**

```
2sales = 5000total sales = 10000class = "Python"
```

### **Multiple variable assignment**

```
sales, expenses, profit = 50000, 20000, 30000print(sales)print(expenses)print(profit)
```

### **Checking variable type**

```
sales = 50000print(type(sales))
```

Output:

```
<class 'int'>
```

**Remember:** Python does not require you to declare a variable's data type explicitly. It determines the type automatically.

**Business Example:** An e-commerce company stores total sales, customer count, product quantity, and profit in separate variables.

## **4. Data Types**

### **Definition**

Data types define the kind of value stored in a variable.

Python provides several built-in data types.

### **Main Python data types**

\| Data Type | Description | Example |\
\|---|---|---|\
\| int | Whole numbers | 100 |\
\| float | Decimal numbers | 99.50 |\
\| str | Text | "Python" |\
\| bool | True or False | True |\
\| list | Ordered, changeable collection | [10, 20, 30] |\
\| tuple | Ordered, unchangeable collection | (10, 20, 30) |\
\| dict | Key-value pairs |
