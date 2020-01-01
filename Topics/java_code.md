# Useful Java Code

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
Scanner sc = new Scanner (System.in);
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

### Boolean

```java
boolean isLesser = first < second;

&&  // and
||  // or
!condition
```

### Char

[ASCII Chart](../Topics/ascii.md)

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
Arrays.sort(arr);

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
Collections.sort(...);  // arraylist, linkedlist, queue, etc.
Collections.shuffle(arrlist);
Collections.reverse(arrlist);
```

## Misc

```java
e.printStackTrace();
```