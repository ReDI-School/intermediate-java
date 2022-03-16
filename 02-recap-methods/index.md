---
title: "02 - Recap Methods"
nav_order: 2
has_children: false
nav_exclude: false
---

# Lesson 2: Recap methods

## Goals
* Intro Git and GitHub
* Recap method `signature`, `arguments` and `return` value
* Code, code, code 🤩

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
We can see that we have used the `public`, `static` and `void` keywords before the method name. We will look at their role in Java in this lesson. For the aforementioned keywords, they mean this:

- `public` serves as a access modifier. It means the method can be accessed from anywhere.
- `static` here means this method belongs to the general class of Main and not to a specific instance of Main. We can therefore call the method from `Main` without creating an actual instance of `Main`. That would look like this: `Main.foo()`.
- `void` means this method doesn't return a value. Methods can return a single value in Java and it has to be defined in the method declaration. However, you can use return by itself to exit the method.
- This method takes as argument an array of `String`.

A method is structured as follow:

```java
public class Main {
    <modifiers> <return type> methodName(<arguments list>){
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

## Method Visibility with Access Modifiers

- `private`: Can only be accessed within the owning class
- `protected`: Can only be accessed within the owning class, classes within the same package and any sub-class of the owning class
- `public`: Can be accessed from anywhere.
- No modifier (default): Can only be accessed within the class and classes within the same package


## Static Methods

Static methods like the `main` method belongs to the class and you do not need an instance of the class to invoke it. If you define a static method call `myMethod` in a class called `MyClass`. You can invoke that method by using the class in the following way:

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

A non-static method belongs to an instance of the class. To invoke or call a non-static method, you must have and use an instance of the class. **What is an instance of a class?**

If you define a non-static method call `myMethod` in a class called `MyClass` you can invoke that method in the following way:

```java
new MyClass().myMethod(...);
```

Here, `new MyClass()` is a new instance of the class `MyClass`. You will learn more about this and Object Oriented Programming later in the course.

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


## [More exercises](https://classroom.github.com/a/v8BdVG8B)

Follow the [link](https://classroom.github.com/a/v8BdVG8B) and accept the assignment to be able to see the exercies and submit your solution. 

## [Homework Assignment](https://classroom.github.com/a/2LRYDkZ_)

Accept the [assignment](https://classroom.github.com/a/2LRYDkZ_) and solve it on your own. Reach out whenever you are stuck and good luck!
