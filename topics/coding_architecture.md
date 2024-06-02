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

These words are more used in the context of project *ORGANIZATION* rather than *DISTRIBUTION*

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

An **SDK** is a collection of tools, libraries/frameworks, and documentation needed to develop, compile, test, and debug projects for a specific platform or service

Think of libraries/frameworks as singular tools and an SDK as a toolbox

Examples of SDKs:
- the `Java Development Kit (JDK)` includes
    - `javac` for compiling
    - `Java Runtime Environment (JRE)` for executing
    - `Java Standard Library`, one of the core libraries
    - `jdb` for debugging
    - `jar` for packaging Java classes into a single archive file
    - `javadoc` for documentation
- Apple's `iOS SDK` for building iOS apps includes the Xcode IDE, Interface Builder, and various tools and frameworks
- Google's `Firebase SDK` includes tools for analytics, authentication, databases, configuration, file storage, etc.
- `Unity SDK` for game dev includes tools for graphics, physics, audio, and input

## Application Programming Interfaces (APIs)

An **API** is set of rules and protocols that allows different software applications to interact with each other

One popular form is the **REST API (REpresentational State Transfer API)**, which uses HTTP to communicate and JSON or XML for data exchange.  
- More info on HTTP and REST in the [web development article](web_dev.md)

All libraries and frameworks have APIs by nature.

APIs are often meant to abstract the underlying logic so that the API caller cannot see how it functions.

Examples of APIs:
- `Google Maps API` - Allows developers to integrate Google Maps into their applications
- `Windows API (WinAPI)` - Lets applications access system resources like the file system and hardware devices
- `TensorFlow API` - Allows developers to build machine learning models using TensorFlow
- `SQL API` - Executing SQL queries against a database

## Summary

Using a \*restaurant analogy\*
- Restaurant - the entire software service or application
- Customer - the client app
- Menu (API Docs) - lists all the available dishes (functions) at the restaurant
- Waiter (API) - acts as the intermediary (API) who communicates between the customer and the kitchen
- Kitchen - the back-end
- Cookbook (Library/Framework) - contains recipes (libraries) and techniques (frameworks) the kitchen uses to prepare dishes
- Cooking Toolkit (SDK) - includes all the tools and ingredients the chefs need to prepare the dishes. This includes pots, pans, knives, and raw materials.

<a id="02"></a>
# Programming Paradigms

OOP: Attributes vs Properties vs Parameters vs Arguments

Attributes and properties are basically the same thing

Attributes are data representing the state of an object.

Parameters are data passed into a method.

Arguments are the actual data being passed into a method.

When to use one or the other? Try to limit attributes to the necessities, since their scope reaches throughout the entire object. Conversely, a parameter's scope only exists in its associated method.
