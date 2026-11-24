# **PHASE 5 — PYTHON FOUNDATIONS (Days 19–21)**

# **Day 19 — Python Basics for Analytics**

**Objective:** Understand Python fundamentals and learn how to write Python programs for data analytics. By the end of this day, you should be able to work with variables, data types, operators, strings, and Python collections such as lists, tuples, dictionaries, and sets.

## **1. Python Introduction**

### **What is Python?**

Python is a high-level, interpreted, general-purpose programming language known for its simple syntax and readability.

It is widely used in:

- Data Analytics
- Data Science
- Machine Learning
- Artificial Intelligence
- Web Development
- Automation
- Data Visualization

**Example:**

```
print("Hello, Data Analytics!")
```

Output:

```
Hello, Data Analytics!
```

### **Why is Python important for Data Analysts?**

Python helps analysts:

- Process large amounts of data.
- Clean and transform raw datasets.
- Perform statistical calculations.
- Automate repetitive tasks.
- Create charts and visualizations.
- Build predictive models.

**Popular Python libraries for Data Analytics:**

| Library      | Purpose                        |
| ------------ | ------------------------------ |
| NumPy        | Numerical calculations         |
| Pandas       | Data manipulation and analysis |
| Matplotlib   | Data visualization             |
| Seaborn      | Statistical visualization      |
| Scikit-learn | Machine learning               |

**Remember:** Python is the programming language, while Pandas, NumPy, and Matplotlib are libraries that provide additional functionality.

## **2. Python Environment**

### **What is a Python Environment?**

A Python environment is the setup required to write, execute, and manage Python programs.

It generally includes:

- Python interpreter
- Code editor or IDE
- Required libraries
- Package management tools

### **Popular Python environments**

[Make Python IDLE's icon simpler - Ideas - Discussions on Python.org](https://images.openai.com/static-rsc-4/VZGZrR_2EqmEIOviE3aiv4snf5___1678eMm7ALdeX-s-DWFkKMIWrqH-cjgnZpwcDsX1U15vBrJsngQulFq9LSKijgiNk-YFnoeUcVYP0S3kRQmIfO1kFPYlufwhmTylwG8VyUkqIpWNkY7g3Yi8E7F37nSXhDQLPHqUlWTnYE?purpose=inline)

**1. Python IDLE**

Basic development environment installed with Python. Suitable for beginners.

[Jupyter PNG Logo — Download Free Transparent Logo](https://images.openai.com/static-rsc-4/EhcZB4ZOJ5P1Jy8ABr9Ft2CP6wyQF_h54vDoM4r1ErKhwu2kocgCCjaha0TjPH0f0g3LEmTBPOWP0-ry8w4CILRzhYmkxa0K_3wRmM2GTILbRmF7FKc9YPfhQCcRKxvTc7aSGvl5kdN8fj2GxXTZpQWRhUmesNW3t7qbsSlYsng?purpose=inline)

**2. Jupyter Notebook**

Allows you to write and execute Python code in separate cells. Very useful for data analytics.

[File:Visual Studio Code 1.35 icon.svg - Wikimedia Commons](https://images.openai.com/static-rsc-4/bwltRsn8xFpdSRcYQ3DdHauINNG_Ll8uEuWak3gU_Cd8IQKU8JMwJXvDy7WOSMXzw_LreGtysSFaVMfFopIshhFxhhA7optqpzdDNA41Fr3DZ8RT6oELKwe8M8zFoIi4_H68G4UOg124XH5x4eObz-mHD-E9xY_6m_hLlZ275hc?purpose=inline)

**3. Visual Studio Code**

A code editor that supports Python development through extensions.

[File:Google Colaboratory SVG Logo.svg - Wikimedia Commons](https://images.openai.com/static-rsc-4/Vva6xZfcPdjvmM5Y2whHAYqkrhLfkY1DBFPaZ6osRiXnciHTCr2RgsqjlRzyLSB2jnJMRMKSL-qrxSYunjYJ9ND4ZlhbVzT3pyhhvGmKe8Ga46rP7tRKVqSQOl8YYNBfIOVrTyOYEhNE8oSmOaf6QfcgmOs4LR6pf9TDMke4rhU?purpose=inline)

**4. Google Colab**

A cloud-based Python notebook environment that runs in a browser.

### **Installing Python**

1. Visit [Python Official Website](https://www.python.org/downloads/?utm_source=chatgpt.com).
2. Download the latest stable Python version.
3. Run the installer.
4. Select **Add Python to PATH** during installation.
5. Complete installation.

Verify installation using CMD:

```
python --version
```

To install a library:

```
pip install pandas
```

**Remember:**

- Python executes your code.
- pip installs additional Python packages.
- Libraries provide reusable functions and tools.

**Business Example:** A company installs Python and Pandas to automate monthly sales reports instead of manually calculating sales in Excel.

## **3. Jupyter Notebook**

### **What is Jupyter Notebook?**

Jupyter Notebook is an interactive development environment where you can write Python code, execute it, display results, and document your analysis in one place.

It is particularly useful for data analysts because it allows code, output, explanations, and visualizations to be combined.

[GSB 544: Data Science and Machine Learning with Python - 1  Intro and Setup](https://images.openai.com/static-rsc-4/6OaJgmnrOIBHeRAvJDh2B90F_pcFL0yhBTx9eF_6F5G1jQx4qcqz3MaO4hBIe0KzYjTinVEZtc2nNojnGC82sPyOMhgBk4evncKwpQeeh55MtlgNoICiF-db0YHuP14u5Uh-EmEXa0avsGDZQWHmSeaZYtB00JzjppKzQ6P6QgU?purpose=inline)

[ds-ml-with-python.github.io](https://ds-ml-with-python.github.io/Course-Textbook/00-setup.html?utm_source=chatgpt.com)

### **Important features**

1. Code Cells – Write and execute Python code.
2. Markdown Cells – Write headings, explanations, and notes.
3. Output Cells – Display results.
4. Visualization – Display graphs and charts.
5. Interactive Execution – Execute individual cells.

### **Installing Jupyter Notebook**

```
pip install notebook
```

Launch Jupyter Notebook:

```
jupyter notebook
```

### **Example**

```
sales = 50000expenses = 20000profit = sales - expensesprint(profit)
```

Output:

```
30000
```

### **Important keyboard shortcuts**

| Shortcut      | Function                         |
| ------------- | -------------------------------- |
| Shift + Enter | Run current cell                 |
| Ctrl + Enter  | Run cell without moving          |
| A             | Insert cell above (command mode) |
| B             | Insert cell below (command mode) |
| M             | Convert cell to Markdown         |
| Y             | Convert cell to Code             |
| DD            | Delete selected cell             |

**Business Application:** A sales analyst can use Jupyter Notebook to calculate revenue, analyze customer purchases, and generate charts in a single document.

**Remember:** Jupyter Notebook is widely used for exploratory data analysis (EDA).

## **4. Variables**

### **What is a Variable?**

A variable is a named storage location used to store data in a program.

In Python, you do not need to declare the data type explicitly. Python automatically determines the type based on the assigned value.

### **Syntax**

```
variable_name = value
```

### **Examples**

```
name = "Rahul"age = 25salary = 45000is_employee = Trueprint(name)print(age)print(salary)print(is_employee)
```

Output:

```
Rahul
25
45000
True
```

### **Multiple variable assignments**

```
a, b, c = 10, 20, 30print(a)print(b)print(c)
```

Output:

```
10
20
30
```

### **Variable naming rules**

| Rule                                   | Example                             |
| -------------------------------------- | ----------------------------------- |
| Must start with a letter or underscore | `name`, `_salary`                   |
| Cannot start with a number             | `1name` (Invalid)                   |
| Cannot contain spaces                  | `employee_name`                     |
| Cannot use Python keywords             | `class` (Invalid)                   |
| Case-sensitive                         | `Salary` and `salary` are different |

### **Business Example**

```
total_sales = 150000total_expenses = 90000profit = total_sales - total_expensesprint("Total Profit:", profit)
```

Output:

```
Total Profit: 60000
```

**Business Application:** Variables store sales, revenue, expenses, profit, customer counts, and other business metrics.

**Remember:** Use meaningful variable names to make your code readable.

## **5. Data Types**

### **What are Data Types?**

Data types define the type of value stored in a variable.

Python has several built-in data types.

### **Important Python data types**

| Data Type | Description                   | Example             |
| --------- | ----------------------------- | ------------------- |
| int       | Integer numbers               | `100`               |
| float     | Decimal numbers               | `99.50`             |
| str       | Text                          | `"Python"`          |
| bool      | True or False                 | `True`              |
| list      | Ordered, mutable collection   | `[10, 20, 30]`      |
| tuple     | Ordered, immutable collection | `(10, 20, 30)`      |
| dict      | Key-value pairs               | `{"name": "Rahul"}` |
| set       | Unique elements               | `{10, 20, 30}`      |

### **Example**

```
employee_name = "Rahul"employee_age = 25employee_salary = 45000.50is_active = Trueprint(type(employee_name))print(type(employee_age))print(type(employee_salary))print(type(is_active))
```

Output:

```
<class 'str'>
<class 'int'>
<class 'float'>
<class 'bool'>
```

### **Type Conversion**

Type conversion means changing one data type into another.

**Syntax:**

```
int()float()str()bool()
```

Example:

```
price = "500"new_price = int(price)print(new_price)print(type(new_price))
```

Output:

```
500
<class 'int'>
```

Another example:

```
quantity = 5price = 100.50total = quantity * priceprint(total)
```

Output:

```
502.5
```

**Business Application:** Data analysts frequently convert text-based numerical values into integers or floats before performing calculations.

**Remember:** Use `type()` to identify the data type of a variable.

## **6. Operators**

### **What are Operators?**

Operators are special symbols used to perform calculations, comparisons, and logical operations.

Python supports several categories of operators.

### **A. Arithmetic Operators**

Used for mathematical calculations.

| Operator | Meaning        | Example   | Result |
| -------- | -------------- | --------- | ------ |
| `+`      | Addition       | `10 + 5`  | 15     |
| `-`      | Subtraction    | `10 - 5`  | 5      |
| `*`      | Multiplication | `10 * 5`  | 50     |
| `/`      | Division       | `10 / 5`  | 2.0    |
| `//`     | Floor division | `10 // 3` | 3      |
| `%`      | Modulus        | `10 % 3`  | 1      |
| `**`     | Exponent       | `2 ** 3`  | 8      |

Example:

```
sales = 100000expenses = 65000profit = sales - expensesprint("Profit:", profit)
```

Output:

```
Profit: 35000
```

### **B. Comparison Operators**

Used to compare two values. They return either `True` or `False`.

| Operator | Meaning               | Example    |
| -------- | --------------------- | ---------- |
| `==`     | Equal to              | `10 == 10` |
| `!=`     | Not equal to          | `10 != 5`  |
| `>`      | Greater than          | `10 > 5`   |
| `<`      | Less than             | `5 < 10`   |
| `>=`     | Greater than or equal | `10 >= 10` |
| `<=`     | Less than or equal    | `5 <= 10`  |

Example:

```
sales = 50000target = 40000print(sales > target)
```

Output:

```
True
```

### **C. Logical Operators**

Used to combine multiple conditions.

| Operator | Meaning                                |
| -------- | -------------------------------------- |
| `and`    | True if both conditions are true       |
| `or`     | True if at least one condition is true |
| `not`    | Reverses the result                    |

Example:

```
sales = 60000target = 50000print(sales >= target and target > 0)
```

Output:

```
True
```

### **D. Assignment Operators**

Used to assign or update variable values.

| Operator | Example  | Equivalent  |
| -------- | -------- | ----------- |
| `=`      | `x = 10` | Assign 10   |
| `+=`     | `x += 5` | `x = x + 5` |
| `-=`     | `x -= 5` | `x = x - 5` |
| `*=`     | `x *= 2` | `x = x * 2` |
| `/=`     | `x /= 2` | `x = x / 2` |

Example:

```
sales = 10000sales += 5000print(sales)
```

Output:

```
15000
```

**Business Application:** Operators help analysts calculate profit, growth percentages, target achievement, and business performance.

**Remember:** Arithmetic operators calculate values, comparison operators compare values, and logical operators combine conditions.

## **7. Strings**

### **What is a String?**

A string is a sequence of characters enclosed within single quotes, double quotes, or triple quotes.

Strings are used to store text information.

Examples:

```
name = "Rahul"company = 'ABC Technologies'message = """Welcome to Python"""
```

### **String Operations**

**A. Concatenation**

Joining two or more strings.

```
first_name = "Rahul"last_name = "Sharma"full_name = first_name + " " + last_nameprint(full_name)
```

Output:

```
Rahul Sharma
```

**B. String Indexing**

Accessing individual characters using their positions.

```
name = "PYTHON"print(name[0])print(name[1])print(name[-1])
```

Output:

```
P
Y
N
```

**C. String Slicing**

Extracting a portion of a string.

Syntax:

```
string[start:end]
```

Example:

```
name = "PYTHON"print(name[0:3])
```

Output:

```
PYT
```

**D. Important String Methods**

| Method      | Purpose                       | Example                    |
| ----------- | ----------------------------- | -------------------------- |
| `upper()`   | Convert to uppercase          | `"hello".upper()`          |
| `lower()`   | Convert to lowercase          | `"HELLO".lower()`          |
| `title()`   | Capitalize each word          | `"rahul sharma".title()`   |
| `strip()`   | Remove surrounding whitespace | `" Hello ".strip()`        |
| `replace()` | Replace text                  | `"Hello".replace("H","Y")` |
| `split()`   | Split into a list             | `"A,B,C".split(",")`       |
| `find()`    | Find substring position       | `"Python".find("t")`       |
| `count()`   | Count occurrences             | `"banana".count("a")`      |

### **Practical Example**

```
customer_name = "  rahul sharma  "clean_name = customer_name.strip().title()print(clean_name)
```

Output:

```
Rahul Sharma
```

**Business Application:** Data analysts use string methods to clean customer names, standardize product names, and remove unwanted spaces from datasets.

**Remember:** Strings are immutable, meaning their original characters cannot be changed directly. String methods return new strings.

## **8. Lists**

### **What is a List?**

A list is an ordered collection of elements that can store multiple values in a single variable.

Lists are:

- Ordered
- Mutable (changeable)
- Allow duplicate values
- Allow different data types

### **Syntax**

```
list_name = [value1, value2, value3]
```

### **Example**

```
sales = [10000, 15000, 20000, 25000]print(sales)
```

Output:

```
[10000, 15000, 20000, 25000]
```

### **Accessing List Elements**

```
products = ["Laptop", "Mobile", "Tablet"]print(products[0])print(products[1])
```

Output:

```
Laptop
Mobile
```

### **Important List Methods**

| Method      | Purpose                               |
| ----------- | ------------------------------------- |
| `append()`  | Add an element at the end             |
| `insert()`  | Add an element at a specific position |
| `remove()`  | Remove a specific element             |
| `pop()`     | Remove an element by position         |
| `sort()`    | Sort elements                         |
| `reverse()` | Reverse the list                      |
| `len()`     | Count elements                        |

### **Example**

```
sales = [10000, 20000, 15000]sales.append(25000)print(sales)sales.remove(15000)print(sales)
```

Output:

```
[10000, 20000, 15000, 25000]
[10000, 20000, 25000]
```

### **Practical Business Example**

```
monthly_sales = [50000, 60000, 75000, 90000]total_sales = sum(monthly_sales)average_sales = total_sales / len(monthly_sales)print("Total Sales:", total_sales)print("Average Sales:", average_sales)
```

Output:

```
Total Sales: 275000
Average Sales: 68750.0
```

**Business Application:** Lists can store monthly sales, product prices, customer IDs, and employee salaries.

**Remember:** Lists use square brackets `[]` and can be modified after creation.

## **9. Tuples**

### **What is a Tuple?**

A tuple is an ordered collection of elements that cannot be modified after creation.

Tuples are:

- Ordered
- Immutable
- Allow duplicate values
- Allow different data types

### **Syntax**

```
tuple_name = (value1, value2, value3)
```

### **Example**

```
employee = ("Rahul", 25, "Data Analyst")print(employee)
```

Output:

```
('Rahul', 25, 'Data Analyst')
```

### **Accessing Tuple Elements**

```
employee = ("Rahul", 25, "Data Analyst")print(employee[0])print(employee[1])
```

Output:

```
Rahul
25
```

### **Important Tuple Methods**

| Method    | Purpose                         |
| --------- | ------------------------------- |
| `count()` | Count occurrences of an element |
| `index()` | Find the position of an element |

Example:

```
numbers = (10, 20, 30, 20, 40)print(numbers.count(20))print(numbers.index(30))
```

Output:

```
2
2
```

### **List vs Tuple**

| Feature      | List     | Tuple        |
| ------------ | -------- | ------------ |
| Syntax       | `[]`     | `()`         |
| Ordered      | Yes      | Yes          |
| Mutable      | Yes      | No           |
| Duplicates   | Allowed  | Allowed      |
| Modification | Possible | Not possible |

**Business Application:** Tuples are useful for storing fixed information, such as company coordinates, fixed configuration values, or predefined category codes.

**Remember:** Use a tuple when the collection should remain unchanged.

## **10. Dictionaries**

### **What is a Dictionary?**

A dictionary is a collection of data stored in key-value pairs.

Each value is accessed using its corresponding key.

Dictionaries are:

- Ordered (insertion order is preserved)
- Mutable
- Key-value based
- Require unique keys
- Allow different data types as values

### **Syntax**

```
dictionary_name = {    "key1": "value1",    "key2": "value2"}
```

### **Example**

```
employee = {    "name": "Rahul",    "age": 25,    "salary": 45000,    "department": "Analytics"}print(employee)
```

Output:

```
{'name': 'Rahul', 'age': 25, 'salary': 45000, 'department': 'Analytics'}
```

### **Accessing Values**

```
print(employee["name"])print(employee["salary"])
```

Output:

```
Rahul
45000
```

### **Important Dictionary Methods**

| Method     | Purpose                  |
| ---------- | ------------------------ |
| `keys()`   | Returns all keys         |
| `values()` | Returns all values       |
| `items()`  | Returns key-value pairs  |
| `get()`    | Retrieves a value safely |
| `update()` | Updates dictionary       |
| `pop()`    | Removes a key-value pair |

### **Practical Example**

```
employee = {    "name": "Rahul",    "salary": 45000}employee["department"] = "Analytics"employee["salary"] = 50000print(employee)
```

Output:

```
{'name': 'Rahul', 'salary': 50000, 'department': 'Analytics'}
```

### **Using get()**

```
print(employee.get("name"))print(employee.get("age", "Not Available"))
```

Output:

```
Rahul
Not Available
```

**Business Application:** Dictionaries are useful for representing employee records, product information, customer details, and business configurations.

**Remember:** Dictionaries use curly brackets `{}` and store information as key-value pairs.

## **11. Sets**

### **What is a Set?**

A set is an unordered collection of unique elements.

Sets are:

- Unordered
- Mutable
- Do not allow duplicate elements
- Do not support indexing

### **Syntax**

```
set_name = {value1, value2, value3}
```

### **Example**

```
numbers = {10, 20, 30, 20, 10}print(numbers)
```

Output (order may vary):

```
{10, 20, 30}
```

Notice that duplicate values are automatically removed.

### **Important Set Methods**

| Method           | Purpose                                       |
| ---------------- | --------------------------------------------- |
| `add()`          | Add an element                                |
| `remove()`       | Remove an element (raises an error if absent) |
| `discard()`      | Remove an element (no error if absent)        |
| `union()`        | Combine two sets                              |
| `intersection()` | Find common elements                          |
| `difference()`   | Find elements present only in the first set   |

### **Example 1 — Removing Duplicates**

```
customer_ids = [101, 102, 103, 101, 102]unique_customers = set(customer_ids)print(unique_customers)
```

Output (order may vary):

```
{101, 102, 103}
```

### **Example 2 — Union**

```
A = {1, 2, 3}B = {3, 4, 5}print(A.union(B))
```

Output:

```
{1, 2, 3, 4, 5}
```

### **Example 3 — Intersection**

```
A = {1, 2, 3}B = {3, 4, 5}print(A.intersection(B))
```

Output:

```
{3}
```

### **Example 4 — Difference**

```
A = {1, 2, 3}B = {3, 4, 5}print(A.difference(B))
```

Output:

```
{1, 2}
```

**Business Application:** Sets help identify unique customers, remove duplicate records, and compare customer lists from different months.

**Remember:** Use sets when you need unique values without duplicates.

# **12. Comparison of Python Data Structures**

This is one of the most important concepts to remember for data analytics interviews and practical work.

| Feature      | List              | Tuple             | Dictionary     | Set           |
| ------------ | ----------------- | ----------------- | -------------- | ------------- |
| Syntax       | `[]`              | `()`              | `{key:value}`  | `{}`          |
| Ordered      | Yes               | Yes               | Yes\*          | No            |
| Mutable      | Yes               | No                | Yes            | Yes           |
| Duplicates   | Yes               | Yes               | Keys: No       | No            |
| Indexing     | Yes               | Yes               | By key         | No            |
| Main purpose | Store collections | Fixed collections | Key-value data | Unique values |

\*Python dictionaries preserve insertion order (Python 3.7+).

**Quick examples:**

```
# Listsales = [100, 200, 300]# Tuplemonths = ("Jan", "Feb", "Mar")# Dictionaryemployee = {"name": "Rahul", "age": 25}# Setunique_ids = {101, 102, 103}
```

# **13. Practical Business Project — Monthly Sales Analysis**

**Scenario:** You are working as a Data Analyst at an e-commerce company. Your manager wants you to analyze the sales of five products.

### **Dataset**

| Product  | Sales (₹) |
| -------- | --------- |
| Laptop   | 50000     |
| Mobile   | 30000     |
| Tablet   | 20000     |
| Keyboard | 10000     |
| Mouse    | 5000      |

### **Python Program**

```
# Product informationproducts = ["Laptop", "Mobile", "Tablet",            "Keyboard", "Mouse"]# Sales informationsales = [50000, 30000, 20000, 10000, 5000]# Total salestotal_sales = sum(sales)# Average salesaverage_sales = total_sales / len(sales)# Highest saleshighest_sales = max(sales)# Lowest saleslowest_sales = min(sales)# Dictionaryreport = {    "Total Sales": total_sales,    "Average Sales": average_sales,    "Highest Sales": highest_sales,    "Lowest Sales": lowest_sales}# Display reportprint(report)
```

### **Expected Output**

```
{
'Total Sales': 115000,
'Average Sales': 23000.0,
'Highest Sales': 50000,
'Lowest Sales': 5000
}
```

### **Business Insights**

1. Total revenue from five products is ₹1,15,000.
2. Average product sales are ₹23,000.
3. Laptop generated the highest sales.
4. Mouse generated the lowest sales.

**Business Application:** This is a basic example of how Python can calculate important business metrics before moving to advanced analysis using Pandas and NumPy.

# **14. Best Practices for Python Beginners**

1. Use meaningful variable names such as `total_sales` instead of `x`.
2. Follow consistent indentation.
3. Use comments to explain complex code.
4. Avoid unnecessary variables.
5. Use appropriate data structures.
6. Keep code simple and readable.
7. Test your code with different values.
8. Use Jupyter Notebook for experimentation and analysis.

Example of comments:

```
# Calculate total monthly revenuesales = [10000, 20000, 30000]total_sales = sum(sales)print(total_sales)
```

# **15. Practice Tasks — Day 19**

Try completing these exercises yourself.

**Your practice checklist**

0/8 completed

**Task 1**\
Create five variables: employee name, age, salary, department, and employment status.

Variables and data types

**Task 2**\
Calculate total sales, expenses, and profit using arithmetic operators.

Arithmetic operators

**Task 3**\
Convert the string '2500' into an integer and add 500.

Type conversion

**Task 4**\
Create a list of five products and add one more product using append().

Lists

**Task 5**\
Create a tuple containing three months and access the second month.

Tuples

**Task 6**\
Create an employee dictionary containing name, age, salary, and department. Update the salary.

Dictionaries

**Task 7**\
Given customer IDs [101, 102, 101, 103, 102, 104], remove duplicates using a set.

Sets

**Task 8**\
Create a sales list and calculate total, average, maximum, and minimum sales.

Business analysis

Reset checklist

# **16. Quick Revision — Day 19**

| Topic            | Key Takeaway                                |
| ---------------- | ------------------------------------------- |
| Python           | Programming language used for analytics     |
| Environment      | Setup for writing and running Python        |
| Jupyter Notebook | Interactive coding and analysis environment |
| Variables        | Store data values                           |
| Data Types       | Define the type of data                     |
| Operators        | Perform calculations and comparisons        |
| Strings          | Store and manipulate text                   |
| Lists            | Store multiple changeable values            |
| Tuples           | Store multiple unchangeable values          |
| Dictionaries     | Store key-value pairs                       |
| Sets             | Store unique values                         |

## **Key Takeaways**

**What you should understand after Day 19:**

- Understand Python fundamentals and its importance in Data Analytics.
- Set up Python and Jupyter Notebook.
- Create variables and identify data types.
- Perform mathematical and logical operations.
- Manipulate text using string methods.
- Work with lists, tuples, dictionaries, and sets.
- Perform basic business calculations using Python.

Day 19 Learning Outcome

You can now write basic Python programs and use Python data structures to store, organize, and analyze simple business information.
