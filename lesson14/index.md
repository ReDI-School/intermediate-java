---
title: Exception
nav_order: 14
has_children: true
---

# Lesson 14: Exception

## Goals

- Learn what are exceptions.
- Learn how to handle exceptions.
- Know common java exceptions.
- Define custom exceptions
- Use custom exception to control program error flow

## Exceptions

Definition of an exception:
> An exception is an unexpected event, which occurs during the execution of a program that disrupts the normal flow of the program’s instructions.

Examples:

1: You have an app to send messages between users, what happens when the internet is down? how does the app handle that?.

2: Your program is reading data from a file and suddenly the file is deleted by a user. How will your program react?

## Handling Exceptions
Handling exception is about detecting when something went wrong and act on it. We don't want our program to just crash or freeze, that would be a bad user experience.

Following the example we gave above:

1: The app handles the network down exception and shows an error message to the user or the app tries to send the message when the internet is back.

2: The program stops when the file is deleted and shows an error to the user.

### Checked Exceptions
Definition:
> A checked exception is a type of exception that must be either caught or declared in the method in which it is thrown.

Example: FileNotFoundException is a checked exception. The following code will not compile as we either need to handle the exception or declare it in the method.
```java
  void readFile(String fileName) {
    FileReader fr = new FileReader(fileName);
  }
```

#### Handle the expcetion:
```java
void readFile(String fileName) {
  try {
      FileReader fr = new FileReader(fileName);
  } catch (FileNotFoundException e) {
      System.out.println("File not found");
  }
}
```

#### Declare the expcetion in the method:
```java
void readFile(String fileName) throws FileNotFoundException {
  FileReader fr = new FileReader(fileName);
}
```

### Runtime Exceptions
Definition:
> A runtime expcetion is a type of exception that happens during the runtime of the program and causes a crash to the program.

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

### Handling exceptions

* Let's see how we can check if the user provided us with a number or not.
  ```java
  Scanner scanner = new Scanner(System.in);
  try {
      String userInput = scanner.nextLine();
      Integer.parseInt(userInput);
  } catch (NumberFormatException nfe) {
      // Here it mean the use did not provide something convertable to a number
      System.out.println("Sorry: You need to provide a number");
  }
  ```

* Here is an example of trying to read a file that does not exist.
  ```java
  try {
    FileReader fr = new FileReader("/file_do_not_exist");
    // ...
  } catch (FileNotFoundException e) {
    System.out.println("File do not exist");
  }
  ```

### Input Validation

We can see that when we require the user's input, it is not that handy to detect wrong input using exception, it would be nice to detect that before and ask the user to give valid input. This where input validation come into play.

```java
Scanner scanner = new Scanner(System.in);
String userInput = scanner.nextLine();
while(!userInput.matches("[0-9]+")) {
    System.out.println("Please provide a number");
    userInput = scanner.nextLine();
}
int number = Integer.parseInt(userInput);
System.out.println("You have entered: " + number);
```

## Custom exceptions
Every now and then, the exceptions defined by Java are not enough. We want to define our own exceptions.
In order to do so, we can just inherit from Exception for checked exceptions or from RuntimeException. 
In order to set a specific message or a specific root cause, we can overwrite the constructors of Exception/RuntimeException.
```java
public class MyException extends Exception {

}

public class MyRuntimeException extends RuntimeException {

}

public class Service { 
  public void doSth() throws MyException {
    throw new MyException();
  }

  public void doSth2() throws Exception {
    throw new MyException();
  }

  public void doSth3() {
    throw new MyRuntimeException();
  }
}
```

## Exercice
Write a dateValidator method that accept a string as parameter and return true if the string is in the format `DD/MM/YYYY` otherwise it returns false.

## Custom exceptions 1 
Define a method `checkPhoneNumber` which will be used to check a phone number and throw a custom checked exception if the phone number is not valid. 
A phone number is valid if:
- Length is exactly 14
- The first character is +
- All the other characters are numerical digits

In your main method, use a Scanner to get a phone number input, and use the method checkPhoneNumber to validate the input.

## Custom exceptions 2 - Rock, Paper, Scissors
- Rock beats Scissor
- Scissor beats Paper
- Paper beats Rock

The user enters one of three options (R, P, or S) and the computer picks one of the three options at random and the program should print who won and how many rounds each person has won so far e.g:
```
Round #10 - Computer wins!
You: 4
Computer: 6
```

If the user enters the wrong option throw a custom exception that forces the application to crash.

## Homework
We would like to implement a simple calculator that does division. The user has to provide us with 2 numbers x & y, then we print the result of x devided by y.
- Implement a function to read user's input.
- Parse user's input to number
- Print the result of division (PS: it is not possible to divide by 0)

Bonus
- Add the possibility to handle more than one operation in your calculator, for example addition and the user have to choose which operation to apply. 