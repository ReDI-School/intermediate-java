---
title: "Homework Solutions"
nav_order: 0
parent: "1 - Introduction to Programming with Java"
nav_exclude: true
---

# Exercise 1

Write the method "squares" that for X and Y given by arguments prints the square of each number between X and Y.

```java
square(1,3)
> 1 - 1
> 2 - 4
> 3 - 9

square(5,6)
> 5 - 25
> 6 - 36
```

If you don't know where to start, try creating a new Java class called ExerciseIntro and copy-pasting the following into it!

```java
public class ExerciseIntro {
    public static void main(String[] args) {
        square(1, 3);
        square(5, 6);
    }

    public static void square(int x, int y) {
        // your code needs to go here!
    }
}
```

## Solution
```java
private static void squares(int x, int y) {
    for (int i = x; i < y; i++) {
        System.out.println(i + " - " + (i * i));
    }
}
```

# Exercise 2

In german, nouns ending with e are almost always feminine. Write a method _isFeminineNoun_ that checks if the provided word ends with e or not.


```
isFeminineNoun("Katze")
> true

isFeminineNoun("Hund")
> false
```

Bonus: can you also make sure the method also catches words ending in _-ung_? Those are also feminine.

## Solution
```java
private static void isFeminineNoun(String noun) {
    boolean isFeminine = noun.endsWith("e");
    System.out.println(isFeminine);
}

private static void isFeminineNounExpanded(String noun) {
    boolean isFeminine = noun.endsWith("e") || noun.endsWith("ung");
    System.out.println(isFeminine);
}
```

# Homework Exercise
Write a program that for given value of variable ‘height’ will print out the right-half of a pine tree to the console.

- The tree starts with “I” on the top and ends with “M” on the bottom. 
- The tree is built from “X” and “Y” characters one after another

For example, for an `height` of 6 it will print:

```
I
XY
XYX
XYXY
XYXYX
M
```

## Solution
```java
private static void tree (int height) {
    if (height < 3) {
        System.out.println("A tree must have a height of at least 3");
    }

    System.out.println("I");
    String treeLine = "X";
    int effectiveHeight = height - 2;
    for (int i=0; i<effectiveHeight; i++) {
        treeLine += (i%2 == 0) ? "Y" : "X";
        System.out.println(treeLine);
    }
    System.out.println("M");
}
```