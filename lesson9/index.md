---
title: Inheritance, Overriding and Overloading
nav_order: 9
has_children: true
---

# Lesson 9: Inheritance, Overriding and Overloading

## Goals

- Check-in
- Recap homework and previous classes.
- What is _Inheritance_?
- What is _Method Overriding_?
- What is _Method Overloading_?
- Break-out
- Regroup and check-out

## Check-in

## Recap homework and previous class.

- What is Object Oriented Programming?
- What is the difference between a class and an object?
- What is a constructor?
- What are the different parts of a method?
- What is the difference between a static and non static method?
- What are the different visibilities we have in Java?

## What is _Inheritance_?

Inheritance is a language construct that allows for classes to be related to one another so that one class can inherit 
features of another class. The class or classes inherited from are called superclasses, or ancestors. The inheriting
classes are called subclasses, or descendents. Inheritance is indicated using the keyword `extends`.

- **Child/Sub/descendant Class:** The class that extends the features of another class is known as child class, sub class 
  or derived class.

- **Parent/Base/Super/Ancestor Class:** The class whose properties and functionalities are used(inherited) by another class
  is known as parent class, super class or Base class.

Suppose we need to write a program that deals with the **area and perimeter of geometric shapes** such as rectangles and 
circles, and possibly other shapes as well. We will design these classes, exploring the possibly hierarchies between
them. Provide full implementations of all methods.

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
}
```

Now, let's see what a Rectangle looks like:

```java
public class Rectangle {

    private final double length;
    private final double breadth;

    public Rectangle(final double length, final double breadth) {
        this.length = length;
        this.breadth = breadth;
    }
}
```

Now, let's see what a Circle looks like:

 ```java
public class Circle {

    private final double radius;
    
    public Circle(final double radius) {
        this.radius = radius;
    }
}
 ```

Supposing now that we have a method that helps us in printing our Shape as defined below:

```java
public class Main {
    
    public static void print(Shape shape) {
        System.out.println("Name: " + shape.type);
        System.out.println("Area: " + shape.area);
        System.out.println("Perimeter: " + shape.perimeter);
    }
    
}
```

#### Questions:

-   What type does our `print` method accepts?
-   Can it accept `Circle` or `Recatangle`?
-   Should it accept `Circle` or `Recatangle`?
-   What can we do to make it accept instances of `Circle` or `Recatangle`?


The answer is **Inheritance**. And how do we achieve it by creating `Rectangle` and `Circle` as subclasses of `Shape`.

Now, let's see what a Rectangle should look like as a subclass:

```java
public class Rectangle extends Shape {

   private final double length;
   private final double breadth;

   public Rectangle(final double length, final double breadth) {
       super("RECTANGLE", length * breadth, 2 * (length + breadth));
       this.length = length;
       this.breadth = breadth;
   }
}
```

Now, let's see what a Circle looks like:

 ```java
public class Circle extends Shape {

    private final double radius;

    public Circle(final double radius) {
        super("CIRCLE", Math.PI * radius * radius, 2 * Math.PI * radius);
        this.radius = radius;
    }
}
 ```

The properties `area` and `perimeter` are now `inherited` by the sub classes `Circle` and `Rectangle`.

#### Questions Revisited:

-   What type does our `print` method accepts?
-   Can it accept `Circle` or `Recatangle`?
-   Should it accept `Circle` or `Recatangle`?
-   What can we do to make it accept instances of `Circle` or `Recatangle`?

#### Additional Questions

- What class visibilities can be inherited?
- How else can we prevent a class from being inherited?

## What is _Method Overriding_?

Supposing we want to take control of how we print our Shapes, and we simply want to do the following

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

But what if we want to print the extra properties of the `Circle` and `Rectangle`, how do we achieve that? 
The answer is method overriding. We simple override the method `print` in each of these classes and do whatever we want
there.

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

#### Questions:

- What differences do you see in the two overridden methods above?
- What method visibilities can be overridden?
- How else can we prevent a method from being overridden?
- Is a constructor a method?
- Can a constructor be overridden?
- Can a static method be overridden?

## What is _Method Overloading_?

In method overloading, more than one method shares the same method name with different signature in the class. In 
method overloading, return type can or can not be be same, but we must have to change the parameter because in java, 
**we can not achieve the method overloading by changing only the return type of the method.**

For example we can define different print methods for each of our shapes as below.

```java

public class Main {

    public static void print(Rectangle rectangle) {
        System.out.println("Name: RECTANGLE");
        System.out.println("Length: " + rectangle.length);
        System.out.println("Breadth: " + rectangle.breadth);
        System.out.println("Area: " + rectangle.area);
        System.out.println("Perimeter: " + rectangle.perimeter);
    }

    public static void print(Circle circle) {
        System.out.println("Name: RECTANGLE");
        System.out.println("Radius: " + circle.radius);
        System.out.println("Area: " + circle.area);
        System.out.println("Perimeter: " + circle.perimeter);
    }

}
```

Here is a simpler example of method overloading

```java
public class Main {

    public static int add(int a, int b) { }

    public static double add(float a, int b) { }

    public static int add(int a, double b, double c) { }

    public static long add(int a, double b) { }

    public static long add(long a, double b, double c, double d) { }

}
```

**The rules of method overloading are not restrictive and well defined. The only rule is that if two methods share the
same name, they must have different argument list.**

## Exercises:

### Exercise 1 

Extract the `Shape` classes and experiment with them. Make them compile. Create some shapes and print them.

### Exercise 2 

Discuss and implement different solutions to accommodate a `Square` i.e. is a `Square` a `Rectangle` or is it another
`Shape` different from a `Rectangle`.
 
### Exercise 3

Implement all the `add` methods defined above.


## Home Work

Think about how you can design the **Animal Kingdom** using OOP and inheritance. Experiment and implement your design.

#### Requirements:

- There must be at least one base class
- There must be at least two sub classes inheriting from a base class.
- There must be at least one method in each base class that shouldn't be overridden.
- There must be at least one method in each base class that can be overridden and it must be overridden by at least one
  of its sub classes.
- Each subclass must have at least one method that is unique to it.
- Each subclass must have at least one member that is unique to it.

