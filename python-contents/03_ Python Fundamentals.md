> An exception is an event that interrupts the normal flow of a program because something unexpected or invalid happened.

The goal is not to hide errors. The goal is to **handle expected problems gracefully**.

---

## Syntax Errors vs Exceptions

### Syntax Error

A syntax error means Python cannot understand the code.

```python
if 10 > 5
    print("Yes")
```

Python reports a `SyntaxError`.

### Runtime Exception

The code is syntactically valid, but something goes wrong while running it.

```python
number = 10
print(number / 0)
```

This produces:

```text
ZeroDivisionError
```

Explain the difference:

```text
Syntax Error
    â†“
Python cannot parse the code

Exception
    â†“
Python understands the code,
but something goes wrong while executing it
```

---

## Common Exceptions

Introduce these gradually:

| Exception | Typical Cause |
|---|---|
| `ValueError` | Invalid value |
| `TypeError` | Wrong type |
| `NameError` | Name does not exist |
| `ZeroDivisionError` | Division by zero |
| `IndexError` | Invalid list index |
| `KeyError` | Missing dictionary key |
| `FileNotFoundError` | File does not exist |

---

## `try` and `except`

Basic syntax:

```python
try:
    # code that may cause an exception
except:
    # code that handles the exception
```

Example:

```python
try:
    number = int(input("Enter a number: "))
    print(number)
except:
    print("Something went wrong.")
```

Explain that the risky code goes inside `try`.

---

## Catch Specific Exceptions

Prefer specific exceptions over a bare `except` when teaching good practice.

```python
try:
    number = int(input("Enter a number: "))
    result = 10 / number
    print(result)

except ValueError:
    print("Please enter a valid number.")

except ZeroDivisionError:
    print("Cannot divide by zero.")
```

Try:

```text
Enter a number: abc
```

Output:

```text
Please enter a valid number.
```

Try:

```text
Enter a number: 0
```

Output:

```text
Cannot divide by zero.
```

---

## Multiple Exceptions

```python
try:
    value = int(input("Enter a number: "))
    print(100 / value)

except ValueError:
    print("That is not a number.")

except ZeroDivisionError:
    print("You cannot enter zero.")
```

Explain that Python checks the `except` blocks until it finds one matching the exception.

---

## Using `as`

```python
try:
    number = int("hello")
except ValueError as e:
    print("Error:", e)
```

`e` contains the exception object.

> `as e` gives us a variable referring to the actual exception that occurred.

---

## `else`

`else` runs only if no exception occurs.

```python
try:
    number = int(input("Enter a number: "))
except ValueError:
    print("Invalid number.")
else:
    print("You entered:", number)
```

Flow:

```text
try
 |
 +-- exception --> except
 |
 +-- no exception --> else
```

---

## `finally`

`finally` runs whether an exception occurs or not.

```python
try:
    number = int(input("Enter a number: "))
    print(10 / number)

except ZeroDivisionError:
    print("Cannot divide by zero.")

finally:
    print("Program finished.")
```

Explain that `finally` is useful for cleanup operations.

---

## Raising Exceptions

Sometimes our own code needs to reject invalid input.

```python
age = -5

if age < 0:
    raise ValueError("Age cannot be negative.")
```

Explain:

> `raise` allows the programmer to deliberately generate an exception.

---

## Custom Exceptions

Simple example:

```python
class InvalidAgeError(Exception):
    pass


age = -1

if age < 0:
    raise InvalidAgeError("Age cannot be negative.")
```

---
## Exercises

### Exercise 1

Ask the user for two numbers and divide them. Handle:

- `ValueError`
- `ZeroDivisionError`

### Exercise 2

Write a program that accesses a list element and handles `IndexError`.

### Exercise 3

Write a program that accesses a dictionary key and handles `KeyError`.

---

# Variable Scopes

## What Is Scope?

> Scope is the region of a program where a particular name can be accessed.

---

## Local Scope

Variables created inside a function are normally local to that function.

```python
def show():
    message = "Hello"
    print(message)

show()
```

This works.

But:

```python
def show():
    message = "Hello"

show()

print(message)
```

This produces `NameError`.

---

## Global Scope

A variable created outside functions is generally in global scope.

```python
name = "Alice"

def greet():
    print(name)

greet()
```

The function can read the global variable.

---

## Local vs Global

```python
x = 10

def test():
    x = 20
    print(x)

test()
print(x)
```

Output:

```text
20
10
```

> The two `x` names refer to different bindings because they exist in different scopes.

---

## LEGB Rule

Python searches for a name using:

```text
L â†’ Local
E â†’ Enclosing
G â†’ Global
B â†’ Built-in
```

### Local

Current function.

### Enclosing

An outer function when functions are nested.

### Global

The module-level namespace.

### Built-in

Python's built-in names such as:

```python
print()
len()
sum()
str()
int()
```

---

## Enclosing Scope

```python
def outer():
    message = "Hello"

    def inner():
        print(message)

    inner()

outer()
```

`inner()` finds `message` in the enclosing function.

---

## `global`

Normally, assigning to a name inside a function creates a local variable.

```python
count = 0

def increase():
    global count
    count += 1

increase()

print(count)
```

Output:

```text
1
```

---

## `nonlocal`

Used with nested functions when we want to modify a variable from the enclosing function.

```python
def counter():
    count = 0

    def increase():
        nonlocal count
        count += 1
        print(count)

    increase()
    increase()

counter()
```

Output:

```text
1
2
```

---

## Exercises

### Exercise 1

Predict the output:

```python
x = 5

def test():
    x = 10
    print(x)

test()
print(x)
```

### Exercise 2

Create a global variable and write a function that reads it.

### Exercise 3

Create nested functions and demonstrate enclosing scope.

---

# Namespaces

## What Is a Namespace?

> A namespace is a place where Python keeps track of names and the objects those names refer to.

For example:

```python
name = "Alice"
age = 20
```

Python maintains associations similar to:

```text
name â†’ "Alice"
age  â†’ 20
```

The names are not the objects themselves.

---

## Scope vs Namespace

Make this distinction clear:

```text
Scope
  â†’ Where a name can be accessed

Namespace
  â†’ Where names are stored/mapped to objects
```

They are closely related but not identical concepts.

---

## Global Namespace

At module level:

```python
name = "Alice"
age = 20

print(globals())
```

`globals()` returns a dictionary representing the current global namespace.

---

## Local Namespace

```python
def test():
    x = 10
    y = 20
    print(locals())

test()
```

`locals()` provides a representation of the current local namespace.

---

## `dir()`

`dir()` helps inspect names available on an object.

```python
text = "hello"

print(dir(text))
```

Another example:

```python
numbers = [1, 2, 3]

print(dir(numbers))
```

Students will recognize methods such as:

```text
append
remove
pop
sort
```

---

## Built-in Namespace

Python provides built-in names:

```python
print()
len()
type()
int()
str()
list()
dict()
```

These are available without importing anything.

---

## Namespace Example

```python
x = 10

def test():
    y = 20
    print("Local:", locals())

test()

print("Global:", globals())
```
---

## Exercises

### Exercise 1

Use `locals()` inside a function containing three variables.

### Exercise 2

Use `dir()` on a string and find five methods students recognize.

### Exercise 3

Use `dir()` on a list and identify methods used earlier in the course.

---

# Modules

## What Is a Module?

> A module is a Python file containing code that can be imported and reused by another Python file.

For example:

```text
calculator.py
```

is a module.

---

## Why Use Modules?

Without modules:

```text
main.py
    â†“
hundreds of functions
hundreds of variables
hundreds of lines
```

With modules:

```text
main.py
   |
   +-- calculator.py
   +-- validation.py
   +-- utilities.py
```

Benefits:

- Organization
- Reuse
- Easier maintenance
- Separation of responsibilities

---

## Creating a Module

Create:

```text
calculator.py
```

Add:

```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b
```

Create:

```text
main.py
```

Then:

```python
import calculator

print(calculator.add(10, 5))
print(calculator.subtract(10, 5))
```

Output:

```text
15
5
```

Explain:

```python
calculator.add()
```

means:

> Look inside the `calculator` module for the name `add`.

This reinforces namespaces.

---

## Import Specific Functions

```python
from calculator import add

print(add(10, 5))
```

You can import multiple names:

```python
from calculator import add, subtract
```

---

## Aliases

```python
import calculator as calc

print(calc.add(10, 5))
```

Aliases can make long module names easier to use.

---

## Standard Library Modules

### `math`

```python
import math

print(math.sqrt(25))
print(math.pi)
```

### `random`

```python
import random

number = random.randint(1, 10)
print(number)
```

### `datetime`

```python
import datetime

today = datetime.date.today()
print(today)
```

---

## `__name__`

A module has a special variable called `__name__`.

When a file is run directly, Python generally sets:

```python
__name__ == "__main__"
```

When it is imported, its module name is generally used instead.

---

## `if __name__ == "__main__":`

Example:

```python
def greet():
    print("Hello!")

if __name__ == "__main__":
    greet()
```


> This allows code to run when the file is executed directly, while avoiding that code running automatically when the module is imported.


---

## Packages - Basic Introduction

A package is a way of organizing related modules into a larger structure.

Example:

```text
myapp/
    main.py
    utilities/
        text.py
        numbers.py
```



---

## Exercises

### Exercise 1

Create `math_utils.py` with:

```python
def square(number):
    return number * number

def cube(number):
    return number * number * number
```

Import it from another file.

### Exercise 2

Import only `square`.

### Exercise 3

Create a module with a `greet()` function and use:

```python
if __name__ == "__main__":
```

to control direct execution.

---

# Classes and Objects

## Creating a Class

```python
class Student:
    pass
```

Create an object:

```python
student1 = Student()
student2 = Student()
```

---

## Attributes

We can attach data to an object.

```python
student1.name = "Alice"
student1.age = 20

print(student1.name)
print(student1.age)
```

However, this is not usually the best way to initialize objects. Introduce `__init__`.

---

## `__init__`

```python
class Student:

    def __init__(self, name, age):
        self.name = name
        self.age = age
```

Create objects:

```python
student1 = Student("Alice", 20)
student2 = Student("Bob", 22)
```

Then:

```python
print(student1.name)
print(student2.name)
```

Output:

```text
Alice
Bob
```

---

## What Is `self`?

In:

```python
self.name = name
```

- `name` on the right is the value received by the method.
- `self.name` is an attribute belonging to the particular object.

For:

```python
student1 = Student("Alice", 20)
```

Python creates an object and `self` refers to that object while its method executes.

Conceptually:

```text
student1
   |
   +-- name â†’ "Alice"
   +-- age  â†’ 20
```

---

## Methods

A method is a function defined inside a class.

```python
class Student:

    def __init__(self, name):
        self.name = name

    def introduce(self):
        print("My name is", self.name)
```

Use it:

```python
student = Student("Alice")
student.introduce()
```

Output:

```text
My name is Alice
```

---

## Multiple Objects

```python
student1 = Student("Alice")
student2 = Student("Bob")

student1.introduce()
student2.introduce()
```

Each object has its own data.

---

## Class Attributes

An attribute defined directly in the class can be shared by instances.

```python
class Student:

    school = "ABC School"

    def __init__(self, name):
        self.name = name
```

Then:

```python
student1 = Student("Alice")
student2 = Student("Bob")

print(student1.school)
print(student2.school)
```

Both can access the class attribute.


---

## A Complete Beginner Example

```python
class Student:

    school = "ABC School"

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(self):
        print(f"My name is {self.name}.")
        print(f"I am {self.age} years old.")
        print(f"I study at {self.school}.")


student1 = Student("Alice", 20)
student2 = Student("Bob", 22)

student1.introduce()
print()
student2.introduce()
```

---

## Object State

Explain that an object's attributes represent its current state.

```python
class BankAccount:

    def __init__(self, balance):
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount
```

Then:

```python
account = BankAccount(1000)

account.deposit(500)

print(account.balance)
```

Output:

```text
1500
```

---

## Basic Inheritance

```python
class Animal:

    def speak(self):
        print("Animal makes a sound")


class Dog(Animal):

    def bark(self):
        print("Woof!")


dog = Dog()

dog.speak()
dog.bark()
```

> Inheritance allows one class to reuse and extend behavior from another class.

---

## Method Overriding

```python
class Animal:

    def speak(self):
        print("Some sound")


class Dog(Animal):

    def speak(self):
        print("Woof!")


dog = Dog()
dog.speak()
```

The child class provides its own version of `speak()`.

---

## `super()`

```python
class Animal:

    def __init__(self, name):
        self.name = name


class Dog(Animal):

    def __init__(self, name, breed):
        super().__init__(name)
        self.breed = breed
```

> `super()` is commonly used to call behavior from the parent class.


---

## Exercises

### Exercise 1 - Car

Create:

```python
class Car:
```

with:

- `brand`
- `model`
- `year`

and a method:

```python
display_info()
```

### Exercise 2 - Rectangle

Create a `Rectangle` class with:

- `length`
- `width`
- `area()`

### Exercise 3 - Bank Account

Create:

- `balance`
- `deposit()`
- `withdraw()`

### Exercise 4 - Inheritance

Create:

```text
Animal
  â†“
Dog
Cat
```

with different `speak()` methods.

---

## What Does Dunder Mean?

"Dunder" is short for:

```text
double underscore
```

For example:

```python
__init__
__str__
__len__
```

These methods have special meaning to Python.

---

## Important Principle


> Python performs certain operations by looking for specially named methods on objects.

For example:

```python
len(obj)
```

can involve:

```python
obj.__len__()
```

And:

```python
obj1 + obj2
```

can involve:

```python
obj1.__add__(obj2)
```

---

## `__init__`


```python
class Student:

    def __init__(self, name):
        self.name = name
```

It is used to initialize a newly created object's state.

---

## `__str__`

Without `__str__`:

```python
class Student:

    def __init__(self, name):
        self.name = name


student = Student("Alice")
print(student)
```

Python's default representation is not very human-friendly.

Define `__str__`:

```python
class Student:

    def __init__(self, name):
        self.name = name

    def __str__(self):
        return self.name
```

Now:

```python
student = Student("Alice")
print(student)
```

Output:

```text
Alice
```

> `__str__` defines a human-friendly string representation of an object.

---

## `__repr__`


```python
class Student:

    def __init__(self, name):
        self.name = name

    def __repr__(self):
        return f"Student({self.name!r})"
```

Explain simply:

- `__str__` â†’ human-friendly representation.
- `__repr__` â†’ developer/debugging-oriented representation.

---

## `__len__`

```python
class Classroom:

    def __init__(self, students):
        self.students = students

    def __len__(self):
        return len(self.students)
```

Then:

```python
classroom = Classroom(["Alice", "Bob", "Charlie"])

print(len(classroom))
```

Output:

```text
3
```

Python uses the object's `__len__()` implementation when `len()` is called.

---

## `__eq__`

`__eq__` controls equality behavior.

```python
class Student:

    def __init__(self, name):
        self.name = name

    def __eq__(self, other):
        return self.name == other.name
```

Then:

```python
student1 = Student("Alice")
student2 = Student("Alice")

print(student1 == student2)
```

Output:

```text
True
```

---

## `__add__`

```python
class Product:

    def __init__(self, price):
        self.price = price

    def __add__(self, other):
        return self.price + other.price
```

Use:

```python
p1 = Product(100)
p2 = Product(200)

print(p1 + p2)
```

Output:

```text
300
```


> We taught Python what `+` should mean for our custom objects.

---

## `__lt__`

`__lt__` is related to `<`.

```python
class Student:

    def __init__(self, marks):
        self.marks = marks

    def __lt__(self, other):
        return self.marks < other.marks
```

Then:

```python
student1 = Student(70)
student2 = Student(80)

print(student1 < student2)
```

Output:

```text
True
```

---

## `__getitem__`

This can allow an object to support indexing.

```python
class Team:

    def __init__(self, players):
        self.players = players

    def __getitem__(self, index):
        return self.players[index]
```

Then:

```python
team = Team(["Alice", "Bob", "Charlie"])

print(team[0])
```

Output:

```text
Alice
```

---

## Dunder Methods Summary

| Dunder Method | Common Operation |
|---|---|
| `__init__` | Initialize object |
| `__str__` | `str(obj)` / `print(obj)` |
| `__repr__` | Developer representation |
| `__len__` | `len(obj)` |
| `__eq__` | `obj1 == obj2` |
| `__lt__` | `obj1 < obj2` |
| `__add__` | `obj1 + obj2` |
| `__getitem__` | `obj[index]` |

---