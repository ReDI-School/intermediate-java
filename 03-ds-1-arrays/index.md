---
title: 3 - Data Structure - Arrays
nav_order: 3
has_children: false
nav_exclude: true
---

# Lesson 3: Data Structure - Arrays

## Goals

* Introducing Arrays
* Declare & Initialise Array
* Access & Change elements of an Array
* Looping through Array elements
* Pass and return Arrays to/from Methods
* Code, code, code 🤩

## Recap & Assignment check

Let's look into the assignment from lesson 2

## Arrays
An array is a collection of items. Each slot in the array can hold an object or a primitive value. Arrays can contain any type of element value (primitive types or objects), but you can't store different types in a single array.

![array](objects-tenElementArray.gif)

Each item in an array is called an element, and each element is accessed by its numerical index. 
As shown in the preceding illustration, numbering begins with 0. The 9th element, for example, 
would therefore be accessed at index 8.

## Declare & Initialise Array

To create an array in Java, you use three steps:

* Declare a variable to hold the array.
* Create a new array object and assign it to the array variable.
* Store things in that array.

This is how you can declare arrays:

```java
public class Main {

    public static void main(String[] args) {
        String names[]; //declaring string array called name
        int[] numbers; // declaring an integer array called numbers
        
    }

}
```

The second step is to create an array object and assign it to that variable. There are two ways to do this:

* Using `new` keyword
* Directly initializing the contents of that array

```java
public class Main {

    public static void main(String[] args) {
       // using new keyword, declares an array of Strings and allocates memory for 10 Strings
        String[] names = new String[10];
       // declares an array of Strings, allocates memory for 4 Strings and initializes all elements
        String[] definedNames = { "Alina", "James", "Anna","Johannes" }; 
    }

}
```
## Access & Change elements in the Array

Once you have an array with initial values, you can get and change the values in each slot of that array. 
To get at a value stored within an array, use the array subscript expression ([]):

```java
public class Main {

    public static void main(String[] args) {
        String[] names = new String[10];
        names[0] = "Alina";
        System.out.println(names[0]);
        names[0]= "Anna";
        System.out.println(names[0]);
    }

}
```
## Looping through array elements

In Java, we can also loop through each element of the array. Below example uses `for loop` to iterate through the array elements

```java
public class Main {

    public static void main(String[] args) {
        String[] names = new String[10];
        for (int i = 0; i < names.length; i++) {
            System.out.println(names[i]);
        }
        for (String name: names) {
            System.out.println(name);
        }
    }
}
```

The property `length` is a built-in property to determine the size of any array. The following code prints the array's size to standard output:

    System.out.println(anArray.length);

## Pass and return Arrays to/from Methods

### Pass an Array to methods

Like variables, we can also pass arrays to methods. Where have you seen this before?

### Return Array from methods

A method can also return an array. For example, the below program returns an array from method `incrementArrElements`.

```java
   public static int[] incrementArrElements(int[] arr){
        for (int i = 0; i < arr.length; i++) {
            arr[i]+=1;
        }     
        // returning  array
        return arr;
   }
```

## [Exercises](https://classroom.github.com/a/vi1e0wLM)

### Find all elements less than X

Write a program to find all elements of the array of ints that are less than X

### Print reversed array

In the java class `PrintReversed` (file in the github repository `src/main/java/com/redi/j2/PrintReversed.java`):

1. Complete the method `printReversedArray` that will print an `int` array reversed. For an array
   `{1,3,5,2,4}`, it prints `{4,2,5,3,1}`
2. Write another method `printReversedList` that will print an `Integer` array reversed.


## [Homework Assignments](https://classroom.github.com/a/vi1e0wLM)

### Merge 2 arrays

In the java class `Merge` (file in the github repository `src/main/java/com/redi/j2/Merge.java`):

1. Complete the method `mergeArrays` that will merge two int arrays into another int array and
   returns it. The merge rule is that for each index, that the element of the first array goes
   before the element of the second array e.g.

   ```
   first = {2, 5, 9}
   second = {1, 4, 0}
   merge = {2, 1, 5, 4, 9, 0}
   ```
   The two arrays are of the same length.

### Find an element

In the java class `FindElement` (file in the github repository `src/main/java/com/redi/j2/FindElement.java`):

1. Complete the method `findFirstInArray` that gets as input a `String` array and a `String`. The
   method should return the first position of the string in this array or -1 if the string is not in
   the array.
2. Write another method called `findLastInArray` that returns the last position of the element.
3. Write the equivalent methods `findFirstInList` and `findLastInList` that does the same as above
   but using a list instead.

### Second smallest

In the java class `SecondSmallest` (file in the github repository `src/main/java/com/redi/j2/SecondSmallest.java`), complete the method `secondSmallest` to return the second-smallest item in an array of integers.

For example
- the second smallest of `[0, 1, 2, 3]` is `1`
- the second smallest of `[1, 3, 4, 1, 1, 4, 2]` is `2` and
- the second smallest of `[2]` is `2`


## Materials

- [Arrays from Oracle](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html){:target="_blank"}
- [Arrays](https://www.programiz.com/java-programming/arrays){:target="_blank"}
- [Java Arrays](http://tutorials.jenkov.com/java/arrays.html){:target="_blank"}
- [More Java Arrays](https://www.w3schools.com/java/java_arrays.asp){:target="_blank"}
- [Multidimensional arrays](https://www.geeksforgeeks.org/multidimensional-arrays-in-java/){:target="_blank"}
