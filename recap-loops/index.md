---
title: "2 - Recap loops"
nav_order: 1
has_children: false
nav_exclude: false
---

# Lesson 2: Recap loops

## Goals
* Intro git & github classroom
* Recap `for`
* Recap `while`
* Recap `do` ... `while`
* Recap `for` each
* Code, code, code 🤩

## Recap & Assignment check
Let's look into the assignment from lesson 1.

## for loops
For loops are the most commonly used loops in Java.

Their structure is as follows:
```java
for (<INITIALIZATION>; <CONDITION>; <INCREMENT>) {
    // <CODE TO EXECUTE>
}
```

For loops are usually used to run `<CODE TO EXECUTE>` a given amount of times.
They are using an `INITIALIZATION` statement which is run exactly once at the beginning, 
a `CONDITION` statement which is run before each iteration and 
an `INCREMENT` statement which is run after each iteration.
For loops are executed until `CONDITION` evaluates to false. If they are false from the beginning,
the code will never be executed.

Example:
```java
public class SimpleForLoopExample {

    public static void main(String[] args) {

        for (int i = 0; i < 10; i++) {
            System.out.println("i is " + i);
        }
    }
}
```

## while loops
While loops are usually used to run code until a condition changes.

Structure:
```java
while (<CONDITION>) {
    <CODE TO EXECUTE>
}
```
While the `CONDITION` evaluates to true, the code will be executed. Usually the `CODE TO EXECUTE` has
an impact on the `CONDITION`, e.g. modifies it's outcome.

Example:
```java
import java.util.Scanner;

public class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        int numberToGuess = 19;
        boolean numberGuessed = false;
        int neededTries = 0;

        while (!numberGuessed) {
            neededTries++;
            System.out.println("Please guess a number between 0 and 20");

            int guessedNumber = input.nextInt();

            if (guessedNumber == numberToGuess) {
                numberGuessed = true;
            }
        }

        System.out.println("Congratulations! You needed " + neededTries + " tries to guess the given number!");
    }
}
```

## do while loops
Do while loops are the least used ones. Unlike while loops, they guarantee at least one code execution.

Structure:
```java
do {
    <CODE TO EXECUTE>
} while(<CONDITION>);
```
The `CODE TO EXECUTE` will first be executed once, then the `CONDITION` will be evaluated.
This is repeated until the `CONDITION` evaluates to false.

Example:
```java
import java.util.Scanner;

public class NumberGuessingGame {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        int numberToGuess = 19;
        boolean numberGuessed = false;
        int neededTries = 0;
        
        do {
            neededTries++;
            System.out.println("Please guess a number between 0 and 20");

            int guessedNumber = input.nextInt();

            if (guessedNumber == numberToGuess) {
                numberGuessed = true;
            }          
        } while (!numberGuessed);

        System.out.println("Congratulations! You needed " + neededTries + " tries to guess the given number!");
    }
}
```

## for each loops
For each loops are like normal for loops. However, a common case is to iterate over a whole list/a whole array.

Structure:
```java
for (type var : array) { 
    <CODE TO EXECUTE>
}
```
This will iterate of the whole array and assign each value once to the variable var.

Example:
```java
for (int number : numbers) {
    System.out.println(number);
}
```
The above prints the same results as the following for loop below:
```java
for (int i=0; i<numbers.length; i++) {
    System.out.println(numbers[i]);
}
```

A for each loop is quite common when you handle lists/arrays.

## break and continue
Sometimes it is needed to skip certain items or to stop the loop prematurely.
In order to do so, we can use the `continue` (skip current iteration) and the `break`
(stop the whole loop) keywords.

Example break:
```java
for (int number : numbers) {
    if (number == 3) {
      break;
    }
    System.out.println(number);
}
```

Example continue:
```java
for (int number : numbers) {
    if (number == 3) {
      continue;
    }
    System.out.println(number);
}
```


## Exercises

### Exercise 1: Sum of an array.

Write a method that takes an array of integers and returns the sum of the elements of that array. Test it by passing in a few `hardcoded` inputs and printing the output to the console. 
Examples:
`[1,2,3,4] `-> 10
`[]` -> 0
`[1]` -> 1

### Exercise 2: Average

The average of a list of numbers is the sum of those numbers divided by the number of elements. Write a method that takes an array of integers and returns the average. Make sure to reuse the sum method that you have written for Exercise 1.
Examples:
`[1,2,3,4]` -> 2.5
`[10,10,10]` -> 10
`[]` -> null
integers and returns the average. Make sure to reuse the sum method that you have written above.

### Exercise 3: Count the `char`

Write a method that takes a `String` and a `char` and returns the number of times you can find that character in that string. Examples:
`"Hello!", 'l'` -> 2
`"Banana", 'a'` -> 3
`"ReDI", 'a'` -> 0 
string.


## Homework

### Graded: Simple Multiplication Table

This exercise is available in [Github classroom assignment here](https://classroom.github.com/a/wJEsXx7a)

- Read a single number with [Scanner](https://beginnersbook.com/2017/09/java-program-to-read-integer-value-from-the-standard-input/)
- Print the multiplication table of the number from 1 until 10

Example:
```
Input: 2
Output:
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
2 x 4 = 8
2 x 5 = 10
2 x 6 = 12
2 x 7 = 14
2 x 8 = 16
2 x 9 = 18
2 x 10 = 20
```

### Graded: Dividable numbers

This exercise is available in [Github classroom assignment here](https://classroom.github.com/a/KOXYDafF)

- Read two numbers with Scanner
- Print each number from 1 to the first entered number that is dividable without remainder by the second number (e.g. 6 is dividable by 3 without remainder as 6 / 3 is 2 with remainder 0, but 6 is not dividable by 4 without remainder as 6 / 4 is 1 with remainder 2)

Example:
```
First: 16
Second: 5
Output:
5 is dividable by 5
10 is dividable by 5
15 is dividable by 5
```


### Multiplication table II

- Write a Java program that reads from the user a value n and prints an n by n multiplication table.
- When run, your program should look as follows:

Example:
```
Dear user, please enter a number, and I will compute a multiplication table for you: 7

You typed in 7. Here is the multiplication table: 

 1  2  3  4  5  6  7
 2  4  6  8 10 12 17
 3  6  9 12 15 18 21
 4  8 12 16 20 24 28
 5 10 15 20 25 30 35
 6 12 18 24 30 36 42
 7 14 21 28 35 42 49

Happy? (y/n)
```

### Bank Account

- Your program should start with a variable holding the current money on a user’s bank account (start with e.g. 100)
- The user should now enter an amount, and he should enter if he wants to deposit to his account or if he wants to withdraw (e.g. 1 for deposit, 2 for withdrawal)
- The variable holding money on the account should be updated accordingly, and the current money should be printed.
The program should run and let the user interact until the money on his account is zero or less.

Example:
```
Current money on account: 100
Enter amount:
30
Enter 1 for deposit, 2 for withdrawal
2
Current money on account: 70
Enter amount:
60
Enter 1 for deposit, 2 for withdrawal
2
Current money on account: 10
Enter amount:
20
Enter 1 for deposit, 2 for withdrawal
1
Current money on account: 30
Enter amount:
30
Enter 1 for deposit, 2 for withdrawal
2
You have no money left, program stopped ...
```

## Materials
- https://www.javatpoint.com/java-for-loop
