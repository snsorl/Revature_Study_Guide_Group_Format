### Pandas

# Why NumPy and Pandas?

```python
marks = [70, 80, 90, 60, 85]
```

Suppose we want to add 5 marks to every student.

With a Python list:

```python
marks = [70, 80, 90, 60, 85]

new_marks = []

for mark in marks:
    new_marks.append(mark + 5)

print(new_marks)
```

Output:

```text
[75, 85, 95, 65, 90]
```

This works.

But when we work with thousands or millions of numerical values, specialized numerical tools become extremely useful.

NumPy provides:

- Efficient numerical arrays
- Vectorized operations
- Mathematical functions
- Multidimensional arrays
- Tools for numerical computation

Pandas builds on ideas from NumPy and provides convenient tools for:

- Tables
- Rows and columns
- Data cleaning
- Filtering
- Grouping
- CSV/Excel-style data
- Data analysis

A useful distinction:

```text
NumPy : Numerical data and arrays

Pandas : Structured/tabular data
```

---

# Installing NumPy and Pandas

Open the VS Code terminal.

Install:

```bash
python -m pip install numpy pandas
```

Verify NumPy:

```bash
python -c "import numpy; print(numpy.__version__)"
```

Verify Pandas:

```bash
python -c "import pandas; print(pandas.__version__)"
```

Another option is:

```bash
pip install numpy pandas
```

---

# Importing NumPy

The conventional import is:

```python
import numpy as np
```

```text
numpy : actual library name
np    : conventional alias
```

This is similar to:

```python
import calculator as calc
```

from the previous modules lesson.

---

# First NumPy Array

```python
import numpy as np

numbers = np.array([10, 20, 30, 40, 50])

print(numbers)
```

Output:

```text
[10 20 30 40 50]
```

> `np.array()` creates a NumPy array.

---

# NumPy Array vs Python List

Python list:

```python
numbers = [10, 20, 30, 40]
```

NumPy array:

```python
numbers = np.array([10, 20, 30, 40])
```

Both can store multiple values.

But NumPy arrays are designed specifically for numerical computing.

---

# Why NumPy Operations Are Convenient

Python list:

```python
numbers = [10, 20, 30]

print(numbers * 2)
```

Output:

```text
[10, 20, 30, 10, 20, 30]
```

This does **not** multiply every number by 2.

With NumPy:

```python
import numpy as np

numbers = np.array([10, 20, 30])

print(numbers * 2)
```

Output:

```text
[20 40 60]
```

Explain:

> NumPy lets us express operations on entire arrays naturally.

---

# Vectorization

> Vectorized operations apply an operation to many values without requiring us to write the Python loop ourselves.

Example:

```python
numbers = np.array([1, 2, 3, 4, 5])

print(numbers + 10)
print(numbers * 2)
print(numbers / 2)
```

Output:

```text
[11 12 13 14 15]
[ 2  4  6  8 10]
[0.5 1.  1.5 2.  2.5]
```


---

# Creating Arrays

## From a List

```python
numbers = np.array([1, 2, 3, 4])
```

## From a Tuple

```python
numbers = np.array((1, 2, 3, 4))
```

## Array of Zeros

```python
zeros = np.zeros(5)

print(zeros)
```

Output resembles:

```text
[0. 0. 0. 0. 0.]
```

## Array of Ones

```python
ones = np.ones(5)

print(ones)
```

## Range

```python
numbers = np.arange(1, 10)

print(numbers)
```

Output:

```text
[1 2 3 4 5 6 7 8 9]
```

Important distinction:

```python
range(1, 10)
```

is Python's built-in range.

```python
np.arange(1, 10)
```

creates a NumPy array.

---

# `np.arange()`

Examples:

```python
np.arange(5)
```

Output:

```text
[0 1 2 3 4]
```

With start and stop:

```python
np.arange(2, 10)
```

Output:

```text
[2 3 4 5 6 7 8 9]
```

With step:

```python
np.arange(2, 10, 2)
```

Output:

```text
[2 4 6 8]
```

---
# Array Data Types

NumPy arrays have a data type.

```python
numbers = np.array([10, 20, 30])

print(numbers.dtype)
```

The exact displayed dtype can vary by platform/version, but it will be an integer dtype.

For floating-point values:

```python
numbers = np.array([10.5, 20.5, 30.5])

print(numbers.dtype)
```

> `dtype` tells us what kind of values the array stores.

---

# `dtype` Explicitly

We can specify a type:

```python
numbers = np.array([1, 2, 3], dtype=float)

print(numbers)
```

Output:

```text
[1. 2. 3.]
```

Another example:

```python
numbers = np.array([1.2, 2.8, 3.5], dtype=int)

print(numbers)
```

---

# Array Dimensions

A one-dimensional array:

```python
numbers = np.array([10, 20, 30, 40])
```

Conceptually:

```text
[10, 20, 30, 40]
```

A two-dimensional array:

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6]
])
```

Conceptually:

```text
1  2  3
4  5  6
```

This is a major reason NumPy is useful.

---

# Shape

Use:

```python
matrix.shape
```

Example:

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

print(matrix.shape)
```

Output:

```text
(2, 3)
```

Explain:

```text
2 rows
3 columns
```

---

# Number of Dimensions

Use:

```python
matrix.ndim
```

Example:

```python
numbers = np.array([1, 2, 3])

print(numbers.ndim)
```

Output:

```text
1
```

For the matrix:

```python
matrix.ndim
```

Output:

```text
2
```

---

# Number of Elements

Use:

```python
matrix.size
```

Example:

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

print(matrix.size)
```

Output:

```text
6
```

Useful summary:

```text
shape : dimensions/size of each axis
ndim  : number of dimensions
size  : total number of elements
dtype : type of elements
```

---

# Indexing NumPy Arrays

NumPy indexing is similar to Python lists.

```python
numbers = np.array([10, 20, 30, 40])

print(numbers[0])
print(numbers[2])
```

Output:

```text
10
30
```

Negative indexing:

```python
print(numbers[-1])
```

Output:

```text
40
```

---

# Slicing NumPy Arrays

```python
numbers = np.array([10, 20, 30, 40, 50])

print(numbers[1:4])
```

Output:

```text
[20 30 40]
```

Other examples:

```python
print(numbers[:3])
print(numbers[2:])
print(numbers[::2])
```

---

# 2D Array Indexing

For:

```python
matrix = np.array([
    [10, 20, 30],
    [40, 50, 60]
])
```

Access:

```python
print(matrix[0, 0])
```

Output:

```text
10
```

And:

```python
print(matrix[1, 2])
```

Output:

```text
60
```

Mental model:

```text
matrix[row, column]
```

---

# Selecting a Row

```python
print(matrix[0])
```

Output:

```text
[10 20 30]
```

Second row:

```python
print(matrix[1])
```

---

# Selecting a Column

```python
print(matrix[:, 0])
```

Output:

```text
[10 40]
```

Explain:

```text
:
â†’ all rows

0
â†’ first column
```

Another example:

```python
print(matrix[:, 1])
```

Output:

```text
[20 50]
```

---

# Array Arithmetic

```python
numbers = np.array([10, 20, 30])

print(numbers + 5)
print(numbers - 5)
print(numbers * 2)
print(numbers / 10)
```

NumPy performs the operation element by element.

---

# Array-to-Array Operations

```python
a = np.array([10, 20, 30])
b = np.array([1, 2, 3])

print(a + b)
print(a - b)
print(a * b)
```

Output:

```text
[11 22 33]
[ 9 18 27]
[10 40 90]
```

Important:

```python
a * b
```

is element-wise multiplication.

It is not matrix multiplication.

---

# Mathematical Functions

NumPy provides many numerical functions.

```python
numbers = np.array([1, 4, 9, 16])

print(np.sqrt(numbers))
```

Output:

```text
[1. 2. 3. 4.]
```

Other examples:

```python
np.abs()
np.round()
np.floor()
np.ceil()
np.sin()
np.cos()
```

> NumPy provides optimized numerical operations that work naturally with arrays.

---

# Aggregation

Given:

```python
marks = np.array([70, 80, 90, 60, 85])
```

We can calculate:

```python
print(np.sum(marks))
print(np.mean(marks))
print(np.min(marks))
print(np.max(marks))
```

Output:

```text
385
77.0
60
90
```

NumPy arrays also provide methods:

```python
print(marks.sum())
print(marks.mean())
print(marks.min())
print(marks.max())
```

---

# Boolean Conditions

NumPy can compare an entire array.

```python
marks = np.array([45, 60, 75, 30, 90])

print(marks >= 50)
```

Output:

```text
[False  True  True False  True]
```

This is called a Boolean mask/Boolean array.

---

# Boolean Filtering

We can use the condition to select values.

```python
marks = np.array([45, 60, 75, 30, 90])

passed = marks[marks >= 50]

print(passed)
```

Output:

```text
[60 75 90]
```

---

# NumPy Practice

```python
marks = np.array([55, 72, 91, 43, 68, 84])
```

Then calculate:

1. Total marks
2. Average
3. Highest mark
4. Lowest mark
5. Marks greater than or equal to 60
6. Marks after adding 5 bonus marks

Expected concepts:

```python
marks.sum()
marks.mean()
marks.max()
marks.min()
marks[marks >= 60]
marks + 5
```

---

# Transition from NumPy to Pandas

> "NumPy is excellent for numerical arrays. But what if our data looks like a table containing names, ages, cities, salaries, and departments?"

Example:

```text
Name     Age    City       Salary
Alice    25     Indore     40000
Bob      30     Delhi      50000
Charlie  28     Mumbai     45000
```

A NumPy array can represent this, but Pandas is designed specifically for this type of structured data.

---

# What Is Pandas?

Pandas is a Python library for data manipulation and analysis.

It provides two fundamental structures:

```text
Series : one-dimensional labeled data
DataFrame : two-dimensional table
```
---

# Importing Pandas

Convention:

```python
import pandas as pd
```

---

# Pandas Series

A Series is a one-dimensional labeled data structure.

```python
import pandas as pd

marks = pd.Series([70, 80, 90, 60])

print(marks)
```

Output resembles:

```text
0    70
1    80
2    90
3    60
dtype: int64
```

Notice:

```text
0
1
2
3
```

These are indexes.

---

# Series with Custom Index

```python
marks = pd.Series(
    [70, 80, 90],
    index=["Alice", "Bob", "Charlie"]
)

print(marks)
```

Conceptually:

```text
Alice      70
Bob        80
Charlie    90
```

This demonstrates why Pandas is called a labeled data structure.

---

# Accessing Series Data

```python
print(marks["Alice"])
```

Output:

```text
70
```

Position-based access can also be done explicitly:

```python
print(marks.iloc[0])
```

Output:

```text
70
```
 `iloc` for position-based access.

---

# Creating a DataFrame

```python
students = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie"],
    "age": [20, 21, 22],
    "marks": [85, 78, 92]
})

print(students)
```

Output resembles:

```text
      name  age  marks
0    Alice   20     85
1      Bob   21     78
2  Charlie   22     92
```
> A DataFrame is a table with rows and columns.

---

# Inspecting a DataFrame

## `head()`

```python
print(students.head())
```

Shows the first rows.

## `tail()`

```python
print(students.tail())
```

Shows the last rows.

## `shape`

```python
print(students.shape)
```

For three rows and three columns:

```text
(3, 3)
```

## `columns`

```python
print(students.columns)
```

## `dtypes`

```python
print(students.dtypes)
```

---

# `info()`

A very useful method:

```python
students.info()
```

It gives information such as:

- Number of rows
- Columns
- Non-null values
- Data types
- Memory information

---

# `describe()`

For numerical columns:

```python
print(students.describe())
```

It can provide statistics such as:

- Count
- Mean
- Standard deviation
- Minimum
- Quartiles
- Maximum

---

# Selecting a Column

```python
print(students["name"])
```

This returns a Series.

Multiple columns:

```python
print(students[["name", "marks"]])
```

---

# Selecting Rows with `iloc`

```python
print(students.iloc[0])
```

First row.

Multiple rows:

```python
print(students.iloc[0:2])
```

Rows 0 and 1.

---

# Selecting with `loc`

Suppose:

```python
students.index = ["s1", "s2", "s3"]
```

Then:

```python
print(students.loc["s1"])
```

selects the row labeled `s1`.

---

# Filtering DataFrames

This is one of the most important Pandas skills.

```python
students[students["marks"] >= 80]
```

This returns students whose marks are at least 80.

Example:

```python
high_scorers = students[students["marks"] >= 80]

print(high_scorers)
```

---

# Multiple Conditions

Use parentheses.

```python
result = students[
    (students["marks"] >= 80) &
    (students["age"] >= 20)
]

print(result)
```

For OR:

```python
result = students[
    (students["marks"] >= 90) |
    (students["age"] >= 22)
]
```

Important:

Use:

```python
&
|
~
```

for Pandas Boolean expressions.

Do not use:

```python
and
or
```

in these DataFrame conditions.

---

# Adding a Column

```python
students["passed"] = students["marks"] >= 40

print(students)
```

Now Pandas creates a Boolean column.

Example:

```text
      name  age  marks  passed
0    Alice   20     85    True
1      Bob   21     78    True
2  Charlie   22     92    True
```

---

# Calculated Columns

```python
students["bonus_marks"] = students["marks"] + 5
```

Another example:

```python
students["final_marks"] = students["marks"] + students["bonus_marks"]
```

---

# Updating Values

Example:

```python
students.loc[students["name"] == "Bob", "marks"] = 85
```

This finds Bob's row and updates his marks.

For beginners, explain the pieces:

```text
students.loc[
    condition,
    column
]
```

means:

> Select rows matching the condition and the specified column.

---

# Sorting

Sort by marks:

```python
sorted_students = students.sort_values("marks")

print(sorted_students)
```

Descending:

```python
sorted_students = students.sort_values(
    "marks",
    ascending=False
)
```

---

# Missing Values

Real-world datasets often contain missing data.

Example:

```python
students = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie"],
    "marks": [85, None, 92]
})
```

Check:

```python
print(students.isna())
```

Count missing values:

```python
print(students.isna().sum())
```

---

# `dropna()`

Remove rows containing missing values:

```python
cleaned = students.dropna()

print(cleaned)
```

> This creates a result with rows containing missing values removed.

---

# `fillna()`

We can replace missing values.

```python
students["marks"] = students["marks"].fillna(0)
```

Or with an average:

```python
students["marks"] = students["marks"].fillna(
    students["marks"].mean()
)
```

---

# Removing Duplicates

```python
students = students.drop_duplicates()
```

This is useful when datasets contain repeated rows.

---

# Renaming Columns

```python
students = students.rename(
    columns={
        "marks": "score"
    }
)
```

Now the column is:

```text
score
```

---

# Working with Strings

Suppose:

```python
students["name"] = [
    " alice ",
    " bob ",
    " charlie "
]
```

Pandas provides string operations through `.str`.

Example:

```python
students["name"] = students["name"].str.strip()
```

Convert to uppercase:

```python
students["name"] = students["name"].str.upper()
```

Convert to lowercase:

```python
students["name"] = students["name"].str.lower()
```

This is useful for data cleaning.

---

# Reading a CSV File

This is one of the most practical Pandas features.

Suppose we have:

```text
students.csv
```

with:

```csv
name,age,marks
Alice,20,85
Bob,21,78
Charlie,22,92
```

Read it:

```python
import pandas as pd

students = pd.read_csv("students.csv")

print(students)
```

---

# File Path Problems


```text
FileNotFoundError
```

Python must be able to find the file.

works when the current working directory is appropriate.

---

# Saving to CSV

After modifying a DataFrame:

```python
students.to_csv(
    "students_cleaned.csv",
    index=False
)
```

Explain:

```text
index=False
```

prevents Pandas from writing the DataFrame index as an extra CSV column.

---

# Grouping Data

Grouping is one of Pandas' most powerful features.

Create:

```python
employees = pd.DataFrame({
    "name": [
        "Alice",
        "Bob",
        "Charlie",
        "David"
    ],
    "department": [
        "IT",
        "HR",
        "IT",
        "HR"
    ],
    "salary": [
        50000,
        45000,
        60000,
        48000
    ]
})
```

Group by department:

```python
print(
    employees.groupby("department")["salary"].mean()
)
```

Conceptually:

```text
IT
â†’ salaries 50000, 60000
â†’ average 55000

HR
â†’ salaries 45000, 48000
â†’ average 46500
```

---

# Aggregation

Common aggregation functions:

```python
mean()
sum()
min()
max()
count()
```

Example:

```python
employees.groupby("department")["salary"].agg(
    ["count", "mean", "min", "max"]
)
```

---

# Counting Categories

Suppose:

```python
students["city"]
```

contains:

```text
Indore
Delhi
Indore
Mumbai
Delhi
Indore
```

We can use:

```python
print(students["city"].value_counts())
```

---

# A Complete Practical Example

For the final section, build a small student analysis dataset.

Create:

```text
students.csv
```

with:

```csv
name,age,city,marks
Alice,20,Indore,85
Bob,21,Delhi,72
Charlie,22,Indore,91
David,20,Mumbai,65
Eva,21,Delhi,88
Frank,23,Indore,55
Grace,22,Mumbai,79
Henry,20,Delhi,95
```

---

# Load the Dataset

```python
import pandas as pd

students = pd.read_csv("students.csv")

print(students)
```

---

# Inspect the Dataset

```python
print(students.head())
print(students.shape)
print(students.columns)
print(students.info())
```

Then:

```python
print(students.describe())
```

---

# Find Average Marks

```python
average_marks = students["marks"].mean()

print("Average marks:", average_marks)
```

---

# Find Highest Marks

```python
highest = students["marks"].max()

print("Highest marks:", highest)
```

---

# Find the Top Student

```python
top_student = students.loc[
    students["marks"].idxmax()
]

print(top_student)
```

returns the index of the row containing the maximum value.

---

# Find Students Who Passed

Assume passing mark is 40.

```python
passed = students[
    students["marks"] >= 40
]

print(passed)
```

---

# Find High Scorers

```python
high_scorers = students[
    students["marks"] >= 80
]

print(high_scorers)
```

---

# Add a Result Column

```python
students["result"] = students["marks"].apply(
    lambda mark: "Pass" if mark >= 40 else "Fail"
)
```

---

# Add Grade

```python
def calculate_grade(mark):
    if mark >= 90:
        return "A"
    elif mark >= 80:
        return "B"
    elif mark >= 70:
        return "C"
    elif mark >= 60:
        return "D"
    else:
        return "F"


students["grade"] = students["marks"].apply(calculate_grade)

print(students)
```
S
---

# Average Marks by City

```python
city_average = students.groupby("city")["marks"].mean()

print(city_average)
```

> "What is the average student score in each city?"

---

# Number of Students by City

```python
city_counts = students["city"].value_counts()

print(city_counts)
```

---

# Sort Students by Marks

```python
ranked = students.sort_values(
    "marks",
    ascending=False
)

print(ranked)
```

This creates a simple ranking.

---

# Top Three Students

```python
top_three = students.sort_values(
    "marks",
    ascending=False
).head(3)

print(top_three)
```

---

# Save the Analysis

```python
students.to_csv(
    "students_analyzed.csv",
    index=False
)
```
---

# NumPy + Pandas Together

the libraries often work together.

For example:

```python
import numpy as np
import pandas as pd

students = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie"],
    "marks": [85, 72, 91]
})

students["normalized"] = (
    students["marks"] -
    students["marks"].mean()
) / students["marks"].std()

print(students)
```

They are complementary.

---


# Exercises - NumPy

## Exercise 1 - Basic Array

Create:

```python
numbers = np.array([10, 20, 30, 40, 50])
```

Print:

- First element
- Last element
- First three elements
- Shape
- Number of dimensions
- Number of elements

---

## Exercise 2 - Marks

Create:

```python
marks = np.array([55, 67, 89, 43, 92, 76])
```

Calculate:

- Total
- Average
- Minimum
- Maximum
- Values greater than 70

---

## Exercise 3 - Bonus

Add 5 marks to every value.

---

## Exercise 4 - Matrix

Create:

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])
```

Find:

- First row
- Last row
- First column
- Center value
- Shape
- Total number of elements

---

# Exercises - Pandas

## Exercise 1 - DataFrame

Create:

```python
students = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie", "David"],
    "age": [20, 21, 22, 20],
    "marks": [85, 72, 91, 65]
})
```

Then:

- Print the DataFrame.
- Print only `name`.
- Print `name` and `marks`.
- Find students with marks above 80.
- Sort by marks.

---

## Exercise 2 - Result

Create a `result` column:

```text
Pass â†’ marks >= 40
Fail â†’ marks < 40
```

---

## Exercise 3 - Grade

Create:

```text
A â†’ 90+
B â†’ 80â€“89
C â†’ 70â€“79
D â†’ 60â€“69
F â†’ below 60
```

---

## Exercise 4 - Missing Data

Create:

```python
students = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie"],
    "marks": [85, None, 92]
})
```

Practice:

```python
isna()
dropna()
fillna()
```

---

## Exercise 5 - Grouping

Create employee data with:

```text
name
department
salary
```

Find:

- Average salary by department.
- Maximum salary by department.
- Number of employees in each department.

---
