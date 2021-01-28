# Python Basics

No semicolons, spacing matters

## Data Types

ALL values in Python are references.

There is no need to explicitly declare a type for a variable.
```python
str
int
float  # similar to java double
list
tuple  # immutable list
bool
range
```

## Functions

__Functions__ are the same thing as a method.

Function signature and body:

<img src="../pictures/python-function.png" width="400">

### Types

You can also specify parameter and return types:
```python
def greeting(name: str) -> str:
    return 'Hello ' + name
```

Although the function is not strictly bounded by such specifications.

### Self 

Specifying "self" allows referral to instance attributes. 

Serves the same purpose as Java's "this".