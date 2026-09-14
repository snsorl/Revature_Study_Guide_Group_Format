# What Is HTTP?

HTTP stands for:

> HyperText Transfer Protocol

HTTP is a protocol used for communication between clients and servers.

A client might be:

- Web browser
- Mobile application
- Another server
- API testing tool
- JavaScript application
- Python program

A server might be:

- Flask application
- Django application
- Node.js application
- Java application
- PHP application

For this lesson:

```text
Client
  â†“
HTTP
  â†“
Flask Server
```

---

# Client and Server

## Client

The client makes the request.

Example:

```text
Browser
```

It might request:

```text
GET /students
```

## Server

The server receives the request and decides what to do.

Our Flask application is the server.

```text
Client
   |
   | GET /students
   v
Flask
   |
   | response
   v
Client
```

---

# What Is a Request?

An HTTP request is a message sent from a client to a server.

A request can contain information such as:

- HTTP method
- URL/path
- Headers
- Query parameters
- Request body

A simplified request:

```text
GET /students HTTP/1.1
```

For a POST request:

```text
POST /students HTTP/1.1

{
    "name": "Alice",
    "age": 20
}
```

---

# What Is a Response?

The server sends an HTTP response back to the client.

A response generally contains:

- Status code
- Headers
- Response body

Example:

```text
HTTP/1.1 200 OK

Hello from Flask!
```

Conceptually:

```text
REQUEST
   â†“
Flask
   â†“
RESPONSE
```

---

# HTTP Methods


| Method | Common Meaning |
|---|---|
| `GET` | Read/retrieve data |
| `POST` | Create new data |
| `PUT` | Update existing data |
| `PATCH` | Partially update data |
| `DELETE` | Delete data |

For the CRUD example, focus on:

```text
GET
POST
PUT
DELETE
```

---

# CRUD

CRUD stands for:

```text
C â†’ Create
R â†’ Read
U â†’ Update
D â†’ Delete
```

Typical API mapping:

```text
Create â†’ POST
Read   â†’ GET
Update â†’ PUT
Delete â†’ DELETE
```

Example:

```text
POST   /students       â†’ Create student
GET    /students       â†’ Get all students
GET    /students/1     â†’ Get student 1
PUT    /students/1     â†’ Update student 1
DELETE /students/1     â†’ Delete student 1
```

This will be the structure of the final exercise.

---

# What Is Flask?

Flask is a Python web framework.

A framework provides tools and conventions that make it easier to build applications.

Instead of manually implementing all HTTP server behavior, Flask provides:

- Routing
- Request handling
- Response handling
- Development server
- JSON support
- URL parameter handling

Import Flask:

```python
from flask import Flask
```

Create an application:

```python
app = Flask(__name__)
```

---

# Installing Flask

Open the VS Code terminal.

Run:

```bash
pip install flask
```

Depending on the Python installation, students may need:

```bash
python -m pip install flask
```

or on some systems:

```bash
py -m pip install flask
```

Verify:

```bash
python -m flask --version
```

If the command works, Flask is installed.

---

# First Flask Application

Create:

```text
app.py
```

Write:

```python
from flask import Flask

app = Flask(__name__)


@app.route("/")
def home():
    return "Hello from Flask!"


if __name__ == "__main__":
    app.run(debug=True)
```

Run:

```bash
python app.py
```

```text
http://127.0.0.1:5000/
```

Open that address in a browser.

Expected response:

```text
Hello from Flask!
```

---

# Explain the Code Line by Line

## Import Flask

```python
from flask import Flask
```

We import the `Flask` class.

---

## Create the Application

```python
app = Flask(__name__)
```

This creates our Flask application object.

Explain:

> `app` represents our Flask web application.

---

## Create a Route

```python
@app.route("/")
```

This tells Flask:

> When a request comes to `/`, use the function below.

---

## Route Function

```python
def home():
    return "Hello from Flask!"
```

The function creates the response.

---

## Run the Application

```python
if __name__ == "__main__":
    app.run(debug=True)
```

This runs the Flask development server when the file is executed directly.


---

# What Is a Route?

A route connects:

```text
HTTP request path
        â†“
Python function
```

Example:

```python
@app.route("/about")
def about():
    return "About page"
```

Now:

```text
GET /about
```

calls:

```python
about()
```

---

# Multiple Routes

```python
from flask import Flask

app = Flask(__name__)


@app.route("/")
def home():
    return "Home"


@app.route("/about")
def about():
    return "About"


@app.route("/contact")
def contact():
    return "Contact"


if __name__ == "__main__":
    app.run(debug=True)
```

Try:

```text
/
 /about
 /contact
```

---

# Route and HTTP Method

By default:

```python
@app.route("/students")
```

handles `GET`.

To explicitly specify methods:

```python
@app.route("/students", methods=["GET"])
def students():
    return "Student list"
```

For multiple methods:

```python
@app.route("/students", methods=["GET", "POST"])
def students():
    ...
```

---

# GET Request

GET is commonly used to retrieve data.

Example:

```python
@app.route("/hello")
def hello():
    return "Hello!"
```

Opening this URL in a browser normally sends a GET request.

```text
GET /hello
```

---

# POST Request

POST is commonly used to send data to the server to create something.

Example:

```python
@app.route("/students", methods=["POST"])
def create_student():
    return "Student created"
```

A normal browser address bar is not a convenient way to send POST requests.

---

# URL Parameters

Sometimes the URL contains an identifier.

Example:

```text
/students/10
```

Flask can capture `10`.

```python
@app.route("/students/<int:student_id>")
def get_student(student_id):
    return f"Student ID: {student_id}"
```

Request:

```text
GET /students/10
```

Response:

```text
Student ID: 10
```

---

# Why `<int:student_id>`?

Flask supports converters.

```python
<int:student_id>
```

means Flask converts the URL portion into an integer.

For example:

```text
/students/25
```

gives:

```python
student_id = 25
```

Other common patterns include:

```python
<string:name>
```

and:

```python
<name>
```

The default is a string.

---

# Query Parameters

Query parameters appear after `?`.

Example:

```text
/students?name=Alice
```

The query parameter is:

```text
name=Alice
```

Flask provides:

```python
request.args
```

Example:

```python
from flask import Flask, request

app = Flask(__name__)


@app.route("/search")
def search():
    name = request.args.get("name")
    return f"Searching for {name}"


if __name__ == "__main__":
    app.run(debug=True)
```

Request:

```text
/search?name=Alice
```

Response:

```text
Searching for Alice
```

---

# URL Parameter vs Query Parameter

This distinction is important.

### URL Parameter

```text
/students/10
```

Usually identifies a specific resource.

```python
@app.route("/students/<int:student_id>")
```

### Query Parameter

```text
/students?age=20
```

Usually provides filtering, searching, sorting, or optional information.

```python
request.args.get("age")
```

A useful mental model:

```text
/students/10
          â†‘
       path parameter


/students?age=20
           â†‘
      query parameter
```

---

# Request Body

POST and PUT requests often send data in the request body.

For APIs, JSON is extremely common.

Example JSON:

```json
{
    "name": "Alice",
    "age": 20
}
```

Flask can read JSON using:

```python
request.get_json()
```

Example:

```python
from flask import Flask, request

app = Flask(__name__)


@app.route("/students", methods=["POST"])
def create_student():
    data = request.get_json()

    print(data)

    return "Student received"


if __name__ == "__main__":
    app.run(debug=True)
```

If the client sends:

```json
{
    "name": "Alice",
    "age": 20
}
```

then:

```python
data
```

is a Python dictionary-like object containing the JSON data.

---

# JSON

JSON stands for:

> JavaScript Object Notation

It is a common data format used for communication between applications.

Example:

```json
{
    "name": "Alice",
    "age": 20,
    "city": "Indore"
}
```

The structure should look familiar because it resembles a Python dictionary.

Python:

```python
{
    "name": "Alice",
    "age": 20
}
```

JSON:

```json
{
    "name": "Alice",
    "age": 20
}
```


---

# Returning JSON

A Flask API normally returns JSON rather than plain text.

Example:

```python
from flask import Flask, jsonify

app = Flask(__name__)


@app.route("/student")
def student():
    return jsonify({
        "id": 1,
        "name": "Alice",
        "age": 20
    })


if __name__ == "__main__":
    app.run(debug=True)
```

Response:

```json
{
    "age": 20,
    "id": 1,
    "name": "Alice"
}
```

---

# `jsonify`

Explain:

```python
jsonify(...)
```

converts Python data into an appropriate JSON response.

Example:

```python
return jsonify({
    "message": "Hello"
})
```

For lists:

```python
return jsonify([
    {"id": 1, "name": "Alice"},
    {"id": 2, "name": "Bob"}
])
```

---

# HTTP Status Codes

An HTTP response includes a status code.

Important beginner codes:

| Code | Meaning |
|---|---|
| `200` | OK |
| `201` | Created |
| `400` | Bad Request |
| `401` | Unauthorized |
| `403` | Forbidden |
| `404` | Not Found |
| `500` | Internal Server Error |

Focus initially on:

```text
200 â†’ successful request
201 â†’ resource created
400 â†’ client sent invalid data
404 â†’ resource not found
500 â†’ server-side error
```

---

# Returning a Status Code

Flask allows:

```python
return jsonify({"message": "Created"}), 201
```

The first value is the response body.

The second value is the status code.

---

# A Small Student API

Before the full CRUD example, build a tiny read-only API.

```python
from flask import Flask, jsonify

app = Flask(__name__)

students = [
    {
        "id": 1,
        "name": "Alice",
        "age": 20
    },
    {
        "id": 2,
        "name": "Bob",
        "age": 21
    }
]


@app.route("/students", methods=["GET"])
def get_students():
    return jsonify(students)


if __name__ == "__main__":
    app.run(debug=True)
```

Visit:

```text
http://127.0.0.1:5000/students
```

Expected:

```json
[
    {
        "age": 20,
        "id": 1,
        "name": "Alice"
    },
    {
        "age": 21,
        "id": 2,
        "name": "Bob"
    }
]
```



---

# Why Use a List Instead of a Database?

> "A real application would usually store this data in a database. For learning HTTP and Flask, we don't need one yet."

Our data:

```python
students = [
    {"id": 1, "name": "Alice", "age": 20},
    {"id": 2, "name": "Bob", "age": 21}
]
```

exists only in memory.

If Flask stops:

```text
Data disappears
```

---

# CRUD Example - Overview

We will build:

```text
Student API
```

Endpoints:

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/students` | Get all students |
| GET | `/students/<id>` | Get one student |
| POST | `/students` | Create student |
| PUT | `/students/<id>` | Update student |
| DELETE | `/students/<id>` | Delete student |

Data:

```python
students = [
    {"id": 1, "name": "Alice", "age": 20},
    {"id": 2, "name": "Bob", "age": 21}
]
```

---

# CRUD - Step 1: Get All Students

```python
@app.route("/students", methods=["GET"])
def get_students():
    return jsonify(students)
```

Request:

```text
GET /students
```

Response:

```json
[
    {
        "id": 1,
        "name": "Alice",
        "age": 20
    },
    {
        "id": 2,
        "name": "Bob",
        "age": 21
    }
]
```

This is:

```text
READ
```

---

# CRUD - Step 2: Get One Student

Route:

```python
@app.route("/students/<int:student_id>", methods=["GET"])
def get_student(student_id):
```

Now find the student.

```python
for student in students:
    if student["id"] == student_id:
        return jsonify(student)
```

If nothing is found:

```python
return jsonify({"error": "Student not found"}), 404
```

Complete version:

```python
@app.route("/students/<int:student_id>", methods=["GET"])
def get_student(student_id):

    for student in students:
        if student["id"] == student_id:
            return jsonify(student)

    return jsonify({"error": "Student not found"}), 404
```

---

# CRUD - Step 3: Create a Student

The client sends:

```json
{
    "name": "Charlie",
    "age": 22
}
```

Flask reads the JSON:

```python
data = request.get_json()
```

Then creates a new dictionary.

```python
new_student = {
    "id": 3,
    "name": data["name"],
    "age": data["age"]
}
```

Add it to the list:

```python
students.append(new_student)
```

Return it:

```python
return jsonify(new_student), 201
```

---

# Generating an ID

For this simple in-memory example, we can calculate the next ID.

```python
new_id = max([student["id"] for student in students], default=0) + 1
```

Explain:

```text
Existing IDs:
1, 2

max â†’ 2

2 + 1 â†’ 3
```

Then:

```python
new_student = {
    "id": new_id,
    "name": data["name"],
    "age": data["age"]
}
```

This is adequate for a classroom demonstration.

Explain that production applications normally use a database or another reliable ID-generation strategy.

---

# Validate Input

Do not blindly assume the client sent correct data.

Bad:

```python
data = request.get_json()

new_student = {
    "name": data["name"],
    "age": data["age"]
}
```

If `name` is missing, this can cause an error.

Better:

```python
data = request.get_json()

if not data:
    return jsonify({"error": "Request body is required"}), 400

if "name" not in data or "age" not in data:
    return jsonify({
        "error": "name and age are required"
    }), 400
```

This is a useful connection to the previous lesson on **exception handling**.

---

# CRUD - Step 4: Update a Student

Client sends:

```text
PUT /students/1
```

with:

```json
{
    "name": "Alice Updated",
    "age": 21
}
```

Find the student:

```python
for student in students:
    if student["id"] == student_id:
```

Read the new data:

```python
data = request.get_json()
```

Update:

```python
student["name"] = data["name"]
student["age"] = data["age"]
```

Return:

```python
return jsonify(student)
```

If it doesn't exist:

```python
return jsonify({"error": "Student not found"}), 404
```

---

# PUT vs PATCH

```text
PUT
â†’ commonly used to replace/update a resource

PATCH
â†’ commonly used for partial updates
```

Example:

PUT:

```json
{
    "name": "Alice",
    "age": 21
}
```

PATCH might update only:

```json
{
    "age": 21
}
```


---

# CRUD - Step 5: Delete

Request:

```text
DELETE /students/2
```

Find the student:

```python
for student in students:
    if student["id"] == student_id:
```

Remove it:

```python
students.remove(student)
```

Return:

```python
return jsonify({
    "message": "Student deleted"
})
```

If it doesn't exist:

```python
return jsonify({"error": "Student not found"}), 404
```

---

# Complete CRUD Application

Create:

```text
app.py
```

Use:

```python
from flask import Flask, jsonify, request

app = Flask(__name__)


students = [
    {
        "id": 1,
        "name": "Alice",
        "age": 20
    },
    {
        "id": 2,
        "name": "Bob",
        "age": 21
    }
]


# ---------------------------------
# GET ALL STUDENTS
# ---------------------------------

@app.route("/students", methods=["GET"])
def get_students():
    return jsonify(students)


# ---------------------------------
# GET ONE STUDENT
# ---------------------------------

@app.route("/students/<int:student_id>", methods=["GET"])
def get_student(student_id):

    for student in students:
        if student["id"] == student_id:
            return jsonify(student)

    return jsonify({
        "error": "Student not found"
    }), 404


# ---------------------------------
# CREATE STUDENT
# ---------------------------------

@app.route("/students", methods=["POST"])
def create_student():

    data = request.get_json()

    if not data:
        return jsonify({
            "error": "Request body is required"
        }), 400

    if "name" not in data or "age" not in data:
        return jsonify({
            "error": "name and age are required"
        }), 400

    new_id = max(
        [student["id"] for student in students],
        default=0
    ) + 1

    new_student = {
        "id": new_id,
        "name": data["name"],
        "age": data["age"]
    }

    students.append(new_student)

    return jsonify(new_student), 201


# ---------------------------------
# UPDATE STUDENT
# ---------------------------------

@app.route("/students/<int:student_id>", methods=["PUT"])
def update_student(student_id):

    data = request.get_json()

    if not data:
        return jsonify({
            "error": "Request body is required"
        }), 400

    for student in students:

        if student["id"] == student_id:

            if "name" in data:
                student["name"] = data["name"]

            if "age" in data:
                student["age"] = data["age"]

            return jsonify(student)

    return jsonify({
        "error": "Student not found"
    }), 404


# ---------------------------------
# DELETE STUDENT
# ---------------------------------

@app.route("/students/<int:student_id>", methods=["DELETE"])
def delete_student(student_id):

    for student in students:

        if student["id"] == student_id:

            students.remove(student)

            return jsonify({
                "message": "Student deleted"
            })

    return jsonify({
        "error": "Student not found"
    }), 404


# ---------------------------------
# RUN APPLICATION
# ---------------------------------

if __name__ == "__main__":
    app.run(debug=True)
```

---

# Testing the CRUD API

Students should test every endpoint.

## Get All

```text
GET /students
```

Expected:

```json
[
    {
        "id": 1,
        "name": "Alice",
        "age": 20
    },
    {
        "id": 2,
        "name": "Bob",
        "age": 21
    }
]
```

---

## Get One

```text
GET /students/1
```

Expected:

```json
{
    "id": 1,
    "name": "Alice",
    "age": 20
}
```

Try:

```text
GET /students/999
```

Expected:

```json
{
    "error": "Student not found"
}
```

Status:

```text
404
```

---

## Create

Send:

```text
POST /students
```

Body:

```json
{
    "name": "Charlie",
    "age": 22
}
```

Expected:

```json
{
    "id": 3,
    "name": "Charlie",
    "age": 22
}
```

Status:

```text
201
```

Then:

```text
GET /students
```

should show Charlie.

---

## Update

Send:

```text
PUT /students/3
```

Body:

```json
{
    "name": "Charlie Brown",
    "age": 23
}
```

Expected:

```json
{
    "id": 3,
    "name": "Charlie Brown",
    "age": 23
}
```

---

## Delete

Send:

```text
DELETE /students/3
```

Expected:

```json
{
    "message": "Student deleted"
}
```

Then:

```text
GET /students
```

Charlie should no longer appear.

---

# Understanding the Request Object

Flask provides:

```python
from flask import request
```

The `request` object contains information about the incoming request.


```python
request.args
request.get_json()
request.method
```

---

## Query Parameters

```python
request.args
```

Example:

```text
/students?name=Alice
```

Read:

```python
name = request.args.get("name")
```

---

## JSON Body

```python
request.get_json()
```

Example:

```json
{
    "name": "Alice"
}
```

Read:

```python
data = request.get_json()
```

---

## HTTP Method

```python
request.method
```

Example:

```python
print(request.method)
```

Could print:

```text
GET
```

or:

```text
POST
```

---

# Route Parameters vs Request Data

Example:

```text
PUT /students/10
```

Here:

```python
student_id
```

comes from the URL.

Example body:

```json
{
    "name": "Alice",
    "age": 21
}
```

comes from:

```python
request.get_json()
```

So:

```text
URL
 â†“
student_id = 10

JSON body
 â†“
name = Alice
age = 21
```

---

# Error Handling in Flask



Suppose:

```python
data = request.get_json()

age = int(data["age"])
```

If invalid data arrives, an exception can occur.

We can validate input before performing operations.

For example:

```python
if not data:
    return jsonify({
        "error": "Request body is required"
    }), 400
```

The important API principle:

> Don't allow invalid client data to silently break the application.

---

# Debug Mode

We use:

```python
app.run(debug=True)
```

Explain:

> Debug mode is useful during development because Flask provides helpful debugging behavior and reloads the application when code changes.

Emphasize:

> Debug mode should not be treated as a production deployment setting.

---

# Mini Exercises

## Exercise 1 - Hello Route

Create:

```text
GET /hello
```

Response:

```text
Hello students!
```

---

## Exercise 2 - About Route

Create:

```text
GET /about
```

Return JSON:

```json
{
    "course": "Python",
    "topic": "Flask"
}
```

---

## Exercise 3 - URL Parameter

Create:

```text
GET /hello/<name>
```

Example:

```text
/hello/Alice
```

Response:

```text
Hello Alice!
```

---

## Exercise 4 - Query Parameter

Create:

```text
GET /search?name=Alice
```

Return:

```json
{
    "search": "Alice"
}
```

---

## Exercise 5 - Simple List API

Create:

```python
colors = [
    "red",
    "green",
    "blue"
]
```

Return the list using:

```python
jsonify()
```

---

# CRUD Exercises

After students understand the supplied CRUD example, give them modifications.

## Exercise 1 - Add Email

Change each student to include:

```text
email
```

Example:

```json
{
    "id": 1,
    "name": "Alice",
    "age": 20,
    "email": "alice@example.com"
}
```

Update POST and PUT.

---

## Exercise 2 - Search

Create:

```text
GET /students?name=Alice
```

Return matching students.

---

## Exercise 3 - Filter by Age

Create:

```text
GET /students?age=20
```

Return students whose age is 20.

---

## Exercise 4 - Delete Confirmation

Change DELETE response to:

```json
{
    "message": "Student Alice deleted successfully"
}
```

---

## Exercise 5 - Validation

Reject:

```json
{
    "name": "",
    "age": -5
}
```

Return status:

```text
400
```

with an appropriate error message.

---
