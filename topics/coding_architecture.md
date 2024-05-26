### Coding Architecture

*THIS ARTICLE TALKS ABOUT IDEAS RELATED TO ORGANIZING CODE*

# Table of Contents

| Section | Title |
| ------- | ----- |
| 01 | [Distributing Code](#01) |
| 02 | [Programming Paradigms](#02) |

<a id="01"></a>
# Distributing Code

Sometimes it is best to use someone else's code when theirs is well written and established  
Sometimes you want to package your code for others to use  
In any case, knowing the common ways code is distributed is important

## Modules & Packages

These words are more used in the context of *ORGANIZATION* rather than *DISTRIBUTION*

*\*DISCLAIMER\* DIFFERENT LANGUAGES WILL HAVE SLIGHTLY DIFFERENT DEFINITIONS OF EACH WORD*

A **module** is a self-contained unit of code (typically found as a single file) that encapsulates related functionality

Here's an example of a Node.js module being defined and used:

```js
// calculator.js

function add(a, b) {
    return a + b;
}

function subtract(a, b) {
    return a - b;
}

function multiply(a, b) {
    return a * b;
}

function divide(a, b) {
    if (b === 0) {
        throw new Error("Cannot divide by zero");
    }
    return a / b;
}

// Export functions for use in other modules
module.exports = {
    add,
    subtract,
    multiply,
    divide
};
```

```js
// main.js

// Import the calculator module
const calculator = require('./calculator');

// Perform arithmetic operations using functions from the calculator module
calculator.add(5, 3);
calculator.subtract(10, 4);
calculator.multiply(6, 2);
calculator.divide(20, 5);
```

A **package** is typically a collection of modules

Examples of packages in different settings:

```bash
# Python
my_package/
├── __init__.py
├── module1.py
└── module2.py

# Java
com/
└── example/
    └── mypackage/
        ├── MyClass1.java
        └── MyClass2.java

# Node.js
my-package/
├── node_modules/
│   ├── express/
│   │   ├── ...
│   │   └── ...
│   └── lodash/
│       ├── ...
│       └── ...
├── package.json
├── index.js
└── README.md
```

## Libraries

A **library** is pre-written code that implements related functionality

Here's an example using the `random` module inside the Python Standard Library:

```python
import random

# Generate a random floating-point number between 0 and 1
random.random()

# Generate a random integer between 1 and 10
random.randint(1, 10)

# Randomly choose an element from a list
my_list = [1, 2, 3, 4, 5]
random.choice(my_list)
```

More examples of libraries:
- `NumPy` - Python numerical computing, especially with large multi-dimensional arrays and matrices
- `Lodash` - A JavaScript utility library delivering modularity, performance & extras
- `Apache Commons` - A library of reusable Java components
- `Standard Template Library (STL)` - A collection of generic classes and functions for C++, providing data structures and algorithms

## Frameworks

A **framework** is pre-written code that implements a particular methodology

Like a scaffold, a framework guides you on how you *should* build your project, streamlining development and enforcing best practices

Frameworks have **Inversion of Control**; whereas you call library functions, frameworks call your functions

Here's an example with the Node.js back-end web framework, `Express.js`

```js
// app.js

const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
    res.send('Hello, World!');
});

app.listen(port, () => {
    console.log(`Example app listening at http://localhost:${port}`);
});
```

More examples of frameworks:
- `Vue.js` - Buiding simple and flexible UI using JavaScript
- `Electron` - Building cross-platform desktop apps using web tech like HTML, CSS, and JS
- `TensorFlow` - Python framework made by Google for building and deploying machine learning models at scale

## Software Development Kits (SDKs)


## Application Programming Interfaces (APIs)

## Summary


<table>
  <tr>
    <td></td>
    <th>Library</th>
    <th>Framework</th>
    <th>SDK</th>
    <th>API</th>
  </tr>
  <tr>
    <th>Local to project?</th>
    <td>no</td>
    <td>no</td>
    <td>no</td>
    <td>no</td>
  </tr>
  <tr>
    <th>Composed of?</th>
    <td>one or more modules</td>
    <td>one or more libraries</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th>Row 3</th>
    <td>Row 3, Column 2</td>
    <td>Row 3, Column 3</td>
  </tr>
</table>


<a id="02"></a>
# Programming Paradigms

OOP: Attributes vs Properties vs Parameters vs Arguments

Attributes and properties are basically the same thing

Attributes are data representing the state of an object.

Parameters are data passed into a method.

Arguments are the actual data being passed into a method.

When to use one or the other? Try to limit attributes to the necessities, since their scope reaches throughout the entire object. Conversely, a parameter's scope only exists in its associated method.
