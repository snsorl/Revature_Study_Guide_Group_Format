# LISTS

> "Python provides a data structure called a **list**, which allows us to store multiple values in a single variable."

---

A **list** is an ordered and mutable collection of elements.

Example:

```python
students = ["Rahul", "Priya", "Amit"]
```

Explain the words:

### Ordered

Elements have a defined position.

```text
Rahul â†’ position 0
Priya â†’ position 1
Amit  â†’ position 2
```

### Mutable

The contents can be changed after the list is created.

### Collection

A list can contain multiple values.

---

## Creating a List

```python
students = ["Rahul", "Priya", "Amit"]
```

Another example:

```python
marks = [80, 75, 92, 88, 67]
```

Strings:

```python
languages = ["Python", "Java", "C++"]
```

Mixed data:

```python
data = [10, "Python", 3.14, True]
```


> "Although Python allows different data types in a list, in real applications we usually store related data together."

---

## Checking a List

```python
students = ["Rahul", "Priya", "Amit"]

print(students)
print(type(students))
```

Output:

```text
['Rahul', 'Priya', 'Amit']
<class 'list'>
```

---

## List Indexing

This is one of the most important concepts.

```python
students = ["Rahul", "Priya", "Amit", "Neha"]
```

Visualize it on the board:

```text
Value       Rahul   Priya   Amit   Neha
Index         0       1       2      3
```

Access:

```python
print(students[0])
```

Output:

```text
Rahul
```

```python
print(students[2])
```

Output:

```text
Amit
```


> "Python uses zero-based indexing. The first element is at index 0, the second at index 1, and so on."

---

## Negative Indexing

Python allows us to access elements from the end.

```python
students = ["Rahul", "Priya", "Amit", "Neha"]
```

```text
Index:      0       1       2       3
           Rahul   Priya   Amit    Neha

Negative:  -4      -3      -2      -1
```

Example:

```python
print(students[-1])
```

Output:

```text
Neha
```

```python
print(students[-2])
```

Output:

```text
Amit
```

---

## Changing List Elements

Because lists are mutable:

```python
students = ["Rahul", "Priya", "Amit"]

students[1] = "Neha"

print(students)
```

Output:

```text
['Rahul', 'Neha', 'Amit']
```
---

## Adding Elements - `append()`

`append()` adds one element at the end.

```python
students = ["Rahul", "Priya"]

students.append("Amit")

print(students)
```

Output:

```text
['Rahul', 'Priya', 'Amit']
```

### Important

```python
students.append("Amit")
```

adds **one element**.

---

## `insert()`

`insert()` adds an element at a particular index.

```python
students = ["Rahul", "Priya", "Amit"]

students.insert(1, "Neha")

print(students)
```

Output:

```text
['Rahul', 'Neha', 'Priya', 'Amit']
```

Syntax:

```python
list.insert(index, value)
```

---

## Adding Multiple Elements - `extend()`

```python
numbers = [1, 2, 3]

numbers.extend([4, 5, 6])

print(numbers)
```

Output:

```text
[1, 2, 3, 4, 5, 6]
```

Compare:

```python
numbers.append([4, 5])
```

versus:

```python
numbers.extend([4, 5])
```

This is an excellent live demonstration.

---

## Removing Elements - `remove()`

```python
students = ["Rahul", "Priya", "Amit"]

students.remove("Priya")

print(students)
```

Output:

```text
['Rahul', 'Amit']
```

`remove()` removes a value.

---

## `pop()`

`pop()` removes an element using its index.

```python
students = ["Rahul", "Priya", "Amit"]

removed = students.pop(1)

print("Removed:", removed)
print(students)
```

Output:

```text
Removed: Priya
['Rahul', 'Amit']
```

Important distinction:

```text
remove() â†’ removes by value
pop()    â†’ removes by index
```

---

## `del`

```python
students = ["Rahul", "Priya", "Amit"]

del students[1]

print(students)
```

Output:

```text
['Rahul', 'Amit']
```

---

## List Slicing

Slicing extracts part of a list.

```python
numbers = [10, 20, 30, 40, 50]
```

```python
print(numbers[1:4])
```

Output:

```text
[20, 30, 40]
```

Explain:

```python
numbers[start:end]
```

The `start` is included.

The `end` is excluded.

So:

```python
numbers[1:4]
```

means indexes:

```text
1, 2, 3
```

### More slicing examples

```python
numbers = [10, 20, 30, 40, 50]
```

First three:

```python
print(numbers[:3])
```

Output:

```text
[10, 20, 30]
```

From index 2 onward:

```python
print(numbers[2:])
```

Output:

```text
[30, 40, 50]
```

Copy:

```python
print(numbers[:])
```

---

## Looping Through a List

```python
students = ["Rahul", "Priya", "Amit"]

for student in students:
    print(student)
```

Output:

```text
Rahul
Priya
Amit
```

---

## Common List Methods

| Method | Purpose |
|---|---|
| `append()` | Add one item |
| `extend()` | Add multiple items |
| `insert()` | Add at a position |
| `remove()` | Remove by value |
| `pop()` | Remove by index |
| `clear()` | Remove all items |
| `sort()` | Sort the list |
| `reverse()` | Reverse the list |
| `index()` | Find position |
| `count()` | Count occurrences |

Example:

```python
numbers = [40, 10, 30, 20]

numbers.sort()

print(numbers)
```

Output:

```text
[10, 20, 30, 40]
```

---

## Useful Built-in Functions

```python
numbers = [10, 20, 30, 40]
```

```python
print(len(numbers))
print(sum(numbers))
print(max(numbers))
print(min(numbers))
```

Output:

```text
4
100
40
10
```

---

## List Exercises

### Exercise 1

Create a list containing five programming languages and print the third language.

### Exercise 2

Create:

```python
numbers = [10, 20, 30, 40, 50]
```

Print:

- first element
- last element
- first three elements
- last two elements

### Exercise 3

Create a list of five marks. Add another mark, remove one mark, and sort the list.

### Exercise 4

Print every element of:

```python
cities = ["Delhi", "Mumbai", "Pune", "Bhopal"]
```

using a `for` loop.

---

# TUPLES


## Definition

A **tuple** is an ordered and immutable collection of elements.

Example:

```python
student = ("Rahul", 21, 85)
```

Tuple uses:

```text
( )
```

while lists use:

```text
[ ]
```

---

## Creating Tuples

```python
numbers = (10, 20, 30)
```

```python
student = ("Rahul", 21, 85)
```

A tuple can contain different types:

```python
data = ("Python", 100, True, 3.14)
```

---

## Tuple Indexing

```python
student = ("Rahul", 21, 85)

print(student[0])
print(student[1])
print(student[2])
```

Output:

```text
Rahul
21
85
```

Tuple indexing works like list indexing.

---

## Negative Indexing

```python
student = ("Rahul", 21, 85)

print(student[-1])
```

Output:

```text
85
```

---

## Tuple Slicing

```python
numbers = (10, 20, 30, 40, 50)

print(numbers[1:4])
```

Output:

```text
(20, 30, 40)
```

---

## Tuple Immutability

This is the most important concept.

```python
student = ("Rahul", 21, 85)

student[1] = 22
```

This causes:

```text
TypeError
```

> "Once a tuple is created, its elements cannot be changed, added, or removed."

---

## List vs Tuple

| Feature | List | Tuple |
|---|---|---|
| Syntax | `[ ]` | `( )` |
| Ordered | Yes | Yes |
| Mutable | Yes | No |
| Indexing | Yes | Yes |
| Slicing | Yes | Yes |
| Can contain duplicates | Yes | Yes |

Simple rule:

> **Use a list when data may need to change.**

> **Use a tuple when the collection should remain unchanged.**

---

## Tuple Unpacking

```python
student = ("Rahul", 21, 85)

name, age, marks = student

print(name)
print(age)
print(marks)
```

Output:

```text
Rahul
21
85
```


> "Python takes the values from the tuple and assigns them to the variables in order."

---

## Tuple Methods

Tuples have fewer methods because they cannot be modified.

Important ones:

```text
count()
index()
```

Example:

```python
numbers = (10, 20, 10, 30)

print(numbers.count(10))
print(numbers.index(20))
```

Output:

```text
2
1
```

---

## Tuple Exercises

### Exercise 1

Create a tuple containing:

```text
name, age, city
```

Print each value.

### Exercise 2

Create:

```python
numbers = (10, 20, 30, 40, 50)
```

Print:

- first element
- last element
- first three elements

### Exercise 3

Create:

```python
student = ("Rahul", 21, 85)
```

Use tuple unpacking to store the values in separate variables.

### Exercise 4

Create a single-element tuple containing `100`.

---

# SETS

## Definition

A **set** is a collection of **unique elements**.

Example:

```python
languages = {"Python", "Java", "SQL"}
```

Duplicates are automatically eliminated.

```python
languages = {"Python", "Java", "Python", "SQL", "Java"}

print(languages)
```

The result contains only unique values.

---

## Creating an Empty Set

Important:

```python
my_set = {}
```

This creates a dictionary.

Correct:

```python
my_set = set()
```

---

## Sets Are Not Indexed

Given:

```python
languages = {"Python", "Java", "SQL"}
```

Don't do:

```python
print(languages[0])
```

A set does not support normal positional indexing.

> "A set is designed around membership and uniqueness, not positions."

---

## Adding Elements

```python
languages = {"Python", "Java"}

languages.add("SQL")

print(languages)
```

---

## Removing Elements

```python
languages.remove("Java")
```

If the item doesn't exist, `remove()` raises an error.

Alternative:

```python
languages.discard("Java")
```

`discard()` does nothing if the value isn't present.

---

## Membership

Sets are very useful for checking whether something exists.

```python
languages = {"Python", "Java", "SQL"}

print("Python" in languages)
```

Output:

```text
True
```

```python
print("C++" in languages)
```

Output:

```text
False
```

---

## Set Union

Suppose:

```python
python_students = {"Rahul", "Priya", "Amit"}
java_students = {"Amit", "Neha", "Ravi"}
```

Union means:

> Everyone in either set.

```python
all_students = python_students | java_students

print(all_students)
```

---

## Intersection

Intersection means:

> Elements common to both sets.

```python
common = python_students & java_students

print(common)
```

Result:

```text
{'Amit'}
```

---

## Difference

```python
python_only = python_students - java_students

print(python_only)
```


> Students who are in Python but not Java.

---

## Symmetric Difference

```python
result = python_students ^ java_students

print(result)
```

This returns values belonging to either set, but not both.

---

## Set Operations Summary

| Operator | Meaning |
|---|---|
| `|` | Union |
| `&` | Intersection |
| `-` | Difference |
| `^` | Symmetric difference |

---

## Set Exercises

### Exercise 1

Create a set containing duplicate numbers and observe the result.

### Exercise 2

Create two sets:

```python
A = {1, 2, 3, 4}
B = {3, 4, 5, 6}
```

Find:

- union
- intersection
- A - B
- B - A

### Exercise 3

Check whether `"Python"` exists in a set of programming languages.

### Exercise 4

Create an empty set correctly.

---

# DICTIONARIES

## Definition

A **dictionary** is a collection of **key-value pairs**.

Example:

```python
student = {
    "name": "Rahul",
    "age": 21,
    "marks": 85
}
```

Here:

```text
"name"  â†’ key
"Rahul" â†’ value
```

```text
"age" â†’ key
21    â†’ value
```

---

## Why Dictionaries?

Compare:

```python
student = ["Rahul", 21, 85]
```

To understand the data, we need to remember:

```text
index 0 = name
index 1 = age
index 2 = marks
```

Dictionary:

```python
student = {
    "name": "Rahul",
    "age": 21,
    "marks": 85
}
```

The meaning is immediately obvious.

---

## Accessing Values

```python
print(student["name"])
```

Output:

```text
Rahul
```

```python
print(student["marks"])
```

Output:

```text
85
```

---

## `get()`

```python
print(student.get("name"))
```

Output:

```text
Rahul
```

If the key doesn't exist:

```python
print(student.get("city"))
```

Output:

```text
None
```

We can provide a default:

```python
print(student.get("city", "Not available"))
```

Output:

```text
Not available
```

---

## Adding a Key

```python
student["city"] = "Bhopal"
```

Now the dictionary has a new key-value pair.

---

## Updating a Value

```python
student["marks"] = 90
```

This changes the existing value.

---

## Removing Data

```python
student.pop("age")
```

Another option:

```python
del student["age"]
```

---

## Dictionary Methods

```python
student = {
    "name": "Rahul",
    "age": 21,
    "marks": 85
}
```

Keys:

```python
print(student.keys())
```

Values:

```python
print(student.values())
```

Key-value pairs:

```python
print(student.items())
```

---

## Loop Through Dictionary Keys

```python
for key in student:
    print(key)
```

---

## Loop Through Values

```python
for value in student.values():
    print(value)
```

---

## Loop Through Key-Value Pairs

This is especially important:

```python
for key, value in student.items():
    print(key, ":", value)
```

Output:

```text
name : Rahul
age : 21
marks : 85
```

---

## Nested Dictionary

A dictionary can contain another dictionary.

```python
students = {
    "student1": {
        "name": "Rahul",
        "marks": 85
    },
    "student2": {
        "name": "Priya",
        "marks": 92
    }
}
```

Access:

```python
print(students["student1"]["name"])
```

Output:

```text
Rahul
```

---

## Dictionary Exercises

### Exercise 1

Create a dictionary containing:

```text
name
age
city
```

Print each value.

### Exercise 2

Add a `"course"` key.

### Exercise 3

Update the age.

### Exercise 4

Loop through the dictionary using `.items()`.

### Exercise 5

Create two student dictionaries and access their names and marks.

---
# FUNCTIONS

## Definition

A **function** is a reusable block of code designed to perform a specific task.

Basic syntax:

```python
def function_name():
    # statements
```

Example:

```python
def greet():
    print("Hello!")
```

Defining a function does not execute it.

We must call it:

```python
greet()
```

---

## Function Definition vs Function Call

Definition:

```python
def greet():
    print("Hello")
```

Call:

```python
greet()
```


> "Defining a function tells Python what the function should do. Calling the function tells Python to actually do it."

---

## Function with a Parameter

```python
def greet(name):
    print("Hello", name)
```

Call:

```python
greet("Rahul")
```

Output:

```text
Hello Rahul
```

Here:

```python
name
```

is the **parameter**.

```python
"Rahul"
```

is the **argument**.

---

## Multiple Parameters

```python
def add(a, b):
    print(a + b)
```

Call:

```python
add(10, 20)
```

Output:

```text
30
```

---

## `return`

This deserves significant teaching time.

```python
def add(a, b):
    return a + b
```

Now:

```python
result = add(10, 20)

print(result)
```

Output:

```text
30
```

Explain:

```text
return â†’ sends a value back to the caller
print  â†’ displays a value
```

Compare:

```python
def add(a, b):
    print(a + b)
```

with:

```python
def add(a, b):
    return a + b
```

The second is more reusable.

For example:

```python
result = add(10, 20)
```

We can then:

```python
print(result)
```

or:

```python
double = result * 2
```

---

## Function with a List

```python
def calculate_average(marks):
    total = sum(marks)
    average = total / len(marks)

    return average
```

Call:

```python
marks = [80, 90, 70]

result = calculate_average(marks)

print(result)
```

Output:

```text
80.0
```

This combines the earlier list topic with functions.

---

## Default Parameters

```python
def greet(name="Student"):
    print("Hello", name)
```

Calling:

```python
greet()
```

Output:

```text
Hello Student
```

Calling:

```python
greet("Rahul")
```

Output:

```text
Hello Rahul
```

---

## Keyword Arguments

```python
def student_info(name, age):
    print("Name:", name)
    print("Age:", age)
```

Call:

```python
student_info(age=21, name="Rahul")
```

Python identifies the parameters by name.

---

## Local Variables

```python
def calculate():
    x = 10
    print(x)

calculate()
```

`x` exists inside the function.

Trying:

```python
print(x)
```

outside the function will result in an error.

> "A local variable is available within the function where it is created."

---

## Function with Multiple Return Values

Python can return multiple values.

```python
def calculate(a, b):
    total = a + b
    difference = a - b

    return total, difference
```

Then:

```python
result1, result2 = calculate(20, 10)

print(result1)
print(result2)
```

Output:

```text
30
10
```

This connects nicely to tuple unpacking.

---

## Function Exercises

### Exercise 1

Create a function called `greet()` that prints:

```text
Welcome to Python
```

### Exercise 2

Create:

```python
square(number)
```

that returns the square.

### Exercise 3

Create:

```python
is_even(number)
```

that returns whether the number is even.

### Exercise 4

Create:

```python
calculate_total(numbers)
```

that returns the total of a list.

### Exercise 5

Create a function that accepts name and age and displays both.

---

# LAMBDA FUNCTIONS

## Definition

A **lambda function** is a small anonymous function.

"Anonymous" means:

> It does not need a conventional function name defined using `def`.

Syntax:

```python
lambda arguments: expression
```

Example:

```python
lambda x: x * 2
```

---

## Normal Function vs Lambda

Normal:

```python
def square(x):
    return x * x
```

Lambda:

```python
square = lambda x: x * x
```

Call:

```python
print(square(5))
```

Output:

```text
25
```

---

## Lambda with Two Arguments

```python
add = lambda a, b: a + b

print(add(10, 20))
```

Output:

```text
30
```

---

## Lambda Automatically Returns the Expression

Normal:

```python
def double(x):
    return x * 2
```

Lambda:

```python
double = lambda x: x * 2
```

There is no explicit:

```python
return
```

The expression result is returned.

---

## Lambda with `sorted()`

This is the most useful practical demonstration.

```python
students = [
    ("Rahul", 85),
    ("Priya", 92),
    ("Amit", 78)
]
```

Suppose we want to sort by marks.

```python
students.sort(key=lambda student: student[1])

print(students)
```

The lambda:

```python
lambda student: student[1]
```

means:

> "Take one student tuple and return the marks."

---

## Lambda with `max()`

```python
students = [
    ("Rahul", 85),
    ("Priya", 92),
    ("Amit", 78)
]

top_student = max(students, key=lambda student: student[1])

print(top_student)
```

Output:

```text
('Priya', 92)
```

This shows students why lambda exists rather than presenting it merely as unusual syntax.

---

## When Should We Use Lambda?

Good use:

```python
square = lambda x: x * x
```

or as a small function passed to another function:

```python
sorted(students, key=lambda student: student[1])
```

Avoid using lambda for complicated logic.

For example, this is much clearer as a normal function:

```python
def calculate_student_result(...):
    # lots of logic
```

Simple guideline:

> **Simple operation â†’ lambda may be useful.**

> **Complex logic â†’ use `def`.**

---

## Lambda Exercises

### Exercise 1

Create a lambda that doubles a number.

### Exercise 2

Create a lambda that adds two numbers.

### Exercise 3

Create a lambda that calculates the square.

### Exercise 4

Given:

```python
numbers = [5, 2, 8, 1, 9]
```

Use `sorted()` with a lambda to sort based on a transformation of each value.

### Exercise 5

Given:

```python
students = [
    ("Amit", 78),
    ("Priya", 95),
    ("Rahul", 84)
]
```

Use a lambda to find the student with the highest marks.

---

# `import` STATEMENT

## What is a Module?

A **module** is a Python file containing reusable code.

For example, a file named:

```text
calculator.py
```

could contain:

```python
def add(a, b):
    return a + b
```

Another Python file can reuse this code.

---

##  Basic `import`

Python provides a module called `math`.

```python
import math
```

Now:

```python
print(math.sqrt(25))
```

Output:

```text
5.0
```

Explain:

```python
math
```

is the module.

```python
sqrt
```

is a function inside that module.

---

## Why Use `math.sqrt()` Instead of `sqrt()`?

When we write:

```python
import math
```

we access the function using:

```python
math.sqrt()
```

This makes it clear where the function came from.

---

## More `math` Examples

```python
import math

print(math.pi)
print(math.sqrt(16))
print(math.ceil(4.2))
print(math.floor(4.8))
```

---

## `from ... import`

Instead of:

```python
import math

print(math.sqrt(25))
```

we can write:

```python
from math import sqrt

print(sqrt(25))
```

Now `sqrt()` is directly available.

---

## Import Multiple Functions

```python
from math import sqrt, ceil, floor

print(sqrt(25))
print(ceil(4.2))
print(floor(4.8))
```

---

## Import Everything

```python
from math import *
```

Explain that although this is valid syntax, it is generally **not recommended** because it makes it less obvious where names came from and can cause naming conflicts.

Prefer:

```python
import math
```

or:

```python
from math import sqrt
```

---

## Aliases

We can give a module another name.

```python
import math as m

print(m.sqrt(25))
```

Here:

```text
math
```

has the alias:

```text
m
```

---

## Common Standard Library Modules

### `math`

Mathematical operations.

```python
import math
```

### `random`

Random values.

```python
import random

print(random.randint(1, 10))
```

### `datetime`

Dates and times.

```python
import datetime

print(datetime.datetime.now())
```

---

## Importing Your Own Module

Create two files:

```text
python_demo/
â”‚
â”œâ”€â”€ main.py
â””â”€â”€ calculator.py
```

### `calculator.py`

```python
def add(a, b):
    return a + b


def subtract(a, b):
    return a - b
```

### `main.py`

```python
import calculator

result1 = calculator.add(10, 20)
result2 = calculator.subtract(20, 5)

print(result1)
print(result2)
```

Output:

```text
30
15
```

This demonstrates a major real-world idea:

> **We can split our Python code into multiple files and reuse functions between those files.**

---

## Import Specific Functions From Our Module

Instead of:

```python
import calculator

print(calculator.add(10, 20))
```

we can:

```python
from calculator import add

print(add(10, 20))
```

---


## `import` Exercises

### Exercise 1

Import `math` and calculate the square root of `144`.

### Exercise 2

Import `pi` from `math`.

### Exercise 3

Import `random` and generate a random number between 1 and 100.

### Exercise 4

Create:

```text
main.py
operations.py
```

Put an `add()` function inside `operations.py` and import it into `main.py`.

### Exercise 5

Import only `add` from `operations.py` rather than importing the entire module.

---

