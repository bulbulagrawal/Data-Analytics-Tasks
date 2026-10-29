# Day-7 
# Lookup & Data Preparation in Excel

These are essential Excel skills for cleaning raw data, matching records, combining text, working with dates, and handling errors. They are especially useful for data analyst, MIS, reporting, and business analyst roles.

How to retrieve information from different tables, clean inconsistent data, prepare text and dates for analysis, and handle errors in Excel. These skills are essential for real-world data analyst tasks because raw data is often incomplete, inconsistent, or spread across multiple worksheets.

What is a Lookup ?
A lookup finds a value in one dataset and return related information from another column or range.

**1. Lookup Functions** :
**XLOOKUP :** Searches for a value in one range and returns a corresponding value from another range.
**Syntax:** : =XLOOKUP(lookup_value, lookup_array, return_array, [if_not_found], [match_mode], [search_mode])

**Arguments:**

>> **lookup_value:** The value you want to find.
>> **lookup_array:** The range where Excel searches.
>> **return_array:** The range containing the result.
>> **[if_not_found]:** Optional message or value if no match exists.
>> **[match_mode]:** Exact match, next smaller/larger match, or wildcard match.
>> **[search_mode]:** Search direction and method.

**Example**: Find the salary of employee ID 103.

**Employee ID     Name         Salary**
      101         Amit         25000
      102         Priya        30000
      103         Rahul        35000

**Excel :** =XLOOKUP(103,A2:A4,C2:C4,"Not Found")

**Result: 35000**
- Can search left or right.
- Uses exact match by default.
- Can display a custom message when no match is found.

**Key takeaway:** XLOOKUP is a modern, flexible lookup function. It defaults to exact matching and can return values from either side of the lookup column. It is not available in some older Excel versions.

**INDEX & MATCH :**

**INDEX**  : Index Returns a value from a specified position in a range
**Syntax** : =INDEX(return_range,MATCH(lookup_value,lookup_range,0))
**Example**: Find the salary of employee ID 103.
**Formula**: =INDEX(C2:C4,MATCH(103,A2:A4,0))
**Result: 35000**
- MATCH finds the position of the employee ID.
- INDEX returns the salary at that position.
- 0 means exact match.

**MATCH**  : Match finds the position of a lookup value 
                        or 
Definition: The MATCH function searches for a specified value in a range and returns its relative position (index number), not the actual value.

**Syntax** : =MATCH(lookup_value, lookup_array, [match_type])
**Arguments** :
- **lookup_value:** The value you want to search for.
- **lookup_array:** The range of cells where Excel searches.
- **[match_type]:** Specifies the type of match.
  --   0 - Exact match.
  --   1 - Exact match or next smallest value; data must be sorted in ascending order.
  -- (-1) - Exact match or next largest value; data must be sorted in descending order.

**Advantages:**
>> Can return values from columns to the left or right of the lookup column.
>> Works in older Excel versions.
>> Can be combined with multiple criteria using more advanced formulas.

**Key takeaway:** INDEX/MATCH is a flexible alternative to VLOOKUP and is especially useful when your lookup column is not positioned to the left of the return column.

**XLOOKUP vs. INDEX/MATCH:** XLOOKUP is generally simpler in modern Excel; INDEX/MATCH is useful for compatibility with older versions.

**2. Text Functions** : Text functions are used to extract, clean, combine, and standardize text data. They are essential when preparing raw datasets for analysis.

**2.1 LEFT** : LEFT extracts a specified number of characters from the beginning (left side) of a text string.
**Syntax** : =LEFT(text,[num_chars])

>> **text**: The text or cell reference.
>> **[num_chars]**: Number of characters to extract. Defaults to 1.

**Example**: If cell A2 contains EMP1025: 
**Synatx** : =LEFT(A2,3)
**Result** : EMP

**Common uses**:

- Extracting country codes.
- Extracting product prefixes.
- Separating the first part of an employee or transaction ID.

**Key takeaway** : Use LEFT when the required information appears at the beginning of a text string.

**2.2 RIGHT** : RIGHT extracts a specified number of characters from the end (right side) of a text string.
**Syntax** : =RIGHT(text,[num_chars])
**Example**: If A2 contains EMP1025:
**Syntax** : =RIGHT(A2,4)
**Result** : 1025

**Common uses:**

- Extracting the last four digits of an ID.
- Retrieving year or code suffixes.
- Extracting the final characters of an order number.

**Key takeaway**: Use RIGHT when the required information is located at the end of a string.

**2.3 MID** : MID extracts a specified number of characters from the middle of a text string, beginning at a position you specify.
**Syntax**: =MID(text,start_num,num_chars)

- **text** : Source text.
- **start_num** : Position of the first character to extract; the first character is position 1.
- **num_chars** : Number of characters to extract.

**Example**: If A2 contains EMP1025:
**Syntax** : =MID(A2,4,4)
**Result** : 1025

The extraction starts at character 4 and returns four characters.

**Common uses** :

- Extracting a code from the middle of an ID.
- Separating portions of fixed-format text.
- Extracting a month or year from a consistently structured code.

**Key takeaway** : MID is ideal when the required text is located at a known position inside a string.

**2.4 LEN** : LEN counts the number of characters in a text string, including spaces and punctuation.
**Syntax** : =LEN(text)
**Example**: If A2 contains Excel Data :
**Syntax** : =LEN(A2)
**Result** : 10 (The count includes the space between Excel and Data.)

**Common uses**:

- Checking ID lengths.
- Validating phone numbers stored as text.
- Identifying extra spaces or inconsistent codes.
- Supporting text extraction formulas.

**Key takeaway**: LEN counts characters, not words. Spaces and punctuation also count as characters.

**2.5 TRIM** : TRIM removes leading and trailing spaces and reduces repeated ordinary spaces between words to a single space.
**Syntax** : =TRIM(text)
**Example**: If A2 contains   Amit   Sharma  :
**Syntax** : =TRIM(A2)
**Result**: Amit Sharma

**Common uses**:

- Cleaning imported customer names.
- Standardizing text before using lookup functions.
- Removing extra spaces from manually entered data.

**Important note**: TRIM does not remove every kind of invisible space. For example, nonbreaking spaces copied from websites may require SUBSTITUTE or another cleaning step.

**Key takeaway**: TRIM is one of the most useful data-cleaning functions because unwanted spaces can cause lookup mismatches.

**2.6 CLEAN** : CLEAN removes many nonprinting characters from text, particularly certain control characters that may appear in imported data.
**Syntax** : =CLEAN(text)
**Example**: =CLEAN(A2)

This removes supported nonprinting characters from the text in A2.

**Why CLEAN matters** : Data imported from websites, text files, or other applications may contain hidden characters that are not easily visible.

These characters can cause issues with:

- Lookup formulas.
- Text comparisons.
- Data exports.
- Consistency checks.

**Common uses**:

- Cleaning data imported from external systems.
- Removing unwanted line breaks or control characters.
- Preparing text before matching or comparing records.

**Important note**: CLEAN does not remove all invisible Unicode characters or all types of whitespace. You may need to combine it with TRIM.
**Combining TRIM and CLEAN** : A useful cleaning formula is: 
**Example**: =TRIM(CLEAN(A2))

This first removes supported nonprinting characters and then trims extra ordinary spaces.

**For imported text that may contain nonbreaking spaces, try**: =TRIM(CLEAN(SUBSTITUTE(A2,CHAR(160)," ")))

Here, CHAR(160) represents a common nonbreaking space. SUBSTITUTE replaces it with a regular space before the other cleaning steps.

**Key takeaway**: CLEAN handles nonprinting characters, while TRIM handles extra ordinary spaces. They solve different problems and often work best together.
Use TRIM for excess ordinary spaces, CLEAN for supported nonprinting characters, and both together when cleaning imported data. Always inspect the cleaned results because neither function removes every possible unwanted character.

**2.7 CONCAT** : CONCAT joins text from multiple cells or ranges into a single text string without automatically inserting separators.
**Syntax** : =CONCAT(text1,[text2],...)
**Example**:

**A (First Name)**        **B (Last Name)**
  Rahul                         Sharma
  Priya	                        Patel

To combine the first and last names in row 2:

**Syntax** : =CONCAT(A2," ",B2)
**Result**: Rahul Sharma (The " " inserts a space between the two names.The space is included explicitly in the formula.)

**Another example** : =CONCAT("EMP",1045)
**Result** : EMP1045

**Common uses**:

- Combining first and last names.
- Creating unique identifiers.
- Joining text with numbers or labels.
- Combining parts of a product code.

**Key takeaway**: CONCAT joins text directly. If you need spaces, commas, or other separators, you must include them in the formula.

**2.8 TEXTJOIN** : TEXTJOIN combines multiple text values using a delimiter, such as a space, comma, hyphen, or line break. It can also ignore empty cells.
**Syntax** : =TEXTJOIN(delimiter,ignore_empty,text1,[text2],...)

- delimiter: The separator between values.
- ignore_empty: TRUE to skip empty cells; FALSE to preserve empty positions.
- text1, text2, etc.: The text or ranges to combine.

**Example**: 
  A           B	          C
Rahul	      Sharma	    Indore
Priya	      Patel	      Bhopal

**Formula**: =TEXTJOIN(", ",TRUE,A2:C2)
**Result**: Rahul, Sharma, Indore

**What happens when a cell is blank?** 
- Suppose A2 contains Rahul, B2 is blank, and C2 contains Indore.

**Another example** : =TEXTJOIN(", ",TRUE,A2:C2)
**Result** : Rahul, Indore (Because ignore_empty is TRUE, Excel skips the blank cell.)

**Common uses**:
- Combining addresses.
- Creating comma-separated lists.
- Combining names while skipping blank cells.
- Joining multiple categories or labels.

**Key takeaway**: TEXTJOIN is generally more convenient than CONCAT when you need a consistent delimiter and want to ignore blank cells.

**CONCAT versus TEXTJOIN**

**Feature	                      CONCAT	              TEXTJOIN**
Combines text	                   Yes	                   Yes
Custom delimiter	            Must insert manually	    Built-in
Can ignore empty cells	      No dedicated argument	     Yes
Best use	                    Simple combinations	      Combining lists or many cells

**Key takeaway**: Use CONCAT for simple text combinations and TEXTJOIN when you need a separator and control over empty cells.

**3. Date Functions** : Date functions help calculate durations, extract date components, build dates, and analyze time-based data.
or
Date functions help you work with dates, calculate durations, identify months and years, and prepare time-based reports.

In data analytics, dates are important for:

- Monthly sales reports.
- Employee joining-date analysis.
- Customer purchase trends.
- Invoice due-date tracking.
- Calculating order processing times.

Excel generally stores dates as serial numbers and displays them using date formats. This allows dates to be sorted and used in calculations.

**A. TODAY function** : TODAY returns the current date according to Excel's date system and recalculates when the workbook recalculates.
OR
Returns the current date according to your computer's date settings.

**Syntax** : =TODAY()
**Result** : If the current date is 28 October 2026, the result is 28-Oct-2026.
**Example**: If A2 contains a joining date:
**Formula**: =TODAY()-A2 (If A2 contains a valid past date, the formula returns the number of days between that date and today.)
This calculates the number of days between the joining date and today, assuming A2 contains a valid Excel date.

**Common uses**:

- Calculating employee tenure in days.
- Identifying overdue tasks.
- Monitoring deadlines.
- Calculating age or elapsed time with suitable formulas.

**Key takeaway**: TODAY returns the current date, not the current time. Its result can change as the date changes.

**3.2 NOW** : NOW returns the current date and time according to Excel's date system.
**Syntax** : =NOW() (The result displays the current date and time, subject to cell formatting and recalculation.)
**Example result** : 28-Oct-2026 10:55
The displayed format depends on the cell's number format. The value updates when Excel recalculates.
**Difference between TODAY and NOW**
  
  **Function	              Returns**
    TODAY()	               Current date
    NOW()	                 Current date and time

**Common uses**: 

- Recording a recalculating date-time value.
- Measuring elapsed time.
- Monitoring date-time calculations.

**Key takeaway**: NOW includes both date and time, but it is a volatile formula result, not a permanent timestamp. Use a static timestamp if you need to preserve the original entry time.

**3.3 DATE**: DATE creates a valid Excel date from year, month, and day components.

**Syntax** : =DATE(year,month,day)
**Example**: =DATE(2026,10,28)
**Result** : October 28, 2026, displayed according to the cell's date format.

Why use DATE? It is useful when year, month, and day are stored in separate columns.

A: Year	      B: Month	      C: Day
 2026	          10	            28

**Formula**: =DATE(A2,B2,C2)
**Result** : 28-Oct-2026

**Common uses**:

- Building dates from separate columns.
- Creating dates for reports.
- Avoiding ambiguous date-text formats.

**Key takeaway**: DATE constructs a real Excel date value. Excel may normalize out-of-range month or day values instead of treating them as errors.

**3.4 DAY, MONTH and YEAR** : These functions extract individual components from a valid Excel date.

**Syntax**:

=DAY(serial_number)
=MONTH(serial_number)
=YEAR(serial_number)

**Example**: If A2 contains October 28, 2026:

    Formula                       Result

    =DAY(A2)                       28
    =MONTH(A2)                     10
    =YEAR(A2)                      2026

**Common uses**:

- Grouping sales by month or year.
- Extracting reporting periods or Extracting years for annual reporting.
- Building date-based filters and summaries.
- Checking dates for business rules.

For example, a helper column containing =MONTH(A2) can help group transactions by month, although using a proper date field in a PivotTable is often preferable.

**Key takeaway** : DAY, MONTH and YEAR return numeric components. MONTH returns a number from 1 to 12, not the month name.

**3.5 DATEDIF** : DATEDIF calculates the difference between two dates in specified units, such as years, months, or days.
**Syntax**: =DATEDIF(start_date,end_date,unit)

**Common units**:

>> "Y" — complete years.
>> "M" — complete months.
>> "D" — total days.
>> "YM" — remaining months after complete years.
>> "MD" — remaining days after complete months, with some edge-case limitations.
>> "YD" — remaining days after complete years.

**Example**: If A2 contains 15-Jan-2020, and B2 contains 28-Oct-2026.
**Syntax** : =DATEDIF(A2,B2,"Y")
**Result** : 6

**Example 1** : Calculate complete months
**Syntax**    : =DATEDIF(A2,B2,"M")
**Result**    : 81

**Example 1** : Calculate total days:
**Syntax**    : =DATEDIF(A2,B2,"D")

The result is the total number of elapsed days between the dates.

**Important**: DATEDIF requires the end date to be on or after the start date. It is an older Excel function that may not appear in formula autocomplete.

**Common uses**:

- Calculating employee service periods.
- Measuring completed years of experience.
- Calculating elapsed time between dates.

**Key takeaway**: DATEDIF is useful for completed periods. Ensure the start date is not later than the end date, and use "Y" or "M" when you need completed years or months.

**3.6 EOMONTH** : EOMONTH returns the last day of a month a specified number of months before or after a starting date.

**Syntax**: =EOMONTH(start_date,months)
**Example**: =EOMONTH(DATE(2026,10,15),0)
**Result**: October 31, 2026.

**Another example**: =EOMONTH(A2,1) ( Returns the last day of the month following the date in A2.)

**Common uses**:

- Monthly sales reporting / Month-end financial reporting.
- Calculating month-end deadlines.
- Monthly sales summaries.
- Invoice schedules / Financial closing and billing schedules.

**Key takeaway**: EOMONTH is especially useful for month-end reporting because it automatically accounts for months with different lengths and leap years.

**3.7 NETWORKDAYS**: NETWORKDAYS calculates the number of working days between two dates, excluding weekends and optionally specified holidays.
**Syntax** : =NETWORKDAYS(start_date,end_date,[holidays])
**Example**: =NETWORKDAYS(A2,B2,$H$2:$H$10) ( Here, A2 is the start date, B2 is the end date, and H2:H10 contains holiday dates.)

**Example 1** : =NETWORKDAYS(A2,B2) (This returns the working days between the dates in A2 and B2, including both endpoints if they are working days.)

**To exclude holidays listed in H2:H10**: =NETWORKDAYS(A2,B2,H2:H10)

**Common uses**:

- Calculating working days for projects / Calculating business days required to process an order.
- Measuring business turnaround time / Measuring working-day delays.
- Tracking attendance or service-level agreements / Tracking employee or project timelines.

**Important**: If your business operates on different weekends, consider **NETWORKDAYS.INTL**.
**Key takeaway**: NETWORKDAYS excludes Saturdays and Sundays by default. Use NETWORKDAYS.INTL if your weekend pattern differs.

**Date function summary**

**Function	                                Main purpose**
  
  TODAY()	                                 Current date
  NOW()                                    Current date and time
  DATE()	                                 Build a date from components
  DAY()	                                   Extract day
  MONTH()	                                 Extract month number
  YEAR()	                                 Extract year
  DATEDIF()	                               Calculate date differences
  EOMONTH()	                               Find month-end date
  NETWORKDAYS()	                           Count working days

**4. Error Handling Functions** : Error-handling functions help prevent formulas from displaying confusing error messages and allow you to manage missing or invalid data more clearly.
OR
Error handling means managing formula errors so that spreadsheets remain understandable, reliable, and easier to analyze.

**Common Excel errors include**:
**Error	              Meaning	                        Common cause**
  #N/A	          Value not available	              Lookup cannot find a match
  #DIV/0!	        Division by zero	                Dividing by zero or an empty denominator
  #VALUE!	        Incorrect value type	            A formula receives an unsuitable type of value
  #REF!	          Invalid reference	                A formula references a deleted or invalid cell
  #NAME?	        Unrecognized name	                Misspelled function or undefined name
  #NUM!	          Invalid numeric value	            An invalid numeric argument or calculation
  #SPILL!	        Spill range blocked	              Dynamic-array results cannot expand into occupied cells

**4.1 IFERROR** : IFERROR returns an alternative value if a formula produces any Excel error.
**Syntax**: =IFERROR(value,value_if_error)
**Example**: =IFERROR(A2/B2,0) ( If B2 is zero and division produces #DIV/0!, the result is 0.)
**Lookup example:**: =IFERROR(INDEX(B2:B10,MATCH(E2,A2:A10,0)),"Not Found")

**Common uses**:

- Handling division errors.
- Providing fallback values for lookup formulas.
- Keeping reports readable when data is incomplete.

**Important**: IFERROR catches many types of formula errors, not just division errors. Avoid using it to hide problems that should be investigated.
**Key takeaway**: IFERROR handles many kinds of formula errors, not just missing lookups. Avoid using it to hide errors that should be investigated.

**4.2 IFNA** : IFNA handles only the #N/A error.
OR
IFNA returns a specified alternative only when a formula produces the #N/A error.
**Syntax**: =IFNA(value,value_if_na)
**Example**: =IFNA(XLOOKUP(E2,A2:A10,B2:B10),"Not Found")
If no matching value is found, the formula returns Not Found.

**Example 1** : =IFNA(XLOOKUP(E2,A2:A5,B2:B5),"Employee Not Found")

If the lookup cannot find the employee, Excel displays Employee Not Found.
Unlike IFERROR, IFNA does not suppress unrelated errors such as #REF! or #DIV/0!.

**Common uses**:

- Handling missing lookup matches.
- Displaying a clear message when an ID does not exist.
- Keeping unrelated formula errors visible.

**Key takeaway**: IFNA is often preferable for lookups because it handles missing-match errors without masking other errors, such as #REF! or #VALUE!.

**4.3 ISERROR** : ISERROR checks whether a value or formula produces an Excel error. It returns TRUE if an error occurs and FALSE otherwise.
**Syntax** : =ISERROR(value)
**Example**: =ISERROR(A2/B2)

If B2 is zero, the result is TRUE because the division produces an error.

**Common uses**:

- Testing formulas for errors.
- Creating conditional checks.
- Combining with IF to display custom messages.

**Example with IF**: =IF(ISERROR(A2/B2),"Check Data",A2/B2)
**Key takeaway** : ISERROR detects errors but does not fix them on its own. Use it with IF when you need custom error-handling logic.

**4.4 ISNA** : ISNA checks whether a value or formula returns the specific #N/A error.
**Syntax**: =ISNA(value)
**Example**: =ISNA(MATCH(E2,A2:A10,0))
Returns TRUE if MATCH cannot find the lookup value and returns #N/A.

**Common uses**:

- Checking for missing lookup values.
- Identifying unmatched records.
- Creating exception reports.

**Key takeaway** : ISNA is narrower than ISERROR. It detects only #N/A, making it useful for finding missing matches without treating every error as the same problem.

**4.5 IF** : IF tests a condition and returns one value when the condition is TRUE and another when it is FALSE.
**Syntax** : =IF(logical_test,value_if_true,value_if_false)
**Example**: =IF(B2=0,"Invalid","Valid")
If B2 is zero, the result is Invalid; otherwise, it is Valid.

**Common uses:**

- Classifying records.
- Checking for missing or invalid values.
- Applying business rules.
- Displaying custom messages.

**Key takeaway**: IF is a logical function rather than a dedicated error-handling function, but it is often used alongside ISERROR, ISNA, and IFERROR to control how formulas respond to conditions.

**5. Quick Revision Table**

**Function                     Main purpose                                                Example**

XLOOKUP                  Search and return a matching value                       =XLOOKUP(E2,A2:A10,B2:B10,"Not Found")
INDEX/MATCH              Find a position and return a corresponding value         =INDEX(B2:B10,MATCH(E2,A2:A10,0))
LEFT                     Extract characters from the beginning                    =LEFT(A2,3)
RIGHT                    Extract characters from the end                          =RIGHT(A2,4)
MID                      Extract characters from a specified position             =MID(A2,2,5)
LEN                      Count characters                                         =LEN(A2)
TRIM                     Remove extra ordinary spaces                             =TRIM(A2)
CLEAN                    Remove supported nonprinting characters                  =CLEAN(A2)
CONCAT                   Join text values                                         =CONCAT(A2," ",B2)
TEXTJOIN                 Join values using a delimiter                            =TEXTJOIN(", ",TRUE,A2:C2)
TODAY                    Return the current date                                  =TODAY()
NOW                      Return the current date and time                         =NOW()
DATE                     Construct a date                                         =DATE(2026,10,28)
DAY                      Extract the day number                                   =DAY(A2)
MONTH                    Extract the month number                                 =MONTH(A2)
YEAR                     Extract the year                                         =YEAR(A2)
DATEDIF                  Calculate date differences                               =DATEDIF(A2,B2,"Y")
EOMONTH                  Return a month-end date                                  =EOMONTH(A2,0)
NETWORKDAYS              Count working days                                       =NETWORKDAYS(A2,B2)
IFERROR                  Handle any formula error                                 =IFERROR(A2/B2,0)
IFNA                     Handle #N/A only                                         =IFNA(XLOOKUP(E2,A2:A10,B2:B10),"Not Found")
ISERROR                  Test for any error                                       =ISERROR(A2/B2)
ISNA                     Test specifically for #N/A                               =ISNA(MATCH(E2,A2:A10,0))
IF                       Apply a logical condition                                =IF(B2>=50,"Pass","Fail")

**6. Key Takeaways** :

1. Lookup: Use XLOOKUP for modern lookup tasks and INDEX/MATCH for flexible position-based lookups, including in older Excel versions.
2. Text extraction: LEFT, RIGHT, and MID extract characters from different positions; LEN counts characters.
3. Data cleaning: TRIM removes extra ordinary spaces, while CLEAN removes supported nonprinting characters. Combining them is often useful.
4. Text combination: CONCAT joins text directly; TEXTJOIN adds a delimiter and can ignore blank cells.
5. Date preparation: TODAY and NOW return dynamic current date/time values, DATE constructs dates, and DATEDIF calculates elapsed eriods.
6. Reporting dates: EOMONTH supports month-end calculations, while NETWORKDAYS calculates working days.
7. Error handling: IFERROR handles broad error types, IFNA focuses on missing-match errors, and ISERROR/ISNA test for errors.
8. Data quality: Clean and standardize source data before performing lookups. This helps reduce mismatches caused by spaces, hidden          characters, and inconsistent formats.

**Practical recommendation**: For Excel data analyst work, prioritize XLOOKUP, INDEX/MATCH, TRIM, CLEAN, LEFT/RIGHT/MID, TEXTJOIN, date functions, and IFERROR/IFNA. These functions cover many common data preparation and reporting tasks.
