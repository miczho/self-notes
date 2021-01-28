# Java Basics

## Primitive Data Types

Variables of these store *values*, thus they're copied by default.
```java
int
long
double
char
boolean
byte
short
float
```

## Reference Data Types

Variables store *addresses*, so copies just reference the same object.
```java
String
int[]  // all array types
// any sort of class/object
```
Space must be given before data can be put in.
```java
// ex
Scanner sc = new Scanner(System.in);
```


## Imports

Some code needs to be imported before it can be used.
```java
import java.util.*;  // imports the entire utilities package
import java.util.Scanner; 
import java.util.ArrayList;
// etc
```

## Method Structure

A __method__ is a set of code that is referred to by a given name.

Method signature and body: 
![](../pictures/java-method-sign.png)