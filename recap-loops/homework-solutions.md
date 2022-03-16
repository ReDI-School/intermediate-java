---
title: "Assignment Solutions"
nav_order: 2
parent: "2 - Recap loops"
nav_exclude: false
---

### Exercise 1: Sum of an array.

Write a method that takes an array of integers and returns the sum of the elements of that array. Test it by passing in a few `hardcoded` inputs and printing the output to the console.

Examples:
```shell
[1,2,3,4] -> 10
[] -> 0
[1] -> 1
```

Here is a solution with a for each type of loop:

```java

public class SumOfArrayExercise {

  public static int sumArray(int[] arr) {
    int result = 0;
    for (int elm: arr) {
      result += elm;
    }
    return result;
  }

  public static void main(String[] args) {
    int[] testArr1 = {1, 2, 3, 4};
    System.out.printf("Test with a simple array initialized with 4 elements should return 10, and returns '%d'%n", sumArray(testArr1));

    int[] testArr2 = {};
    System.out.printf("Test with an empty array should return 0, and returns '%d'%n", sumArray(testArr2));

    int[] testArr3 = {1};
    System.out.printf("Test with a single element array should return 1, and returns '%d'%n", sumArray(testArr3));
  }

}
```

Note that this could have been done with any type of loop. However, a for each loop here comes handy since we are receiving an array as an argument.

### Exercise 2: Average

The average of a list of numbers is the sum of those numbers divided by the number of elements. Write a method that takes an array of integers and returns the average. Make sure to reuse the sum method that you have written for Exercise 1.

Examples:
```shell

[1,2,3,4] -> 2.5
[10,10,10] -> 10
[] -> 0
```

Solution:

```java

public class AverageOfArrayExercise {

  public static int sumArray(int[] arr) {
    int result = 0;
    for (int i = 0; i < arr.length; i++) {
      result += arr[i];
    }
    return result;
  }

  public static double averageArray(int[] arr) {
    if (arr.length == 0) {
      return 0;
    }
    int sum = sumArray(arr);
    return (double) sum / arr.length;
  }

  public static void main(String[] args) {
    int[] testArr1 = {1, 2, 3, 4};
    System.out.printf("Test with a simple array initialized with 4 elements should return '2.5', and returns '%.1f'%n", averageArray(testArr1));

    int[] testArr2 = {};
    System.out.printf("Test with an empty array should return '0.0', and returns '%.1f'%n", averageArray(testArr2));

    int[] testArr3 = {1};
    System.out.printf("Test with a single element array should return '1.0', and returns '%.1f'%n", averageArray(testArr3));
  }

}
```

### Exercise 3: Count the `char`

Write a method that takes a `String` and a `char` and returns the number of times you can find that character in that string.

Examples:
```shell
`"Hello!", 'l'` -> 2
`"Banana", 'a'` -> 3
`"ReDI", 'a'` -> 0 
```

Solution:

```java

public class CountCharExercise {

  public static int countChars(String word, char repeatChar) {
    int count = 0;
    char repeatCharLowerCased = Character.toLowerCase(repeatChar);
    char[] charsArr = word.toCharArray();
    for (char chr: charsArr) {
      char lowerCased = Character.toLowerCase(chr);
      if (lowerCased == repeatCharLowerCased) {
        count++;
      }
    }
    return count;
  }

  public static void main(String[] args) {
    System.out.printf("Test with string 'hello' and 'l' should return '2', and returns '%d'%n", countChars("hello", 'l'));

    System.out.printf("Test with string 'Banana' and 'a' should return '3', and returns '%d'%n", countChars("Banana", 'a'));

    System.out.printf("Test with string 'ReDi' and 'a' should return '0', and returns '%d'%n", countChars("ReDI", 'a'));
  }

}
```

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

Solution:

```java

public class MultiplicationTable {

  /**
   * Reads input from console/terminal
   */
  public static int getInputFromStandardIn() {
    Scanner scanner = new Scanner(System.in);
    return scanner.nextInt();
  }

  public static void printMultiplicationTable(int input) {
    for (int i = 1; i < 11; i++) {
      int result = input * i;
      System.out.printf("%d x %d = %d%n", input, i, result);
    }
  }

  public static void run() {
    int input = getInputFromStandardIn();
    printMultiplicationTable(input);
  }

  public static void main(String[] args) {
    System.out.println("Testing MultiplicationTable program");
    run();
  }

}
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

Solution:
```java

public class DividableNumbers {

  public static void run() {
    Scanner scanner = new Scanner(System.in);
    int inputNumberOne = scanner.nextInt();

    int inputNumberTwo = scanner.nextInt();
    printDividableNumbers(inputNumberOne, inputNumberTwo);
  }

  public static void printDividableNumbers(int firstNumber, int secondNumber) {
    if (secondNumber == 0 || firstNumber < secondNumber) {
      return;
    }
    for (int i = secondNumber; i <= firstNumber; i++) {
      if (i % secondNumber == 0) {
        System.out.printf("%d is dividable by %d%n", i, secondNumber);
      }
    }
  }

  public static void main(String[] args) {
    System.out.println("Testing DividableNumbers program");
    run();
  }

}
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

```java

public class MultiplicationTableII {

  /**
   * Reads input from console/terminal
   */
  public static int getInputFromStandardIn() {
    Scanner scanner = new Scanner(System.in);
    return scanner.nextInt();
  }

  public static void printMultiplicationTable(int input) {
    for (int i = 1; i <= input; i++) {
      for (int j = 1; j <= input; j++) {
        System.out.printf("%d\t", i * j);
      }
      System.out.println();
    }
  }

  public static void run() {
    int input = getInputFromStandardIn();
    printMultiplicationTable(input);
  }

  public static void main(String[] args) {
    System.out.println("Testing MultiplicationTableII program");
    run();
  }

}
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

Solution:
```java

import java.util.Scanner;

public class BankAccount {

  public static String formatCurrentAmount(int amount) {
    return String.format("Current money on account: %d", amount);
  }

  public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);
    int currentMoneyAmount = 100;

    do {
      System.out.println(formatCurrentAmount(currentMoneyAmount));
      System.out.println("Enter amount:");
      int amount = scanner.nextInt();
      System.out.println("Enter 1 for deposit, 2 for withdrawal");
      int depositOrWithdrawal = scanner.nextInt();
      if (depositOrWithdrawal != 1 && depositOrWithdrawal != 2) {
        System.out.println("Invalid input - only values '1' or '2' are valid");
        continue;
      }
      if (depositOrWithdrawal == 1) {
        currentMoneyAmount += amount;
      } else {
        currentMoneyAmount -= amount;
      }

    } while(currentMoneyAmount > 0);

    System.out.println("You have no money left, program stopped ...");
  }

}
```