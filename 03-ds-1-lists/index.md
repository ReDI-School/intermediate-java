---
title: 03 - Data Structure - Lists
nav_order: 4
has_children: false
nav_exclude: false
---

# Lesson 3: Data Structure - Lists

## Goals

* Understand the difference between Arrays and Lists
* Discuss different kind of Lists
* Declare & Initialise ArrayList and Access its elements
* Code, code, code 🤩

## Recap & Assignment check

Let's look into the assignments from Class 3

## Lists

In Java, we need to declare the size of an array before we can use it. Once the size of an array is
declared, it's not possible to change it.  What if we don't know how many elements will 
be in our array?

To handle this issue, we can use the `List` data structure. The List data structure is defined in
Java by the `List` interface. Unlike arrays, lists can automatically adjust its capacity when we 
add or remove elements from it.

A `List` is an ordered collection (also known as a sequence). The user of this collection has precise
control over where in the list each element is inserted. The user can access elements by their 
integer index (position in the list), and search for elements in the list.

The `ArrayList` class is an implementation of the `List` interface which allows us to create 
resizable arrays.

The list interface looks like this:

```java
interface List<E>{
  // Adds the element to the end of the list increasing its size by 1.
  boolean add(E element);
  // Adds the element to position #index of the list increasing its size by 1.
  boolean add(int index, E element);
  // Replaces the element at position #index, does not increase the size.
  boolean set(int index, E element);
  // Returns the element at #index
  E get(int index);
  // Removes the element at #index and return that element.
  E remove(int index);
  // Removes the first occurrence of the specified element from this list, 
  // if it is present (optional operation).
  boolean remove(E element);
  // Returns the current size of the list
  int size();
}
```

> Question; What other methods can a `List` have?

### Declare & Initialise ArrayList

```java
// create Integer type arraylist
List<Integer> arrayList = new ArrayList<>();

// create String type arraylist
ArrayList<String> arrayList = new ArrayList<>();
```

Note: We can not create array lists of primitive data types like int, float, char, etc. Instead, we
have to use their corresponding *Wrapper* class (Integer, Float, Boolean, etc).

### Methods of ArrayList

Add elements

```java
ArrayList<String> animals = new ArrayList<>();

// Add elements
animals.add("Dog");
animals.add("Cat");
animals.add("Horse");
System.out.println("ArrayList: " + animals);
```

Add Using index number

```java
ArrayList<String> animals=new ArrayList<>();

// Add elements
animals.add(0,"Dog");
animals.add(1,"Cat");
animals.add(2,"Horse");
System.out.println("ArrayList: " + animals);
```

Access ArrayList elements

```java
// Get the element from the array list
String str = animals.get(0);
System.out.print("Element at index 0: " + str);
```

Access ArrayList elements in foreach loop

```java
for (int i = 0; i < animals.size(); i++) {
    System.out.println(animals.get(i));
}

for (String animal: animals) {
    System.out.println(animal);
}
```

Change ArrayList Elements

```java
animals.set(2, "Zebra");
System.out.println("Modified ArrayList: " + animals);
```

Remove ArrayList Elements

```java
String str = animals.remove(2);
System.out.println("Final ArrayList: " + animals);
System. out.println("Removed Element: " + str);
```

Java ArrayList To Array
```java
// Create a new array of String type
String[] arr = new String[animals.size()];

// Convert ArrayList into an array
animals.toArray(arr);
```

Java Array to ArrayList

```java
// Create an array of String type
String[] arr = {"Dog", "Cat", "Horse"};

// Create an ArrayList from an array
ArrayList<String> animals = new ArrayList<>(Arrays.asList(arr));
```

> Question; What other kind of `Lists` do we have?

> Question; How do you find out whether the given `List` is empty or not?


## [Exercises and Assignments](https://classroom.github.com/a/nJT37gYK ){:target="_blank"}

Please download the assignment from GitHub Classroom.

## Materials

- [ArrayList (Official documentation)](https://docs.oracle.com/javase/7/docs/api/java/util/ArrayList.html ){:target="_blank"}
- [Java ArrayList Vs Array](https://www.programiz.com/java-programming/arraylist ){:target="_blank"}