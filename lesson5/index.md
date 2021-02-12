---
title: Recap Functions & Methods
nav_order: 5
has_children: true
nav_exclude: true
---

# Lesson 5: Recap Functions & Methods

## Goals
* Recap method `signature`, `arguments` and `return` value
* Recap `recursion`
* Code, code, code 🤩

## Recap & Homework check
Let's look into the homework from lesson 5

## Java Method

in computer programming, a function is a block of code that performs a specific task.
In object-oriented programming, the method is just another name used for function. Methods are bound to a class and they 
define the behavior of a class. In Java, all function definitions must be inside classes.
Let's look at an example of the main method

```java
public class Main {
    public static void main(String[] args){
      //code to execute
    }
}
```

Here, we have created a method named `main` in the class `Main`.
We can see that we have used the `public`, `static` and `void` keywords before the method name.

- `public` - access modifier. It means the method can be accessed from anywhere.
- `static` here means this method belongs to the class Main and not to a specific instance of Main. 
  Which means we can call the method from a different class like that `Main.foo()`.
- `void` means this method doesn't return a value. Methods can return a single value in Java and it has to be defined in 
  the method declaration. However, you can use return by itself to exit the method.
- This method takes as argument an array of `String`.

A method is structured as follow:

```java
public class Main {
    <modifier> <return type> methodName(<arguments list>){
      //code to execute
    }
}
```
To use a method, it should be called. If a method returns a value, it **can** be immediately assigned to a variable when
called. A method that returns nothing i.e. `void` **cannot** be assigned to a variable when called.

The main advantage is code reusability. We can write a method once, and use it multiple times. We do not have to rewrite
the entire code each time. Think of it as, "write once, reuse multiple times". Methods also make code more readable and 
easier to debug. For example, a method named `getSquare()` is so readable that we can know that this method will be calculating 
the square of a number whenever it is called.

## Method visibility

- `private`: Can only be accessed within the owning class
- `protected`: Can only be accessed within the owning class, classes within the same package and any sub-class of the owning class
- `[no-visibilty]`: Can only be accessed within the class and classes within the same package
- `public`: Can be accessed from anywhere.

## Static Methods

Static methods like the `main` method belongs to the class and you do not need an instance of the class to invoke it.
If you define a static method call `myMethod` in a class called `MyClass` you can invoke that method by using the class 
in the following way:

```java
MyClass.myMethod(...)
```

### Example 1:
```java
public class Main {

    public static void print(String name) {
        System.out.println(name);
    }

    public static void main(String[] args){
        print("Java");
    }
}
```

### Example 2:

Here, we have mentioned the return type of the method as int. Hence, the method should always return an integer value.
Also observe that when we called sum the first time, we assigned the return value to a variable `value`, however we did
assign the return value to anything at the second invocation.

```java
public class Main {

    public static int sum(int a,  int b) {
        return a + b;
    }

    public static void main(String[] args){
        int value = sum(5, 1);
        int anotherValue = Main.sum(5, 1);
        sum(5, 1);
    }
}
```

## Non-static Methods

Non-static method belongs to an instance of the class. To invoke or call a non-static method, you must have and
use an instance of the class. **What is an instance of a class?**

If you define a non-static method call `myMethod` in a class called `MyClass` you can invoke that method in the following way:

```java
new MyClass().myMethod(...);
```

Here, `new MyClass()` is an instance of the class `MyClass`. You will learn more about this and Object Oriented 
Programming later in the course.

OR in the following way

```java
MyClass myClass = new MyClass();
myClass.myMethod(...)
```

### Example 1:
```java
public class Main {

    public void print(String name) {
        System.out.println(name);
    }

    public static void main(String[] args){
        print("Java"); // This is wrong and will not compile
        new Main().print("Java"); // This is correct and will compile
    }
}
```

### Example 2:
```java
public class Main {

    public int sum(int a,  int b) {
        return a + b;
    }

    public static void main(String[] args){
        Main main = new Main();
        int value = main.sum(5, 1);
    }
}
```

## [Recursion](https://www.google.com/search?q=recursion)

A recursion occurs when invoking a method and that invocation manages to trigger another invocation of the same
method. Recursion can be obvious and subtle for example:

```java
public class Main {

    public int foo(int a) {
        return foo(a);
    }

}
```

And sometimes it is less subtle and usually involves multiple methods. For example:

```java
public class Main {

    public int foo(int a) {
        return bar(a);
    }

    public int bar(int a) {
        return foo(a);
    }

}
```

A recursion can grow exponentially when there are multiple recursive calls. For example:

```java
public class Main {

    public int foo(int a) {
        return foo(a) + foo(a);
    }

}
```

When using recursion, it is very important to have a terminating point otherwise the call stack will run out of memory and
you will have what is called [`StackOverflowError`](https://stackoverflow.com).

In the exercises for this lesson, you will have an example of a problem that can be solved using recursion.

## Exercises

Note - The methods in this exercises can be static and they can be invoked from the `main` method for testing.

Feel free to name your methods however you like.

### 1 - Prettify

Prettifying a string means to print the string in the standard output with the characters that appear sided by side
separated by a character chosen by the user.

You should write a method that takes a string and the separating character and prettifies the string using the
separating character. In addition make sure to get the separating character from the user via the standard input.

### 2 - Sum of an array.

Write a method that takes an array of integers and returns the sum of the elements of said array.

### 3 - Average

The average of a collection of numbers is the sum divided by the number of elements. Write a method that takes an array of
integers and returns the average. Make sure to reuse the sum method that you have written above.

### 4 - Count the `char`

Write a method that takes a `String` and a `char` and returns the number of times you can find that character in that
string.

### 5 - Min/Max

- Write a method that takes three numbers and returns the minimum number of the three
- Write another method that takes three numbers and returns the maximum number of the three

### 5 - Recursion: Logarithm

Using recursion, write a method that given an integer, it returns the number of digits representing that integer
in base 10 e.g. `f(141) = 3` because `141` has three digits.

### 6 - Recursion: Fibonacci

using recursion, write a method that returns the `n`th fibonacci number given n. The fibonacci numbers are defined as
follows:

```
f(0) = 0
f(1) = 1
f(n) = f(n-1) + f(n-2) for n > 1
```

### 7 - Recursion: Palindrome

Using recursion, write a method that takes a string and returns a boolean indicating if the provided string is a
palindrome or not.

A palindrome is a string that is the same backward and forward e.g. `hannah`, `level`, `madam`, etc..
