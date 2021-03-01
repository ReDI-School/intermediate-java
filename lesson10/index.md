---
title: Interfaces,Abstarct and Final classes
nav_order: 10
has_children: true
nav_exclude: true
---

## Learning Objectives

At the end of the class, attendees we be able to

- Define what an final class is
- Create and use final classes in Java
- Explain what final classes are useful for
- Define what an abstract class is
- Create and use abstract classes in Java
- Explain what abstract classes are useful for
- Define what an interface is
- Create and use interfaces in Java
- Explain what interfaces are useful for
- Explain the differences between abstract classes and interfaces


## Recap
- What is inheritance?
- What is method overriding and overloading?


## What is _final_?

**final** is a keyword which can be used with variable ,method or class


### With methods
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


    public double getArea() {
        return this.area;
    }
}
```
Now lets create a Rectangle sub class of class Shape and override getArea

```java
public class Rectangle extends Shape{

    public Rectangle(String type, double area, double perimeter) {
        super(type, area, perimeter);
    }

    @Override
    public double getArea() {
        return 0;
    }
}
```

#### Questions:
- When we create an object for Rectanlge and invoke getArea() what would be the output?


In some cases when we want child class to invoke parent class method but not to overrirde them in such scenario we use **final** keyword before method

Now lets make it final
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

    public final double getArea() {
        return this.area;
    }
}
```

### Questions?
- Now we just saw how we can restrict the child class to override the parent method. How about restricting any class to extend other classes?



The solution is simple we can add **final** keyword on class.A class that is declared final cannot be subclassed at all.

### Questions?
- Have you noticied any Java Classes before?

Now let's change Shape class to final and see what will happen to sub-classes.

```java
public final class Shape {

    private final String type;
    private final double area;
    private final double perimeter;

    public Shape(final String type, final double area, final double perimeter) {
        this.type = type;
        this.area = area;
        this.perimeter = perimeter;
    }

    public final double getArea() {
        return this.area;
    }
}
```


## Abstract Class and Interfaces
[Interfaces & Abstract Classes](https://speakerdeck.com/ftchirou/interfaces-and-abstract-classes-in-java)

## Exercises

### Exercise 1 
Make `Shape` class from lesson9 as abstarct and observer the error message and try to add/make existing method as abstract.

### Exercise 2
Create different subclasses of `Shape` like `Rectangle` and `Square`.Instanciate and try to assign to sub-classes to `Shape` and discuss pros and cons?

### Exercise 3
Model a `Vehicle` with interface try to comeup with good methods which can be part of interface
and also create subclasses and try to invoke the methods?

## Links
- [Final Classes](https://docs.oracle.com/javase/tutorial/java/IandI/final.html)
- [What is an interface?](https://docs.oracle.com/javase/tutorial/java/concepts/interface.html)
- [Interfaces](https://docs.oracle.com/javase/tutorial/java/IandI/createinterface.html)
- [Abstract Classes](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html)