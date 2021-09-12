---
title: Java, JVM and compilers
nav_order: 0
has_children: false
nav_exclude: true
---

# Lesson 2: Java, JVM and compilers

## Goals
* Understand java and javac
* Understand what bytecode is
* Being able to run javac on the commandline and find the generated files
* Do some basic Java exercises 🤩


## Slides
[Google Slides](https://docs.google.com/presentation/d/e/2PACX-1vR7ZtxEYkaNjmf53n-y91HNBKbE16oU1F-Dmf0Vl6APcoaJCyQW8J5uK4tg49mRA4FHYjX5uUUqNxly/embed)


## Java compilation recap
Compile:
```shell
javac MyFile.java
e.g.
javac HelloWorld.java
```
Run:
```shell
java MyFile
e.g.
java HelloWorld
```

## Exercises

### Exercise 1 - easy
Write a Java program to display the following pattern.

```java
   J    a   v     v  a
   J   a a   v   v  a a
J  J  aaaaa   V V  aaaaa
 JJ  a     a   V  a     a
```

If you don't know where to start, try creating a new Java class called Exercice1 and copy-pasting the following into it!

```java
public class Exercice1 {
  public static void main(String[] args) {
    print();
  }

  public static void print() {
    // your code needs to go here!
  }
}
```

### Exercise 2 - easy

Write a Java program to reverse a string. Go to the editor Input Data:
```
Any String, e.g.: The quick brown fox
```
Expected Output:
```
Reverse string: xof nworb kciuq ehT
```

### Exercise 3 - medium

Write a Java program and compute the sum of the digits of an integer. 
Do this with a separate method having the following notation:

```java
    public static int getSumOfDigits(int number) {
        // your code needs to go here!
    }
```
Input Data:
```
Any integer, e.g.: 25
```
Expected Output:
```
The sum of the digits is: 7
```
### Exercise 4 - hard
Write a Java program to create and display unique three-digit number using 1, 2, 3, 4. 
Repeating numbers are not allowed. Valid examples:
```
123
124
132
134
```
Invalid examples:
```
122
111
212
```
Hint: You need nested for loops.
Hint2: There are 24 numbers.

## Homework:
Finish the above easy tasks - and try the hard ones.