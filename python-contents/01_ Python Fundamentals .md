# Python Introduction

## What is Python?

**Python is a high-level, general-purpose programming language.**

Let's break this definition down.

### Programming Language

A programming language is a language that allows humans to give instructions to a computer.

For example:

```python
print("Hello, World!")
```

We are telling Python:

> Display the text `Hello, World!` on the screen.

### High-Level Language

A high-level language is designed to be relatively easy for humans to read and write.

Compare:

```python
print("Hello")
```

with low-level machine instructions such as binary or processor instructions.

Python hides many low-level computer details from the programmer.

### General-Purpose Language

Python is not restricted to one specific type of application.

Python can be used for:

- Web development
- Automation
- Data analysis
- Artificial intelligence
- Machine learning
- Scientific computing
- Scripting
- Testing
- Desktop applications
- DevOps
- Cybersecurity
- Education

---

## Why is Python Popular?

Python has several important characteristics.

### Simple syntax

Python code is usually concise and readable.

```python
name = "John"
print(name)
```

### Beginner-friendly

Python syntax is relatively close to natural language.

### Large ecosystem

Python has thousands of third-party packages available through PyPI.

### Cross-platform

Python programs can generally run on:

- Windows
- Linux
- macOS

### Large community

There is a large community producing:

- Libraries
- Frameworks
- Tutorials
- Documentation
- Tools
- Open-source projects

---

# Your First Python Program

Create a folder:

```text
python-training
```

Open the folder in VS Code.

Create:

```text
hello.py
```

Write:

```python
print("Hello, World!")
```

Open:

**VS Code â†’ Terminal â†’ New Terminal**

Run:

```bash
python hello.py
```

On some systems, the command may be:

```bash
python3 hello.py
```

Expected output:

```text
Hello, World!
```

---

## Understanding the Program

Consider:

```python
print("Hello, World!")
```

There are several concepts here.

### `print`

`print` is a built-in Python function.

It displays information on the screen.

Example:

```python
print("Python")
print("Programming")
print("Training")
```

Output:

```text
Python
Programming
Training
```

### `"Hello, World!"`

This is a string literal.

We will study string literals in detail later.

### Parentheses

```python
print(...)
```

The parentheses are used to pass information to a function.

For example:

```python
print("Hello")
```

---

# Python Comments

Comments are notes written inside source code for humans.

A single-line comment starts with `#`.

```python
# This prints a greeting
print("Hello")
```

Python ignores the comment when executing the program.

Comments are useful for:

- Explaining code
- Documenting decisions
- Temporarily disabling code
- Helping other developers understand the program

Example:

```python
# Store the user's name
name = "Alice"

# Display the name
print(name)
```

Avoid unnecessary comments such as:

```python
# Print hello
print("Hello")
```

The code is already obvious.

---

# Interpreter vs Compiler

## Learning Objectives

Students should understand:

- What source code is.
- What an interpreter does.
- What a compiler does.
- The conceptual difference between interpreted and compiled execution.
- How Python executes a program.

---

# What is Source Code?

Source code is the program written by the programmer.

Example:

```python
name = "Alice"
print(name)
```

The file might be:

```text
hello.py
```

The computer ultimately needs instructions in a form that the machine can execute.

Therefore, some mechanism must process our source code.

---

# What is an Interpreter?

An **interpreter** is a program that executes source code by processing it during program execution.

A simplified model is:

```text
Python Source Code
        â†“
    Interpreter
        â†“
 Program Execution
        â†“
      Output
```

When we run:

```bash
python hello.py
```

we are asking the Python interpreter to execute the Python program.

---

# What is a Compiler?

A **compiler** translates source code into another form, often machine code or an intermediate representation, before execution.

Conceptually:

```text
Source Code
    â†“
 Compiler
    â†“
Executable / Machine Code
    â†“
 Execution
```

Languages such as C and C++ traditionally use compilation as a major part of their execution model.

---

# Interpreter vs Compiler

| Interpreter | Compiler |
|---|---|
| Processes code during execution | Translates code before execution |
| Often easier to experiment interactively | Often produces a separate executable or compiled artifact |
| Errors can appear during execution | Many errors can be detected during compilation |
| Commonly associated with scripting languages | Commonly associated with compiled languages |

However, students should **not memorize the oversimplification that "Python is interpreted and C is compiled."**

Modern language implementations can use multiple stages.

---

# How Python Actually Executes Code

A useful beginner-level model is:

```text
Python Source Code
       â†“
Python Interpreter
       â†“
Bytecode
       â†“
Python Virtual Machine
       â†“
Execution
```

For example:

```python
print("Hello")
```

When Python executes the program, CPython internally compiles Python source into bytecode and then executes that bytecode.

For beginners, the important idea is:

> We write Python source code, and the Python runtime processes it and executes it.

---

# Interactive Python Interpreter

Open the VS Code terminal and type:

```bash
python
```

You may see:

```text
>>>
```

This is the Python interactive interpreter, commonly called the **REPL**.

REPL means:

```text
Read
Evaluate
Print
Loop
```

Try:

```python
>>> 10 + 20
30
```

Try:

```python
>>> print("Hello")
Hello
```

Try:

```python
>>> 5 * 5
25
```

Exit with:

```python
exit()
```

---

# Virtual Environment - venv

## Learning Objectives

Students should understand:

- What a virtual environment is.
- Why projects need isolated environments.
- How to create a `venv`.
- How to activate and deactivate it.
- How VS Code uses the selected Python interpreter.

---

# The Problem

Imagine two Python projects.

### Project A

Requires:

```text
requests version 2.x
```

### Project B

Requires a different version.

If all packages are installed globally, projects can interfere with each other.

This creates dependency problems.

---

# What is a Virtual Environment?

A **virtual environment** is an isolated Python environment created for a project.

Conceptually:

```text
Computer
â”‚
â”œâ”€â”€ Project A
â”‚   â””â”€â”€ Virtual Environment A
â”‚       â””â”€â”€ Project dependencies
â”‚
â””â”€â”€ Project B
    â””â”€â”€ Virtual Environment B
        â””â”€â”€ Project dependencies
```

Each project can maintain its own dependencies.

---

# Creating a Virtual Environment

In the VS Code terminal:

```bash
python -m venv .venv
```

This creates:

```text
.venv/
```

The `.venv` directory contains the project's virtual environment.

---

# Activating the Virtual Environment

### Windows PowerShell

```powershell
.venv\Scripts\Activate.ps1
```

### Windows Command Prompt

```cmd
.venv\Scripts\activate
```

### Linux/macOS

```bash
source .venv/bin/activate
```

After activation, the terminal commonly displays something similar to:

```text
(.venv)
```

---

# Verify the Environment

Run:

```bash
python --version
```

Then:

```bash
python -c "import sys; print(sys.executable)"
```

This demonstrates which Python executable is being used.

---

# Deactivate

When finished:

```bash
deactivate
```

---

# VS Code Python Interpreter

VS Code can detect Python environments.

Students should select the project's `.venv` interpreter.

Typical process:

```text
Ctrl + Shift + P
        â†“
Python: Select Interpreter
        â†“
Select .venv
```

The important concept is:

> The terminal environment and VS Code's selected Python interpreter should normally point to the same project environment.

---

# PyPI and pip

## Learning Objectives

Students should understand:

- What a package is.
- What PyPI is.
- What pip is.
- How to install packages.
- How to inspect installed packages.
- How to uninstall packages.

---

# What is a Package?

A package is reusable Python software that provides functionality that we can use in our own programs.

Instead of writing everything ourselves, we can use existing libraries.

For example, suppose we need to make HTTP requests.

Instead of implementing HTTP functionality from scratch, we can use a package such as `requests`.

---

# What is PyPI?

**PyPI** stands for:

**Python Package Index**

PyPI is the major public repository for Python packages.

Developers publish Python packages to PyPI so others can install them.

Conceptually:

```text
Developer
   â†“
Publishes package
   â†“
PyPI
   â†“
Developer/User
   â†“
pip install
```

---

# What is pip?

`pip` is a Python package installer.

It is commonly used to install packages from package indexes such as PyPI.

Example:

```bash
python -m pip install requests
```

Using:

```bash
python -m pip
```

is often preferable to simply:

```bash
pip
```

because it makes clear which Python installation/environment is being used.

---

# Installing a Package

Activate the virtual environment.

Then:

```bash
python -m pip install requests
```

Python downloads and installs the package and its dependencies into the environment.

---

# Using an Installed Package

Create:

```text
requests_demo.py
```

Example:

```python
import requests

response = requests.get("https://example.com")

print(response.status_code)
```

This demonstrates an important concept:

```text
pip
 â†“
Install package
 â†“
import package
 â†“
Use package in Python program
```

---

# List Installed Packages

Run:

```bash
python -m pip list
```

You can also use:

```bash
python -m pip show requests
```

---

# Uninstalling a Package

```bash
python -m pip uninstall requests
```

---

# requirements.txt

## Learning Objectives

Students should understand:

- Why projects need dependency documentation.
- What `requirements.txt` is.
- How to generate it.
- How to install dependencies from it.

---

# The Problem

Suppose we build a project using:

```text
requests
flask
pandas
```

Another developer downloads our project.

How do they know what packages are required?

We can document the dependencies in:

```text
requirements.txt
```

---

# Example requirements.txt

```text
requests==2.32.5
```

A project might have:

```text
requests==2.32.5
flask==3.1.2
```

The exact versions depend on the project and environment.

---

# Generate requirements.txt

After installing project dependencies:

```bash
python -m pip freeze > requirements.txt
```

This records installed packages and versions.

---

# Install from requirements.txt

Another developer can create a virtual environment and run:

```bash
python -m pip install -r requirements.txt
```

Conceptually:

```text
requirements.txt
        â†“
       pip
        â†“
Install dependencies
        â†“
Project ready
```

---

# Why Versions Matter

Consider:

```text
requests==2.32.5
```

The `==` means that a particular version is required.

Version information can help make installations more reproducible.

Students should understand the difference between:

```text
requests
```

and:

```text
requests==2.32.5
```

The first does not specify an exact version.

The second does.

---

# Types and Identifiers

## Learning Objectives

Students should understand:

- What data is.
- What a data type is.
- Common Python built-in types.
- Variables.
- Identifiers.
- How Python determines types.

---

# What is Data?

A program works with data.

Examples:

```text
John
25
98.5
True
```

Different types of data require different representations and operations.

---

# What is a Data Type?

A **data type** describes the kind of value an object represents.

Common Python types include:

| Type | Meaning | Example |
|---|---|---|
| `int` | Integer | `10` |
| `float` | Decimal number | `10.5` |
| `str` | Text | `"Python"` |
| `bool` | Boolean | `True` |
| `NoneType` | No value | `None` |

---

# Integers

An integer is a whole number.

```python
age = 25
count = 100
temperature = -5
```

Check the type:

```python
print(type(age))
```

Output:

```text
<class 'int'>
```

---

# Floating-Point Numbers

A `float` represents a number with a decimal component.

```python
price = 99.99
temperature = 36.5
```

Check:

```python
print(type(price))
```

---

# Strings

A string represents text.

```python
name = "Alice"
city = "Delhi"
```

Check:

```python
print(type(name))
```

---

# Boolean

Boolean values represent logical states.

There are two Boolean values:

```python
True
False
```

Example:

```python
is_logged_in = True
is_admin = False
```

---

# None

`None` represents the absence of a value.

```python
result = None
```

Check:

```python
print(type(result))
```

---

# Variables

A variable is a name that refers to a value/object.

Example:

```python
name = "Alice"
age = 25
```

We can then use:

```python
print(name)
print(age)
```

Output:

```text
Alice
25
```

A useful conceptual model is:

```text
name â”€â”€â”€â”€â”€â”€â”€â†’ "Alice"
age  â”€â”€â”€â”€â”€â”€â”€â†’ 25
```

---

# Python is Dynamically Typed

Python variables do not require us to declare a type explicitly.

For example:

```python
value = 10
```

Later:

```python
value = "Hello"
```

This is valid Python.

The object currently referenced by `value` determines the runtime type.

---

# Identifiers and Keywords

## Learning Objectives

Students should understand:

- What an identifier is.
- Rules for creating identifiers.
- Naming conventions.
- Python keywords.
- Invalid identifiers.

---

# What is an Identifier?

An **identifier** is a name used to identify something in Python.

Examples:

```python
name
age
student_name
calculate_total
```

Identifiers can be used for:

- Variables
- Functions
- Classes
- Modules
- Other program elements

---

# Identifier Rules

A Python identifier:

1. Can contain letters.
2. Can contain digits.
3. Can contain underscores.
4. Cannot start with a digit.
5. Cannot be a Python keyword.
6. Is case-sensitive.

Valid:

```python
name
student_name
age2
_total
```

Invalid:

```python
2name
student-name
student name
```

---

# Case Sensitivity

Python is case-sensitive.

These are different identifiers:

```python
name
Name
NAME
```

Example:

```python
name = "Alice"
Name = "Bob"

print(name)
print(Name)
```

Output:

```text
Alice
Bob
```

---

# Naming Convention

Python commonly uses **snake_case** for variables and functions.

Good:

```python
student_name = "Alice"
total_marks = 450
calculate_average()
```

Avoid:

```python
studentName
TotalMarks
```

These styles may be valid Python, but Python's conventional style is generally snake_case.

---

# What are Keywords?

Keywords are reserved words that have special meaning in Python.

Examples include:

```text
if
else
for
while
class
def
return
import
True
False
None
and
or
not
```

You cannot use a keyword as an ordinary variable name.

Invalid:

```python
if = 10
```

---

# Finding Python Keywords

Python provides a `keyword` module.

```python
import keyword

print(keyword.kwlist)
```

This is a useful demonstration because students can see the actual keyword list used by their Python version.

---

# Operators

## Learning Objectives

Students should understand:

- Arithmetic operators.
- Comparison operators.
- Assignment operators.
- Logical operators.
- Membership operators.
- Identity operators.
- Operator precedence.

---

# What is an Operator?

An operator is a symbol or keyword used to perform an operation on values.

Example:

```python
10 + 5
```

Here:

```text
10 â†’ operand
+  â†’ operator
5  â†’ operand
```

Result:

```text
15
```

---

# Arithmetic Operators

| Operator | Meaning | Example |
|---|---|---|
| `+` | Addition | `10 + 5` |
| `-` | Subtraction | `10 - 5` |
| `*` | Multiplication | `10 * 5` |
| `/` | Division | `10 / 5` |
| `//` | Floor division | `10 // 3` |
| `%` | Modulus/remainder | `10 % 3` |
| `**` | Exponentiation | `2 ** 3` |

Examples:

```python
print(10 + 5)
print(10 - 5)
print(10 * 5)
print(10 / 5)
print(10 // 3)
print(10 % 3)
print(2 ** 3)
```

Output:

```text
15
5
50
2.0
3
1
8
```

---

# Assignment Operator

The basic assignment operator is:

```python
=
```

Example:

```python
age = 25
```

This means:

> Assign the value `25` to the variable `age`.

It does **not** mean mathematical equality.

---

# Augmented Assignment

Python provides shorthand operators.

Instead of:

```python
count = count + 1
```

we can write:

```python
count += 1
```

Other examples:

```python
count -= 1
price *= 2
value /= 2
```

---

# Comparison Operators

Comparison operators compare values.

| Operator | Meaning |
|---|---|
| `==` | Equal |
| `!=` | Not equal |
| `>` | Greater than |
| `<` | Less than |
| `>=` | Greater than or equal |
| `<=` | Less than or equal |

Example:

```python
age = 20

print(age == 20)
print(age > 18)
print(age < 18)
```

Output:

```text
True
True
False
```

Comparison operations produce Boolean values.

---

# `=` vs `==`

This is one of the most important beginner distinctions.

Assignment:

```python
age = 20
```

Comparison:

```python
age == 20
```

Explain to students:

```text
=   â†’ assign
==  â†’ compare
```

---

# Logical Operators

Python has:

```python
and
or
not
```

Example:

```python
age = 25
has_id = True

print(age >= 18 and has_id)
```

Both conditions must be true for `and` to produce `True`.

Example:

```python
is_weekend = True
is_holiday = False

print(is_weekend or is_holiday)
```

At least one condition is true.

`not` reverses a Boolean result:

```python
is_logged_in = False

print(not is_logged_in)
```

Output:

```text
True
```

---

# Membership Operators

Membership operators determine whether a value exists inside a collection or sequence.

```python
in
not in
```

Example:

```python
name = "Alice"

print("A" in name)
print("z" in name)
```

Output:

```text
True
False
```

---

# Identity Operators

Python provides:

```python
is
is not
```

They test object identity.

Example:

```python
a = None

print(a is None)
```

Output:

```text
True
```

Beginners should learn an important distinction:

```python
==
```

checks equality.

```python
is
```

checks identity.

Do not teach these as interchangeable.

---

# Operator Precedence

Python follows precedence rules.

Example:

```python
result = 10 + 5 * 2
```

The multiplication happens first:

```text
5 * 2 = 10
10 + 10 = 20
```

Therefore:

```python
print(result)
```

produces:

```text
20
```

Parentheses can make the intended order explicit:

```python
result = (10 + 5) * 2
```

Result:

```text
30
```

---

# String Literals

## Learning Objectives

Students should understand:

- What a string is.
- Different string literal syntaxes.
- Quotes.
- Escape sequences.
- Multiline strings.
- String concatenation.
- Basic string operations.
- Formatted strings.

---

# What is a String?

A string is a sequence of characters used to represent text.

Example:

```python
name = "Alice"
```

The value:

```text
Alice
```

is a string.

---

# String Literals

Python supports single and double quotes.

```python
name = "Alice"
city = 'Delhi'
```

Both represent strings.

We can also use:

```python
message = "Hello, Python!"
```

---

# Why Have Two Quote Styles?

It can make strings containing quotes easier to write.

Example:

```python
message = "Alice's book"
```

Or:

```python
message = 'He said "Hello".'
```

---

# Escape Characters

A backslash introduces escape sequences.

Example:

```python
message = "Hello\nWorld"
print(message)
```

Output:

```text
Hello
World
```

Common escape sequences:

| Escape | Meaning |
|---|---|
| `\n` | New line |
| `\t` | Tab |
| `\\` | Backslash |
| `\"` | Double quote |
| `\'` | Single quote |

---

# Multiline Strings

Triple quotes can represent multiline strings.

```python
message = """This is
a multiline
string."""

print(message)
```

Output:

```text
This is
a multiline
string.
```

---

# String Concatenation

Strings can be joined using `+`.

```python
first_name = "John"
last_name = "Smith"

full_name = first_name + " " + last_name

print(full_name)
```

Output:

```text
John Smith
```

---

# String Repetition

The `*` operator can repeat strings.

```python
print("Hi " * 3)
```

Output:

```text
Hi Hi Hi
```

---

# String Indexing

Strings are sequences.

```python
name = "Python"
```

Indexes start at zero.

```text
P y t h o n
0 1 2 3 4 5
```

Therefore:

```python
print(name[0])
```

Output:

```text
P
```

And:

```python
print(name[3])
```

Output:

```text
h
```

---

# Negative Indexing

Python also supports negative indexes.

```text
P  y  t  h  o  n
-6 -5 -4 -3 -2 -1
```

Therefore:

```python
print(name[-1])
```

Output:

```text
n
```

---

# Basic String Methods

Example:

```python
name = "python programming"

print(name.upper())
print(name.lower())
print(name.title())
```

Output:

```text
PYTHON PROGRAMMING
python programming
Python Programming
```

Other useful methods:

```python
name.strip()
name.replace("python", "Java")
name.startswith("python")
name.endswith("programming")
```

---

# f-Strings

f-strings are one of the most useful ways to construct strings.

```python
name = "Alice"
age = 25

message = f"My name is {name} and I am {age} years old."

print(message)
```

Output:

```text
My name is Alice and I am 25 years old.
```

This is much easier to read than manually concatenating strings.

---

# Conditional Statements

## Learning Objectives

Students should understand:

- Decision making.
- `if`.
- `else`.
- `elif`.
- Conditions.
- Boolean expressions.
- Nested conditions.
- Combining conditions.

---

# Why Do We Need Conditions?

Programs often need to make decisions.

For example:

```text
If the user's age is 18 or more:
    allow registration
Otherwise:
    reject registration
```

Python allows us to express this using conditional statements.

---

# The `if` Statement

Basic syntax:

```python
if condition:
    statement
```

Example:

```python
age = 20

if age >= 18:
    print("You are an adult.")
```

Output:

```text
You are an adult.
```

---

# Indentation

Python uses indentation to define blocks of code.

Correct:

```python
if age >= 18:
    print("Adult")
```

Incorrect:

```python
if age >= 18:
print("Adult")
```

Typically, Python code uses **four spaces** for indentation.

This is an important difference from languages that commonly use braces:

```text
{
    ...
}
```

Python uses indentation.

---

# `if` + `else`

Example:

```python
age = 16

if age >= 18:
    print("Adult")
else:
    print("Minor")
```

Output:

```text
Minor
```

The program chooses exactly one branch.

---

# `if` + `elif` + `else`

Use `elif` when there are multiple conditions.

```python
marks = 75

if marks >= 90:
    print("A")
elif marks >= 75:
    print("B")
elif marks >= 60:
    print("C")
else:
    print("D")
```

Output:

```text
B
```

Python evaluates the conditions from top to bottom.

---

# Multiple Conditions

```python
age = 25
has_id = True

if age >= 18 and has_id:
    print("Entry allowed")
else:
    print("Entry denied")
```

---

# Nested Conditions

A condition can contain another condition.

```python
age = 25
has_id = True

if age >= 18:
    if has_id:
        print("Entry allowed")
    else:
        print("ID required")
else:
    print("You must be 18 or older")
```

Teach nesting, but also explain that excessive nesting can make programs difficult to read.

---

# Practical Example - Grade Calculator

```python
marks = 82

if marks >= 90:
    grade = "A"
elif marks >= 80:
    grade = "B"
elif marks >= 70:
    grade = "C"
elif marks >= 60:
    grade = "D"
else:
    grade = "F"

print(f"Grade: {grade}")
```

This combines:

- Variables
- Numbers
- Comparison operators
- Conditions
- Assignment
- f-strings

This is an excellent integration exercise.

---

# Loops

## Learning Objectives

Students should understand:

- Why repetition is needed.
- `for` loops.
- `while` loops.
- `range()`.
- Loop variables.
- `break`.
- `continue`.
- Nested loops.
- Common loop patterns.

---

# Why Do We Need Loops?

Suppose we want to print numbers 1 through 5.

Without a loop:

```python
print(1)
print(2)
print(3)
print(4)
print(5)
```

This works, but becomes impractical for larger amounts of repetition.

A loop allows us to express the repetition once.

```python
for number in range(1, 6):
    print(number)
```

Output:

```text
1
2
3
4
5
```

---

# The `for` Loop

A `for` loop repeats code for each item in an iterable.

Basic structure:

```python
for variable in iterable:
    statement
```

Example:

```python
names = ["Alice", "Bob", "Charlie"]

for name in names:
    print(name)
```

Output:

```text
Alice
Bob
Charlie
```

---

# Understanding `range()`

`range()` is commonly used with `for`.

```python
range(5)
```

produces numbers conceptually corresponding to:

```text
0
1
2
3
4
```

Notice that `5` is excluded.

Example:

```python
for number in range(5):
    print(number)
```

Output:

```text
0
1
2
3
4
```

---

# `range(start, stop)`

```python
for number in range(1, 6):
    print(number)
```

Output:

```text
1
2
3
4
5
```

The `stop` value is excluded.

This is an important Python convention:

```text
start â†’ included
stop  â†’ excluded
```

---

# `range(start, stop, step)`

Example:

```python
for number in range(2, 11, 2):
    print(number)
```

Output:

```text
2
4
6
8
10
```

Here:

```text
start = 2
stop  = 11
step  = 2
```

---

# Looping Through a String

Strings are iterable.

```python
word = "Python"

for character in word:
    print(character)
```

Output:

```text
P
y
t
h
o
n
```

---

# The `while` Loop

A `while` loop repeats as long as a condition is true.

Syntax:

```python
while condition:
    statement
```

Example:

```python
count = 1

while count <= 5:
    print(count)
    count += 1
```

Output:

```text
1
2
3
4
5
```

---

# `for` vs `while`

A useful beginner guideline:

### Use `for` when:

You are iterating through a known sequence or collection.

```python
for name in names:
    print(name)
```

### Use `while` when:

The repetition depends primarily on a condition.

```python
while password != correct_password:
    ...
```

---

# Infinite Loops

Be careful with `while`.

This loop never changes `count`:

```python
count = 1

while count <= 5:
    print(count)
```

The condition remains true forever.

Correct:

```python
count = 1

while count <= 5:
    print(count)
    count += 1
```

This teaches students the concept of **loop progress**.

---

# `break`

`break` immediately exits a loop.

Example:

```python
for number in range(1, 11):
    if number == 5:
        break

    print(number)
```

Output:

```text
1
2
3
4
```

When `number` becomes `5`, the loop terminates.

---

# `continue`

`continue` skips the rest of the current iteration and proceeds to the next iteration.

Example:

```python
for number in range(1, 6):
    if number == 3:
        continue

    print(number)
```

Output:

```text
1
2
4
5
```

The iteration containing `3` is skipped.

---

# Nested Loops

A loop can contain another loop.

Example:

```python
for row in range(1, 4):
    for column in range(1, 4):
        print(row, column)
```

Output:

```text
1 1
1 2
1 3
2 1
2 2
2 3
3 1
3 2
3 3
```

Nested loops are useful for:

- Tables
- Grids
- Matrix-like data
- Combinations
- Pattern exercises

---

# Practical Example - Multiplication Table

```python
number = 5

for multiplier in range(1, 11):
    result = number * multiplier
    print(f"{number} x {multiplier} = {result}")
```

Output:

```text
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
...
5 x 10 = 50
```

This combines:

- Variables
- Integers
- Arithmetic operators
- `range()`
- `for`
- f-strings

---

# Practical Example - Sum of Numbers

```python
total = 0

for number in range(1, 11):
    total += number

print(total)
```

Output:

```text
55
```

Explain the changing state:

```text
Initial total = 0

number = 1 â†’ total = 1
number = 2 â†’ total = 3
number = 3 â†’ total = 6
...
number = 10 â†’ total = 55
```

This is a very important programming pattern:

> Initialize â†’ Repeat â†’ Update â†’ Use the result.

---

# Practical Example - Find Even Numbers

```python
for number in range(1, 21):
    if number % 2 == 0:
        print(number)
```

This integrates:

- Loop
- Conditional statement
- Modulus operator

Output:

```text
2
4
6
8
10
12
14
16
18
20
```

---

# Integrated Beginner Project

After completing all topics, students should build a small project that combines everything they have learned.

## Project: Student Result Processor

The program should:

1. Store a student's name.
2. Store marks.
3. Calculate the total.
4. Calculate the average.
5. Determine a grade.
6. Display the result.
7. Process multiple students.

Example:

```python
students = [
    ("Alice", [85, 90, 78]),
    ("Bob", [65, 72, 68]),
    ("Charlie", [92, 88, 95]),
]

for name, marks in students:
    total = sum(marks)
    average = total / len(marks)

    if average >= 90:
        grade = "A"
    elif average >= 80:
        grade = "B"
    elif average >= 70:
        grade = "C"
    elif average >= 60:
        grade = "D"
    else:
        grade = "F"

    print(f"Student: {name}")
    print(f"Total: {total}")
    print(f"Average: {average:.2f}")
    print(f"Grade: {grade}")
    print("-" * 30)
```

This project gives students a reason to use multiple concepts together instead of learning them as disconnected syntax.

---

# Beginner Exercises

## Exercise 1 - Personal Introduction

Create variables:

```python
name
age
city
```

Print:

```text
My name is ...
I am ... years old.
I live in ...
```

---

## Exercise 2 - Calculator

Create two numbers and display:

- Addition
- Subtraction
- Multiplication
- Division
- Remainder

---

## Exercise 3 - Even or Odd

Given:

```python
number = 17
```

Print:

```text
Even
```

or:

```text
Odd
```

Hint:

```python
number % 2
```

---

## Exercise 4 - Age Category

Given an age, display:

```text
Child
Teenager
Adult
Senior
```

Use conditional statements.

---

## Exercise 5 - Grade

Given marks, calculate:

```text
90+  â†’ A
80+  â†’ B
70+  â†’ C
60+  â†’ D
Below 60 â†’ F
```

---

## Exercise 6 - Number Printer

Print numbers from 1 to 100.

Then modify the program to print only even numbers.

---

## Exercise 7 - Multiplication Table

Ask the user for a number and print its multiplication table from 1 to 10.

---

## Exercise 8 - Sum

Calculate the sum of numbers from 1 to 100.

---

## Exercise 9 - Countdown

Use a `while` loop to print:

```text
10
9
8
7
...
1
```

Then print:

```text
Blast off!
```

---
