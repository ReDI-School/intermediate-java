---
title: "10 - Error Handling & Exceptions"
nav_order: 11
has_children: false
nav_exclude: true
---

# Lesson 10: Error Handling & Exceptions

## Goals
- Identify what can go wrong in your applications
- Understand how to use Java Exceptions to handle errors
- Know the differences between checked and unchecked exceptions
- Use your own custom exceptions to elegantly handle errors

## Identify what can go wrong in your applications 
When we write code, we often start with an idea of what happens if everything goes well
Let's say we write an application that asks the user to enter their instagram name and then prints the date when they uploaded their last picture:
- The user enters their name and presses enter
- We send a request to the Instagram API and ask for the most recent picture this user uploaded.
- Instagram sends us back a URL to the picture & the time it was uploaded.
- We print the upload time.
- Everyone is happy.


**Question: What can you think of that could go wrong here?**

When trying to write good code, you should **always** think about what could go wrong. 
When we talk about something going wrong we don't talk about **if** it will happen - we talk about **WHEN** it will happen. If it **can** go wrong, it **will** go wrong :)
This is such a fundamental part of software development that Java provides you a built-in way to elegantly handle these error scenarios: **Exceptions**.

Definition of an exception:
> An exception is an unexpected event, which occurs during the execution of a program that disrupts the normal flow of the program’s instructions.

Examples of exceptions:

1. You have an array of 3 elements, what happens when your program tries to print the 4th element in the array? how does the program handle that? 
2. Your program is parsing user inputs to integer, What happens when user enter text instead of numbers? how will your program react?

## Understand how to use Java Exceptions to handle errors

Handling exceptions is about detecting when something went wrong and acting on it. Usually, we don't want our program to just randomly crash. 
We either want to handle the error, or at the very least, provide a proper error message to the user and tell them what went wrong.

Following the example we gave above:

1. Your program should display an error message informing the user that element 4 can't be found because the array contains only 3 elements, may be prompt the user to add another element index to be printed
2. Your program should display an error message informing the user to enter data in the valid format


See the following code as an example, what could go wrong here?

```java
public class Main {
  public static void main(String[ ] args) {
    int[] myNumbers = {1, 2, 3};
    System.out.println(myNumbers[4]); // error!
  }
}
```

Don't scroll down yet - Take a minute to think about it...

-----------------

When we run the above code you get the following:

```java
    Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 4 out of bounds for length 3
```


A better version to avoid this error function would be:

```java
public class Main {
  public static void main(String[ ] args) {
    int[] myNumbers = {1, 2, 3};
    try {
      int index=4;
      System.out.println(myNumbers[index]); // invalid index
      System.out.println("Valid Index!");
    }catch (ArrayIndexOutOfBoundsException e){
      System.out.println("Error: myNumbers array contains only 3 elements, index 4 is out of bounds");
    }
  }
}
```

Note the `try` and `catch` keywords. We wrap the code that can cause an exception in a `try { ... }` block and add a `catch(ArrayIndexOutOfBoundsException e) {...}` after it.
Your application will start by executing the code in the `try` block: `System.out.println(myNumbers[4])`

If the exception happens - the index is out of bounds - the application will leave the `try` block immediately, ignore the rest of the code in the `try` block and enter the `catch` block. 
Then, it will execute the code written in the catch block and print `Error: myNumbers array contains only 3 elements, index 4 is out of bounds` to the console.

If the exception does not happen - the index is within the bounds - the application will continue with the rest of the `try` block and print `Valid Index!` to the console.
It will **skip** the catch block entirely.


Let's look at the second part of `catch (ArrayIndexOutOfBoundsException e)`. What is this `ArrayIndexOutOfBoundsException e`?
Exceptions in Java are classes! Just like the classes we looked at in the previous sessions.

For our ArrayIndexOutOfBoundsException example, this is the code that actually throws the exception:

Within the catch block, you gain access to the exception object and all it's properties, including the error message.

It can be used like this:
```java
try {
    System.out.println(myNumbers[4]); // invalid index
    System.out.println("Valid index");
}catch (ArrayIndexOutOfBoundsException e){
    System.out.println(e.getMessage());
}
```

Not the `e.getMessage()` in the catch block - it will return the string `Index 4 out of bounds for length 3`.


### Checked and unchecked exceptions
Definition:
> A checked exception is a type of exception that must be either caught or declared in the method in which it is thrown.

The purpose of it is to force the developer to consider **expected** cases they might not be aware of.

Example: IOException is a checked exception. The following code will not compile unless we either handle the exception or declare it in the method.


#### Handle the exception:
```java
public static void main(String[ ] args) {
    int firstNum, secondNum, result;
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    try {
        System.out.println("Enter a first number:");
        firstNum = Integer.parseInt(br.readLine());
        System.out.println("Enter a second number:");
        secondNum = Integer.parseInt(br.readLine());
        result = firstNum * secondNum;
        System.out.println("The Result is: " + result);
    } catch (IOException ioe) {
        System.out.println(ioe);
    }
}
```

#### Declare the exception in the method:
Instead of handling this exception directly, we can also propagate it to its caller and let them handle it. This can be useful if how you want to handle it depends on who calls the method.

```java
void readFile(String fileName) throws FileNotFoundException {
  FileReader fr = new FileReader(fileName);
}
```

In this case, you don't decide in `readFile` what to do in case of an exception, but warn whoever calls `readFile` that they have to handle it.

### Runtime Exceptions
Definition:
> A runtime exception is a type of exception that happens during the runtime of the program and causes a crash to the program.

Two of the most common types of runtime exceptions are `NullPointerException` and `IndexOutOfBoundsException`

## Exceptions in practice
### Getting to know exceptions

* We will try to get a user's input from the console. In order to achieve this we need to use a Scanner. Then let's try to convert the user's input to an Integer.

  ```java
  Scanner scanner = new Scanner(System.in);
  String userInput = scanner.nextLine();

  // this will throw an exception if user input is not convertable to an integer
  Integer.parseInt(userInput);
  ```

* Let's see what happens when we try to access an element that do not exist in a List

  ```java
  List<String> emptyList = new ArrayList<>();

  // this will throw an exception in any case!
  emptyList.get(5);
  ```

* Let's see one of the common Java exception `NullPointerException`
```java
  public static void main() {
    String x= null;
    printMyThing(x);
  }

  private static void printMyThing(String s) {
      System.out.println(s.toLowerCase());
  }
```

## Custom exceptions
Every now and then, the exceptions defined by Java are not enough. We want to define our own exceptions.
In order to do so, we can just inherit from `Exception` class for checked exceptions or from `RuntimeException` class for runtime exceptions.
In order to set a specific message or a specific root cause, we can overwrite the constructors of Exception/RuntimeException.

```java
public class MyException extends Exception {

}

public class MyRuntimeException extends RuntimeException {

}

public class Service {

  //Checked Custom Exception
  public void doSth() throws MyException {
    throw new MyException();
  }

  //Checked Generic Exception
  public void doSth2() throws Exception {
    throw new MyException();
  }

  //Unchecked Custom Exception
  public void doSth3() {
    throw new MyRuntimeException();
  }
}
```

## Recap
 - Exceptions are a tool to make expected misbehaviour visible and to allow other parts of the code to handle it explicitly
 - Exceptions are triggered ("thrown") with `throw new <ExceptionClass>`.
 - To handle an exception explicitly, we wrap the method that throws the exception in a try/catch block and use the catch section to handle it.
 - There are a bunch of predefined Exception types in Java that can be used (e.g. `DateTimeException`, `FileNotFoundException`, `NumberFormatException`, ...)
 - A custom exception can be implemented with a class that extends either `Exception` or a subclass of it, like `RuntimeException` or one of the predefined ones.
 - To make it visible that a method could raise a certain exception, we append `throws <ExceptionName>` to the method definition. This will force code that calls this method to explicitly handle it.

## When NOT to use exceptions
Use exceptions only for exceptional situations, e.g. 
- a file should be there, but isn't
- the user should put in a number, but puts a name
- you want to call the instagram API but you have no internet connection.

Do not use it for anything else. It is considered bad practice - Exceptions complicate the flow of your application because you jump between functions and blocks before they complete.

## Exercises

## Exercise 1
Write a dateValidator method that accept a string as parameter and returns nothing if the string is in the format `DD/MM/YYYY` otherwise it raises a `DateTimeException` as a checked exception.

## Exercise 2: Replace the `DateTimeException` in Exercise 1 with a custom Exception.

# Assignment

## [Rock, Paper, Scissors Game with Error Handling](https://classroom.github.com/a/BAPYLA8Z ){:target="_blank"}

#### Follow the [link](https://classroom.github.com/a/BAPYLA8Z ){:target="_blank"}, accept and download the assignment from GitHub Classroom
