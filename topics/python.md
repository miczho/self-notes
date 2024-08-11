## All About Python


| Table of Contents |
| ----------------- |
| [Basics](#basics) |
| [Sample Code](#sample_code) |


# <a id="basics"></a> Basics

No semicolons, spacing matters

### Data Types

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

### Functions

__Functions__ are the same thing as a method.

Function signature and body:

<img src="../img/python_function.png" width="400">

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

# <a id="sample_code"></a> Sample Code

### Conditionals/Loops

```python
for i in range(int)
	# code

for element in list
	# code

try:
	# code
except:
	# code
finally:
	# code
```

## Data Types

A lot of functions can be used between data types.

### String

```python
len(string)  # String length
string[0]
string[0:5]  # Substring - [inclusive : exclusive]

ord(string)  # char to int
string.count('a')  # char frequency 
```

### Int

```python
3 // 2  # Floor division
3 ** 2  # Exponent

chr(integer)  # int to char
```

### List

```python 
len(list)

list.append(item)
list.insert(index, item)
list.remove(item)
list.sort()  # Ascending order
list.pop()  # Can be used like a stack

min(list)  # Smallest element, max(list)
sum(list)
```