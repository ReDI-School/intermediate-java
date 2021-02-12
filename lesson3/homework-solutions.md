---
title: "Homework Solutions"
nav_order: 3
parent: Git
nav_exclude: true
---

# Exercise 1

Write a Java Program that finds a minimum value in the given array of integers. 
Add a method to find a maximum value. 
Add a method to find an average. 
Can you do it in 1 loop?

## Solution
```java
public class Task1 {

    public static void main(String[] args) {
        int[] array = {1, 2, 3, 100, -1, 800};

        System.out.println("Min value: " + minValue(array));
        System.out.println("Max value: " + maxValue(array));
        System.out.println("Avg value: " + avgValue(array));

        calculateAndPrintStats(array);
    }

    private static int minValue(int[] array) {
        int min = Integer.MAX_VALUE;

        for (int i = 0; i < array.length; i++) {
            if (array[i] < min) {
                min = array[i];
            }
        }
        return min;
    }

    private static int maxValue(int[] array) {
        int max = Integer.MIN_VALUE;

        for (int i = 0; i < array.length; i++) {
            if (array[i] > max) {
                max = array[i];
            }
        }
        return max;
    }

    private static double avgValue(int[] array) {
        int sum = 0;

        for (int i = 0; i < array.length; i++) {
            sum += array[i];
        }
        return sum / array.length;
    }

    private static void calculateAndPrintStats(int[] array) {
        int sum = 0;
        int min = Integer.MAX_VALUE;
        int max = Integer.MIN_VALUE;

        for (int i = 0; i < array.length; i++) {
            sum += array[i];
            if (array[i] < min) {
                min = array[i];
            }
            if (array[i] > max) {
                max = array[i];
            }
        }

        System.out.println("Print all statistics: ");
        System.out.println("Min value: " + min);
        System.out.println("Max value: " + max);
        System.out.println("Avg value: " + sum / array.length);
    }
}
```

# Exercise 2

Write a Program that checks that a given string is a palindrome. 
A string is Palindrome if position of each character remain the same in case even string is reversed. 
For example 'MADAM' is a palindrome string as position of each character remain same even if string 'MADAM' is reversed.

## Solution
```java
public class Task2 {

    public static void main(String[] args) {
        System.out.println(isPalindrome("MADAM"));
        System.out.println(isPalindrome("JAVA"));
    }

    private static boolean isPalindrome(String str) {
        int i = 0, j = str.length() - 1;

        // While there are characters to compare
        while (i < j) {

            // If there is a mismatch
            if (str.charAt(i) != str.charAt(j))
                return false;

            // Increment first pointer and
            // decrement the other
            i++;
            j--;
        }

        return true;
    }
}
```

# Exercise 3 
Vowels counter
Write a Java method to count all vowels (English Alphabet) in a string.

- Test Data: Input the string: this is a String.
- Expected Output: Number of  Vowels in the string: 4

- Test Data: Input the string: Are you checking Upper case?
- Expected Output: Number of  Vowels in the string: 10

## Solution
```java
public class Task3 {

    public static void main(String[] args) {
        System.out.println(countVowels("this is a String"));
        System.out.println(countVowels("Are you checking Upper case?"));
    }

    private static int countVowels(String str) {
        int count = 0;
        String checkStr = str.toLowerCase();
        for (int i = 0; i < str.length(); i++) {
            char ch = checkStr.charAt(i);
            if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
                count++;
            }
        }
        return count;
    }
}
```

# Exercise 4 
Given an array of Strings, find the longest String in the array.
Add a method to find the longest word in the sentence, assume that input has only english alphabet and spaces

Can you reuse the first method in the second method?

## Solution 
```java
public class Task4 {

    public static void main(String[] args) {
        System.out.println(longestWord("What is the longest word in this sentence"));
        System.out.println(longestWord("What about this"));
    }

    private static String longestWord(String sentence) {
        String[] words = sentence.split(" ");
        return longestWord(words);
    }

    private static String longestWord(String[] words) {
        int longest = 0;
        int longestSize = words[0].length();

        for (int i = 1; i < words.length; i++) {
            if (longestSize < words[i].length()) {
                longestSize = words[i].length();
                longest = i;
            }
        }

        return words[longest];
    }
}
```

# Exercise 5 
Write a program that calculates the factorial of a positive integer n, factorial is the product of all positive integers less than or equal to n: 
For example, The value of 0! is 1, according to the convention for an empty product
4! = 1 * 2 * 3 * 4 = 24

## Solution 
```java
public class Task5 {

    public static void main(String[] args) {
        System.out.println(factorial(4));
        System.out.println(factorial(8));
    }

    private static long factorial(int n) {
        long result = 1;

        for (int i = 1; i <= n; i++) {
            result *= i;
        }

        return result;
    }
}
```