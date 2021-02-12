---
title: hashCode(), equals() and toString()
nav_order: 12
has_children: true
nav_exclude: true
---

# Lesson 12: Recap Array & ArrayList

## Goals
* Learn what the equals method is
* Learn how to write a good equals method
* Learn what the toString method is
* Learn what the hashCode method is
* Learn how to combine the hashCode and equals methods.
* Learn how to generate the hashCode method
* Learn how to generate the equals method


## Recap Object class
Object is the most common ancestor. Every class we create extends implicitly the Object class.
It can be found [here](https://docs.oracle.com/javase/7/docs/api/java/lang/Object.html).

```java
class A {} // is the same as
class A extends Object {}

// Therefore the following always works:
A a = new A(); // is the same as
Object a = new A();
```

As you can see in the Object class, it defines three (and some more, less important ones) methods (and implements them):
- public boolean equals(Object other)
- public int hashCode()
- public String toString()

As every class extends the Object class, every class therefore has these methods. As you can see, they are public and not final,
therefore our own defined classes *can and should* always overwrite these methods. 

## equals
The equals method indicates whether two objects are equal.

```java
A a1 = new A();
A a2 = new A();
a1.equals(a2);
```
The aforementioned equals invocation will return true if the two objects are equal, otherwise false.

#### What does equal mean?
This is completely up to you. For example you can define equals for a class Car as "Cars are equal if they have the 
same amount of wheels and the same colour.". Of course this is not a good example - as this would only take two properties of a 
car into account - however, what if those are the only two properties of your Car class?

Objects are always compared using the `equals` method, NEVER using `==`. The latter only works on primitive types like `int`, but not
with real objects like `Integer`.

## hashCode
A hash is a one way function. Given an object, a hash function returns a representation (in Java an int), however, you can never go from
it's result back to the object.
A hashCode is an integer representation of your object. Remember HashSets and the buckets where Java looks in? Which bucket to look in is 
determined by it's HashCode.
There are rules that a hashCode function has to fulfill:
- The hashCode for an object should be the same every time
- If two objects are equal, then they must have the same hashCode
- If two objects are not equal, they could still have the same hashCode
- Two objects with the same hashCode are not necessarily equal


## IntelliJ
Luckily, IntelliJ helps us with defining hashCode and equals methods. 
In a given class `right click` -> `Generate...`-> `equals and hashCode`.
IntelliJ will make sure to fulfill the requirements. It won't however if you manually
edit it and break it.

## toString
Have you ever tried the following with your class?
```java
public class MyClass {
  private String text;
  
  public MyClass(String text) {
    this.text = text;
  } 

  public static void main(String[] args){
    MyClass clazz = new MyClass("Redis text");
    System.out.println(clazz);
  }
}
```
What is the result? Correct, jibberish. This is because Java does not know about how to print your class.
Therefore a method called `toString()` exists and you can override it.
```java
public class MyClass {
  private String text;
  
  public MyClass(String text) {
    this.text = text;
  } 
  
  @Override
  public String toString() {
    return "MyClass[text = " + text +"]";  
  }

  public static void main(String[] args){
    MyClass clazz = new MyClass("Redis text");
    System.out.println(clazz);
  }
}
```

Again, IntelliJ is your friend and can generate this method for you.

## Exercises
### Point
Creates a class Point with two properties:
```
final Integer x
final Integer y
```
Implements the equals method. Do not generate it. Pay attention and do not use ==.
Implements the hashCode function to return x + y.

In the main method:

- Create a point1 = Point(3, 4)
- Create another point2 = Point(3, 4)
- Create another point3 = Point(2, 5)
- Create another point4 = point1

Answer the following question without coding:
- [No code] What is point1.equals(point2) ? Why?
- [No code] What is point1 == point2 ? Why?
- [No code] What is point1.equals(point1) ? Why?
- [No code] What is point1 == point1 ? Why?
- [No code] What is point1 == point4 ? Why?
- [No code] What is point1.hashCode()?
- [No code] What is point3.hashCode()?
- [No code] What is point1.equals(point3) ? Why?

Verify the answers to the above questions by printing each of them.

## Advanced - MyHashSet
Define another class called `Bucket` with one property
- `final List<Point> items` initialized as an empty list

Implement the following methods in Bucket

- `boolean contains(Point point)` returns true if items contains point otherwise returns false. Here you must use a for loop over items and use the equals method to compare the Points.
- `void add(Point point)` adds point into items if items does not contain point. Feel free to use the previously defined contains method.
- `int size()` returning the size of items

Define another class called MyHashSet with one property

- `final List<Bucket> buckets`.
- Insert 10 new instances of `Bucket` in buckets. Now buckets should be of size 10.

Implement the following methods in `MyHashSet`

- `void add(Point point)` Get the bucket found in buckets at index point.hashCode() and add point to the bucket using Bucket#add
- `boolean contains(Point point)` Get the bucket found in buckets at index point.hashCode() and check if the bucket contains point using Bucket#point.
- `int size()` returning the sum of the sizes of all buckets

In the main method:

- Create an instance of MyHashSet
- Add Point(3, 4) to the created MyHashSet
- [No code] What bucket index in MyHashSet was Point(3, 4) added to?
- [No code] What is the size of that bucket?
- [No code] What is the size of the created MyHashSet?
- Add Point(2, 5) to the created MyHashSet
- [No code] What bucket index in MyHashSet was Point(2, 5) added to?
- [No code] What is the size of that bucket?
[No code] What is the size of the created MyHashSet?
- Does the created MyHashSet contain Point(1, 6)?
- Does the created MyHashSet contain Point(3, 4)?
- Add Point(0, 0) to the created MyHashSet
- [No code] What bucket index in MyHashSet was Point(0, 0) added to?
- [No code] What is the size of that bucket?
- [No code] What is the size of the created MyHashSet?

Congratulations - you've programmed your own `HashSet<Point>`!

## Materials
- [JournalDev equals and hashCode](https://www.journaldev.com/21095/java-equals-hashcode)
- [JournalDev toString](https://www.journaldev.com/18578/java-tostring-method)
- [Object](https://docs.oracle.com/javase/7/docs/api/java/lang/Object.html)
