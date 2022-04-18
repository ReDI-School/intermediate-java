---
title: "Assignment Solutions"
nav_order: 1
parent: "01 - Introduction to the Intermediate Java course"
nav_exclude: false
---

### Exercise 1: Multiples of 3 or 5
```
If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.
Find the sum of all the multiples of 3 or 5 below 1000.
```

The solution for this exercise is pretty straightforward. Your program should iterate until 999 while summing all numbers that don't have any remainder after dividing them by 3 or 5.

```java
public class Main {

  public static void main(String[] args) {

    int sum = 0;

    for (int i = 1; i < 1000; i++) {
      if (i % 3.0f == 0 || i % 5.0f == 0) {
        sum += i;
      }
    }

    System.out.println("The sum is "+sum); // 233168
  }
}
```

Notice that using a *for* loop is convenient, because you know the amount of times you will have to iterate.

### Exercise 2: Smallest Multiple
```
2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder.
What is the smallest positive number that is _evenly divisible_ by all the numbers from 1 to 20?
```

While there are multiple ways of solving this exercise, official arithmetic solutions (like [this one](https://en.wikipedia.org/wiki/Least_common_multiple)) are more complex than using brute force.

The solution below uses a *while* loop and keep testing numbers until the smallest multiple is found (but it takes a lot of time in slow computers).

```java
public class Main {

  public static void main(String[] args) {

    boolean found = false;
    long number = 1;

    while(!found) {

      boolean remainder = false;

      for (int i = 1; i <= 20; i++) {
        if (((double)number) % i != 0) {
          remainder = true;
          break;
        }
      }

      if(!remainder) {
        found = true;
      }
      else {
        number++;
      }
    }

    System.out.println("The smallest multiple is "+number); // 232792560
  }
}
```
