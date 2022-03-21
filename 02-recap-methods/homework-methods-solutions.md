---
title: "Assignment Solutions"
nav_order: 0
parent: "02 - Recap Methods"
nav_exclude: false
---
# Solutions for Class 02 (Methods Recap)
Here are some possible solutions for the exercises. Please keep in mind all exercises have multiple solutions, and they are all correct if they make the tests pass.

## Exercise 1 - Prettify
Prettifying a string means to return the string with the characters that appear side by side separated by a character chosen by the user.

### Solution

```java
public static String prettify(String text, char separator) {
    StringBuilder builder = new StringBuilder();
    for(char c : text.toCharArray()) {
        builder.append(c);
        builder.append(separator);
    }
    builder.deleteCharAt(builder.length()-1);
    return builder.toString();
}
```

## Exercise 2 - Count the character
Write a method that takes a `String` and a `char` and returns the number of times you can find that character in that string.
Note that the counting should be **case-insensitive**

### Solution

```java
public static int countCharacter(String text, char search) {
    int count = 0;
    for(String c : text.split("")) {
        if(c.equalsIgnoreCase(String.valueOf(search))) {
            count++;
        }
    }
    return count;
}
```

## Exercise 3 - Find minimum value
Write a method that takes three numbers and returns the minimum number of the three.

### Solution

```java
public static int getMin(int num1, int num2, int num3) {
    return Math.min(num1, Math.min(num2, num3));
}
```

## Exercise 4 - Find maximum value
Write a method that takes three numbers and returns the maximum number of the three

### Solution

```java
public static int getMax(int num1, int num2, int num3) {
    return Math.max(num1, Math.max(num2, num3));
}
```