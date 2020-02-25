# Generics

Reference [Link](https://www.reddit.com/r/learnjava/comments/2u0ab9/really_confused_about_generics_can_somebody_eli5/)

Imagine you have a class called Bucket and you want to put something in that bucket, in this case water:
```java
public class Bucket {

	private Water content;

	public Bucket(Water content) {
	    this.content = content;
	}

	public Water getContent() {
	    return content;
	}
```

If you now create a Bucket you can easily fill it with Water.
```java
Water water = new Water();
Bucket waterBucket = new Bucket(water);
```

But what if you want to fill the Bucket with Sand? It wouldn't be possible because your Bucket only accepts Water.

To make your Bucket more flexible you can use Generics, so let's add Generics to the Bucketclass:
```java
public class Bucket <T>{

	private T content;

	public Bucket(T content) {
	    this.content = content;
	}

	public T getContent() {
	    return content;
	}
```

T stands for Generic which tells the compiler what type of content the bucket will have.

So if you now want to fill the Bucket with sand you can use this:
```java
Sand sand = new Sand();
Bucket<Sand> sandBucket = new Bucket<>(sand);
```

or with Water like this:
```java
Water water = new Water();
Bucket<Water> waterBucket = new Bucket<>(water)
```

A good example is __Lists__ in Java where you have to define the Type of the Entries.