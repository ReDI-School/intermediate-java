---
title: "8 - OOP3 - Inheritance and Visibility"
nav_order: 8 
has_children: false 
nav_exclude: false
---

# Lesson 8: OOP3 - Inheritance and Visibility

## Goals

- Check-in
- What is Inheritance?
- Why Do we need it?
- Have we seen it before?
- Visibility and access modifiers
- Some code Action!

## Check-in
How is everybody doing?
## What is Inheritance?

- Inheritance is one of the key features of OOP that allows us to create a new class from an existing class.
- The new class that is created is known as subclass (child or derived class), and the existing class from where the child class is derived is known
  as superclass (parent or base class).
- To inherit from a class, use the `extends` keyword in java.

### Let's define, again, a Product class.

```java
package com.redi.j2;

public class Product {

    private float price;

    private String name;

    private String category;


    public float getPrice() {
        return price;
    }


    protected void setPrice(float price) {
        if (price < 0)
            System.out.println("Are you kidding me?");
        else
            this.price = price;
    }


    public String getName() {
        return name;
    }


    public void setName(String name) {
        this.name = name;
    }


    public String getCategory() {
        return category;
    }


    public void setCategory(String category) {
        this.category = category;
    }


    @Override
    public String toString() {
        return "Product{" +
               "price=" + price +
               ", name='" + name + '\'' +
               ", category='" + category + '\'' +
               '}';
    }

}
```

### What if I have many laptops, and I need to make sure that none of them has its price to be less than 100?

#### Old solution (bad)

```java
package com.redi.j2;

public class Laptop {

    private float price;

    private String name;

    private String category = "Electronics";


    public float getPrice() {
        return price;
    }


    protected void setPrice(float price) {
        if (price < 100)
            System.out.println("I can't be that cheap");
        else
            this.price = price;
    }


    public String getName() {
        return name;
    }


    public void setName(String name) {
        this.name = name;
    }


    public String getCategory() {
        return category;
    }


    public void setCategory(String category) {
        this.category = category;
    }


    @Override
    public String toString() {
        return "Product{" +
               "price=" + price +
               ", name='" + name + '\'' +
               ", category='" + category + '\'' +
               '}' + "I'm also a a laptop btw!";
    }

```

### new solution (nice!)

Why don't we use inheritance?

```java
package com.redi.j2;

public class Laptop extends Product {

    public Laptop() {
        setCategory("electronics");
    }


    @Override
    public void setPrice(float price) {
        if (price < 100) {
            System.out.println("I can't be THAT cheap!!");
        }
        else {
            super.setPrice(price);
        }
    }


    @Override
    public String toString() {
        return super.toString() + "I am also a laptop btw!";
    }
}
```

### Think of inheritance as an "is-a" relationship

- In Java, inheritance is an is-a relationship. That is, we use inheritance only if there exists an is-a relationship between two classes. For example,

- Laptop is a Product, Car is a Vehicle, Orange is a Fruit.

## Why do we need it?

- The most important use of inheritance in Java is code reusability. The code that is present in the parent class can be directly used by the child
  class.
- Method overriding is also known as runtime polymorphism. Hence, we can achieve Polymorphism in Java with the help of inheritance.

## Have we seen it before?

**YES!!** Since day one actually. Remember this example from the very first lesson?

```java
package com.redi.j2;

public class Main {

    public static void main(String[] args) {
        System.out.println("Hello World");

        String name = "Memet";
        String profession = "skydiver";
        int age = 40;
        boolean smoking = false;

        coolOrNotCool(profession);

        for (int i = 0; i < 10; i++) {
            System.out.println("hey " + i);
        }
    }


    private static void coolOrNotCool(String profession) {
        if (profession.equals("skydiver")) {
            System.out.println("Cool");
        }
        else {
            System.out.println("Not cool");
        }
    }
}
```

let's take a moment and understand what is a [`String`](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html) really?

## Visibility and access modifiers

### Default Access Modifier - No Keyword

- Default access modifier means we do not explicitly declare an access modifier for a class, field, method, etc.

- A variable or method declared without any access control modifier is available to any other class in the same package.

### Private Access Modifier - Private

- Methods, variables, and constructors that are declared private can only be accessed within the declared class itself.

- Private access modifier is the most restrictive access level. Class and interfaces cannot be private.

### Public Access Modifier - Public

- A class, method, constructor, interface, etc. declared public can be accessed from any other class. Therefore, fields, methods, blocks declared
  inside a public class can be accessed from any class belonging to the Java Universe.

![modifiers summary](Screenshot%202021-10-13%20113506.png)

## What is _Method Overriding_?

Let's have a look at another example of handy Inheritance: defining geometric shapes.

```java
public class Shape {

    private final String type;

    private final double area;

    private final double perimeter;


    public Shape(final String type, final double area, final double perimeter) {
        this.type = type;
        this.area = area;
        this.perimeter = perimeter;
    }

    // Getters for all properties

}
```

Let us say we want to define two specific shapes: a rectangle and a circle. One way of defining these classes could be:

```java
public class Rectangle {

    private final double length;

    private final double breadth;

    private final double area;

    private final double perimeter;


    public Rectangle(final double length, final double breadth) {
        this.length = length;
        this.breadth = breadth;
        this.area = length * breadth;
        this.perimeter = 2 * (length + breadth);
    }

    // Getters for all properties
}
```

If one could do it with inheritance, having Rectangle as a subclass of the Shape class:

```java

public class Rectangle extends Shape {

    private final double length;

    private final double breadth;


    public Rectangle(final double length, final double breadth) {
        super("RECTANGLE", length * breadth, 2 * (length + breadth));
        this.length = length;
        this.breadth = breadth;
    }

    // Getters for length and breadth only, 
}
```

And for Circle:

```java
public class Circle {

    private final double radius;

    private final double area;

    private final double perimeter;


    public Circle(final double radius) {
        this.radius = radius;
        this.area = Math.PI * radius * radius;
        this.perimeter = 2 * Math.PI * radius;
    }

    // Getters for all properties
}
 ```

If one could do it with inheritance, having Circle as a subclass of the Shape class:

 ```java
public class Circle extends Shape {

    private final double radius;


    public Circle(final double radius) {
        super("CIRCLE", Math.PI * radius * radius, 2 * Math.PI * radius);
        this.radius = radius;
    }

    // A getter for the radius only, since we are inheriting all other getters from the parent class.
}
 ```

The properties `area` and `perimeter` are now `inherited` by the sub classes `Circle` and `Rectangle`.

Now suppose we want to take control of how we print our Shapes, and we simply want to do the following

```java
public class Main {

    public static void print(Shape shape) {
        shape.print();
    }

}
```

The assumption here is that the class `Shape` has the method `print` which we haven't defined. So let's define it.

```java
public class Shape {

    private final String type;

    private final double area;

    private final double perimeter;


    public Shape(final String type, final double area, final double perimeter) {
        this.type = type;
        this.area = area;
        this.perimeter = perimeter;
    }


    public void print() {
        System.out.println("Name: " + type);
        System.out.println("Area: " + area);
        System.out.println("Perimeter: " + perimeter);
    }
}
```

So now we have taken control the printing of our shapes. The method `print` is now inherited by the sub classes `Circle`
and `Rectangle`.

But what if we want to print the extra properties of the `Circle` and `Rectangle`, how do we achieve that? The answer is method overriding. We simple
override the method `print` in each of these classes and do whatever we want there.

For example we can override `print` in `Rectangle` as follows:

```java
public class Rectangle extends Shape {

    private final double length;

    private final double breadth;


    public Rectangle(final double length, final double breadth) {
        super("RECTANGLE", length * breadth, 2 * (length + breadth));
        this.length = length;
        this.breadth = breadth;
    }


    @Override
    public void print() {
        super.print();
        System.out.println("Length: " + length);
        System.out.println("Breadth: " + breadth);
    }
}
```

And we can override `print` in `Circle` as follows:

```java
public class Circle extends Shape {

    private final double radius;


    public Circle(final double radius) {
        super("CIRCLE", Math.PI * radius * radius, 2 * Math.PI * radius);
        this.radius = radius;
    }


    @Override
    public void print() {
        System.out.println("Radius: " + radius);
    }
}
```

## Exercises:

### Exercise 1

Extract the `Shape` class and implement the `Square` shape.

### Exercise 2
Make a new class `RediList`, that extends the `ArrayList` class and  implement a `count` method that returns the number of occurrences of a specific element in the object of `RediList`. Think about how can you implement such functionality with the data structures that you have learned so far.

## [Inheritance and Visibility assignment](https://classroom.github.com/a/G8hBj-_N)

#### Follow the link, accept and download the assignment from GitHub Classroom

## food for thought

- After learning about access modifiers do you think a constructor of a class can be private? Let's have a discussion about it on slack!
