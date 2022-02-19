---
title: "01 - Introduction to the Intermediate Java course"
nav_order: 1
nav_exclude: false
has_children: true
---

# Lesson 1: Introduction

## Goals of this class
* Getting to know each other
* Get familiar with schedule, attendance, tools
* Course introduction
* Check required software (Java & Intellij Idea)
* Iteration control structures recap (loops)
* Do some basic Java exercises 🤩

### General info
* 📓 Course certificate only after minimum 80% attendance
* 💨 We don’t show up late to class (and inform otherwise)
* 🏝 We take a 10 minutes break in the middle of the class
* 🕺🏻 We are here for you! Always ask questions if something is not clear.
* 🚀 Never forget the feedback!
* 🕸 [Web](https://redi-school.github.io/intermediate-java), [Previous Semesters](https://redi-j2.netlify.com)
* 🐦 Slack: #22s_programming_java
* 🎓 We will have a Project at the end of the course!

### Content of this course

We planned to cover the following topics over the course of the semester. However, it is
important to note that this is not set in stone. Depending on the progress of the class as a whole,
we may cover a bit more or a bit less. It is nevertheless most important that we work and progress
as a group whilst helping one another grow.

* The Java language
* Data structures
* Object Oriented Programming
* Exceptions
* Libraries
* Build Tools
* Unit Testing 
* File IO

### Which tools we will be using?

All tools we use are described in the Initial Setup page.

At this point, we expect you have all of them installed and running, but if you didn't make it ask the teachers on Slack.

*Important:* The focus of this course is not teaching you the tools, so we will show you only the basics, along with the content.


## Iteration Control Structures Recap 
Let's review what we learned in the _Introduction to Java_ course.

### FOR loops
For loops are the most commonly used iteration control structures in Java (and other languages).

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

### WHILE loops
While loops are usually used to run code until a condition is not met anymore.

Structure:
```java
while (<CONDITION>) {
    <CODE TO EXECUTE>
}
```
While the `CONDITION` evaluates to true, the code will be executed. Usually the `CODE TO EXECUTE` has
an impact on the `CONDITION`, e.g. modifies its outcome.

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

### DO-WHILE loops
Do-while loops are the least used ones. Unlike while loops, they guarantee at least one code execution.

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

## Exercises

### Exercise 1: Multiples of 3 or 5

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Find the sum of all the multiples of 3 or 5 below 1000.

[Original Source](https://projecteuler.net/problem=1)

### Exercise 2: Smallest Multiple

2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder.

What is the smallest positive number that is _evenly divisible_ by all the numbers from 1 to 20?

[Original Source](https://projecteuler.net/problem=5)

## Supporting Materials:
- [Intellij Idea. First Java Application Tutorial](https://www.jetbrains.com/help/idea/creating-and-running-your-first-java-application.html)
- [The Java Tutorials (from Oracle)](https://docs.oracle.com/javase/tutorial/)
- [W3Schools Java Tutorial](https://www.w3schools.com/java/)
- [O'Reilly Programming Podcasts](https://www.oreilly.com/topics/oreilly-programming-podcast)
