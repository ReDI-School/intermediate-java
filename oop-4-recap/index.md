---
title: "10 - OOP4 Classes, Abstract Classes & Interfaces Recap"
nav_order: 10 
has_children: false
nav_exclude: false
---

# Lesson 10: OOP4 - Classes, Abstract Classes and Interfaces Recap

## Goals

- Check-in
- Simulation of pull requests reviews
- Practice exercise about abstract classes and interfaces

## Check-in
How is everybody doing?

## Pull-Request review simulator: The "bug sniper"

See if you can detect the issues in the code and propose improvements.

### Question 1 - Constructors

Which numbers will be printed out:

```java
public class JavaTriviaOne {

  public JavaTriviaOne() {
    System.out.println(number);
    number = 5;
  }

  public static void main(String[] args) {
    JavaTriviaOne one = new JavaTriviaOne();
    System.out.println(one.number);
  }

}
```

### Question 2 - Constructors

Which number will be printed out:

```java
public class JavaTriviaTwo {

  public JavaTriviaTwo() {
    number = 5;
  }

  public static void main(String[] args) {
    JavaTriviaTwo one = new JavaTriviaTwo();
    System.out.println(one.number);
  }

  private int number = 3;

  {
    number = 4;
  }

}
```

### Question 3 - Constructors

Which numbers will be printed out:
```java

public class JavaTriviaThree {

  int num1;
  int num2;
  int num3;

  public JavaTriviaThree() {
    int num1, num2, num3 = 5;
    this.num1 = num1;
    this.num2 = num2;
    this.num3 = num3;
  }

  public static void main(String[] args) {
    JavaTriviaThree one = new JavaTriviaThree();
    System.out.println(one.num1);
    System.out.println(one.num2);
    System.out.println(one.num3);
  }

}
```

### Question 4 - methods

Why doesn't this code compile?
```java
public class JavaTriviaFour {

  private final int questionNumber;

  public JavaTriviaFour() {
    questionNumber = 4;
  }

  void public think() {
    System.out.println("To compile or not compile, that is the question");
  }

}
```

### Question 5 - classes

We want to define a general concept for any type of bird that serves as a base for other developers to extend. Thus, we created the following `Bird` class: 
```java

// file 'Bird.java'
class Bird {
   public String getName() { return null; }
   public void printName() {
      System.out.print(getName());
   }
}
 
// .. and another file 'Stork.java'
public class Stork extends Bird {
   public String getName() { return "Stork!"; }
   public static void main(String[] args) {
      new Stork().printName();
   }
}
```

How could this code be improved?

### Question 6 - classes

We want to define a general concept for any type of animal that serves as a base for other developers to extend. Therefore, we created the following `Animal` class:
```java
// file 'Animal.java'
public class abstract Animal {

    public Animal() {
        System.out.println("Trust me, I'm an animal.");
    }

    public String abstract getSpecies() {
        return "dog";
    }
}

// file 'Bear.java'
public class Bear extends Animal {
    public static void main(String[] args) {
        Bear grizzly = new Bear();
    }
}
```

Would that code compile?, and how can we improve it?



### Question 7: classes

What could be improved in the following `Product` class:

```java
public class product {

  String color;
  int price;

  public product(String color, int price) {
    this.color = color;
  }
  
  public String GetColor() {
      return null;
  }

}

```


## Assignment

## [Abstract classes and interfaces assignment](https://classroom.github.com/a/nlIfekz9)

#### Follow the link, accept and download the assignment from GitHub Classroom
