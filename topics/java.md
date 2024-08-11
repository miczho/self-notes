## All About Java 


| Table of Contents |
| ----------------- |
| [Basics](#basics) |
| [Sample Code](#sample_code) |


# <a id="basics"></a> Basics

### Primitive Data Types

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

### Reference Data Types

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

### Imports

Some code needs to be imported before it can be used.

```java
import java.util.*;  // imports the entire utilities package
import java.util.Scanner; 
import java.util.ArrayList;
// etc
```

### Method Structure

A __method__ is a set of code that is referred to by a given name.

Method signature and body:  
![](../img/java_method_sign.png)

# <a id="sample_code"></a> Sample Code

### Main Signature

```java
public class Main {
	public static void main(String[] args) {
		// program code
	}
}
```

### Console Input/Output

```java 
System.out.println();
System.out.print();
System.out.printf();

// java.util.Scanner;
Scanner sc = new Scanner(System.in);
String x = sc.nextLine();
int y = sc.nextInt();
```

### Conditionals/Loops

```java
do {
	// code
} while (...) ;


switch(expression) {
  case x:
    // code 
    break;
  case y:
    // code 
    break;
  default:
    // code 
}


for(element : array/arrlist) {
	// code
}


try {
	// code
} catch(Exception e) {
	// code
} finally {
	// code
}
```

## Primitive Data

### Int

```java
// java.util.Random;
Random rand = new Random();
int x = rand.nextInt(100);  // 0 to 99

Math.max(int a, int b);
Math.min(int a, int b);
Math.pow(int val, int pow);
Math.abs(a - b);
Math.PI;
```

#### Bit Manipulation

```java
int1 | int2  // Bitwise OR
int1 ^ int2  // EXCLUSIVE OR (XOR)
int1 & int2  // AND

~int1  // Bitwise complement

int1 << val  // Left shift
int1 >> val
int1 >>> val  // Unsigned right shift

Integer.bitCount(int1)  // returns frequency of 1's (can also do for longs)
```

### Boolean

```java
boolean isLesser = first < second;

&&  // and
||  // or
!condition
```

### Char

[ASCII Chart](../img/ascii_chart.png)

```java
// use single quotes
char c = 100;  // ASCII, letter 'd'

string.charAt(index);
```

## Reference Data

### String

```java
string.length();
string.substring(int start, int end);
string.indexof(...);
string.format("%.2f", value);
string1.equals(string2);

String.valueOf(int n);
```

### Array

```java
int[] arr = new int[n];
arr.length;
arr.clone();  // creates a copy

// java.util.Arrays;
Arrays.toString(arr);
Arrays.deepToString(2dArr);
Arrays.equals(arr1, arr2);
Arrays.sort(arr);  // ascending order

resetArray(arr);  // all to 0
```

### List Interface

```java
List a = new ArrayList();
List b = new LinkedList();
List d = new Stack(); 
List c = new Vector(); 
```

##### ArrayList

```java
// java.util.ArrayList;
ArrayList<String> arrlist = new ArrayList<String>();  // or Integer or Double, or Character, etc.
arrlist.add("First");
arrlist.get(0); 
arrlist.set(i, arrlist.get(i) - 1);
arrlist.size();
arrlist.remove(“First”);
arrlist.contains(element);
arrlist.clone();  // creates a copy
arrlist1.equals(arrlist2);

// java.util.Collections;
Collections.sort(list);  // ascending order
Collections.shuffle(arrlist);
Collections.reverse(arrlist);
```

## Misc

```java
e.printStackTrace();
```