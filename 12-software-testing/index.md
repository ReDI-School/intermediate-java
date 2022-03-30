---
title: 12 - Unit Testing
nav_order: 13
has_children: true
nav_exclude: true
---

# Lesson 12: Unit Testing

## Goals
- Learn about software testing in general
- Deep dive into Unit tests - what is the purpose of Unit tests
- Learn about libraries that helps you to write Unit tests

## Libraries
- [JUnit5](https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-api/5.7.0)

## Slides

[Google Slides](https://docs.google.com/presentation/d/e/2PACX-1vSYCIArENldqw6a04i1WIcVvLXwPVr3vtNvc5AQaaVtkSgiA_HhUU5GQAkWBfAarXYF6rXnSvXEm4cU/embed)

## Exercises

### Exercise 1
Given the following operations, write unit tests to make sure they work as expected
Write test that test the behavior in the happy case and test that test exceptional behaviors (i.e. dividing by zero).

```java
public class Operations {

    public int divide(int x, int y) {
        return x / y;
    }

    public int multiply(int x, int y) {
        return x * y;
    }

    public int sum(int x, int y) {
        return x + y;
    }

    public int difference(int x, int y) {
        return x - y;
    }
}

```

### Exercise 2
Write a program that checks if a word or a phrase is palindrome using TDD method. 

Hint: A word or a phrase is a **palindrome** if it reads the same backward as forward i.e. `mom`, `madam`, `reace car`, `radar`, `level`, `Was it a car or a cat I saw`

## Additional Resources

 - [Junit Tutorial - tutorialpoint](https://www.tutorialspoint.com/junit/index.htm)
 - [Junit Tutorial - guru99](https://www.guru99.com/junit-tutorial.html)
 - [JUnit5 User Guide](https://junit.org/junit5/docs/current/user-guide/)
 - [Tests naming conventions](https://dzone.com/articles/7-popular-unit-test-naming)
