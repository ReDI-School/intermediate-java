---
title: Array & ArrayList
nav_order: 6
has_children: true
---

# Lesson 6: Recap Array & ArrayList

## Goals
* Declare & Initialise Array and Access its elements 
* Declare & Initialise ArrayList and Access its elements 
* Understand the difference between Array vs ArrayList
* Code, code, code 🤩

## Recap & Homework check
Let's look into the homework from lesson 5

## Array
![array](objects-tenElementArray.gif)

An array is a collection of items. Each slot in the array can hold an object or a primitive value. 
Arrays can contain any type of element value (primitive types or objects), but you can't store different types in a single array.

### Declare & Initialise Array
To create an array in Java, you use three steps:
 * Declare a variable to hold the array.
 * Create a new array object and assign it to the array variable.
 * Store things in that array.

This is how you can declare arrays:
```java
public class Main {
    public static void main(String[] args){
        String names[];
        int[] numbers;
    }
}
```

The second step is to create an array object and assign it to that variable. There are two ways to do this:
 - Using `new` keyword
 - Directly initializing the contents of that array

```java
public class Main {

    public static void main(String[] args) {
        String[] names = new String[10];
        String[] definedNames = { "Alina", "James", "Anna","Johannes" };
    }

}
```

### Access elements in the Array
Once you have an array with initial values, you can get and change the values in each slot of that array. 
To get at a value stored within an array, use the array subscript expression ([]):

```java
public class Main {

    public static void main(String[] args) {
        String[] names = new String[10];
        names[0] = "Alina";
        System.out.println(names[0]);
    }

}
```

### Go through array 

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

### Exercises

#### Print reversed array
Write a method that will print an int array reversed. For an array {1,3,5,2,4}, it prints {4,2,5,3,1}

#### Merge 2 arrays
Write a method that will merge two int arrays. Merge rule is first element from the first array, then first from the second array, ...
Print the result array.

#### Create an Array from the terminal
Create an array of random int values with the length given from the terminal
Create an array of the length given by the user, all elements are given by the user

#### Find an element
Write a method that gets as input an int array and a number and return a position of the element in this array or -1 if the element is not in the array

Find the first position of the element. 
Find the last position of the element.

## ArrayList
What if the user doesn't know how many elements will be in the array?

In Java, we need to declare the size of an array before we can use it. 
Once the size of an array is declared, it's hard to change it.

To handle this issue, we can use the ArrayList class. 
The ArrayList class present in the java.util package allows us to create resizable arrays.

Unlike arrays, array lists can automatically adjust its capacity when we add or remove elements from it. 

### Declare & Initialise ArrayList
```java
// create Integer type arraylist
ArrayList<Integer> arrayList = new ArrayList<>();

// create String type arraylist
ArrayList<String> arrayList = new ArrayList<>();
```

Note: We can not create array lists of primitive data types like int, float, char, etc. 
Instead, we have to use their corresponding wrapper class.

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
ArrayList<String> animals = new ArrayList<>();

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
### Exercises
#### From Array to ArrayList
Use ArrayList for all exercises from the previous section

#### How do you find out whether the given ArrayList is empty or not?

#### Second Smallest
Write a program to find the second smallest element in an array of integers.
Write a program to find the second smallest element in an array list of integers

#### Find all elements less than X
Write a program to find all elements of the array of ints that are less than X

#### Build Sum element
Given an array arr[] of n integers, construct a Sum Array sum[] (of same size) such that sum[i] is equal to the sum of all the elements of arr[] except arr[i].

#### Create an Array from the terminal 
Add elements to the array from the terminal until the user enters nothing

## Homework
Finish all exercises

### Square matrix calculations
Write user defined methods for square matrix to calculate:
- Left diagonal sum
- Right diagonal sum

### Swap two elements
Write a Java program of swap two elements in an array list.
User enters the positions. Check user's inout, that positions are valid

### Organizing array
Given an array arr[] of random integers, the task is to push all the zero’s in the array to the start and all the one’s to the end of the array.
Note that the order of all the other elements should be the same.

Example:

Input: arr[] = {1, 2, 0, 4, 3, 0, 5, 0}
Output: 0 0 0 2 4 3 5 1

### Check if it is a subset array
Given two arrays and we need to find whether one array is a subset of other or not

Example:
Input:
array1: 1 6 5
array2: 1 4 7 3 5 6

output: yes

## Materials
- [Arrays from Oracle](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html)
- [ArrayList from Oracle](https://docs.oracle.com/javase/7/docs/api/java/util/ArrayList.html)
- [Arrays](https://www.programiz.com/java-programming/arrays)
- [ArrayList](https://www.programiz.com/java-programming/arraylist)
- [Java Arrays](http://tutorials.jenkov.com/java/arrays.html)
- [More Java Arrays](https://www.w3schools.com/java/java_arrays.asp)
- [Multidimensional arrays](https://www.geeksforgeeks.org/multidimensional-arrays-in-java/)
