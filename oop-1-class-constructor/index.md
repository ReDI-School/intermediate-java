---
title: OOP 1 What is a class
nav_order: 0
has_children: true
nav_exclude: true
---

# Lesson 7: Object-Oriented Programming (OOP) 1

## Goals

- Know what Object-Oriented Programming is.
- Be able to translate a real-life object to a programming object.
- Be able to create a Java class.
- Be able to instantiate an object of a Java class.
- Understand the difference between a class and an object.
- Have an overview about class constructors.
- Have an overview about the main concepts of OOP.

## Recap & Homework check

Let's look into the homework from lesson 6

[Google Slides](https://docs.google.com/presentation/d/1M_Eeyv9fA4oJda54TCXdyhBqFoclJgqYenxT7GqkXwo/embed)

## What Is an Object?

An object is a software bundle of related property and behavior. Software objects are often used to model the real-world
objects that you find in everyday life. This lesson explains how property and behavior are represented within an object,
introduces the concept of data encapsulation, and explains the benefits of designing your software in this manner.

Objects are key to understanding object-oriented technology. Look around right now and you'll find many examples of
real-world objects: your dog, your desk, your television set, your bicycle.

Real-world objects share two characteristics: They all have property and behavior. Dogs have property (name, color,
breed, hungry) and behavior (barking, fetching, wagging tail). Bicycles also have property (current gear, current speed)
and behavior (changing gear, applying brakes). Identifying the property and behavior for real-world objects is a great
way to begin thinking in terms of object-oriented programming.

Take a minute right now to observe the real-world objects that are in your immediate area. For each object that you see,
ask yourself two questions: "What possible properties can this object be in?" and "What possible behavior can this
object perform?". Make sure to write down your observations. As you do, you'll notice that real-world objects vary in
complexity; your desktop lamp may have only two possible properties (on and off) and two possible behaviors (turn on,
turn off), but your desktop radio might have additional properties (on, off, current volume, current station) and
behavior (turn on, turn off, increase volume, decrease volume, seek, scan, and tune). You may also notice that some
objects, in turn, will also contain other objects. These real-world observations all translate into the world of
object-oriented programming.

![Concept Object](concepts-object.gif)

Software objects are conceptually similar to real-world objects: they too consist of property and related behavior. An
object stores its property in fields (variables in some programming languages) and exposes its behavior through
methods (functions in some programming languages). Methods operate on an object's internal property and serve as the primary
mechanism for object-to-object communication. Hiding internal property and requiring all interaction to be performed
through an object's methods is known as data encapsulation — a fundamental principle of object-oriented programming.

Consider a bicycle, for example:

![Concept Bicycle Object](concepts-bicycleObject.gif)

By attributing property (current speed, and current gear) and providing methods for changing that property, the object
remains in control of how the outside world is allowed to use it. For example, if the bicycle only has 6 gears, a method
to change gears could reject any value that is less than 1 or greater than 6.

Bundling code into individual software objects provides a number of benefits, including:

- **Modularity**: The source code for an object can be written and maintained independently of the source code for other
  objects. Once created, an object can be easily passed around inside the system.
- **Information-hiding**: By interacting only with an object's methods, the details of its internal implementation
  remain hidden from the outside world.
- **Code re-use**: If an object already exists (perhaps written by another software developer), you can use that object
  in your program. This allows specialists to implement/test/debug complex, task-specific objects, which you can then
  trust to run in your own code.
- **Pluggability** and debugging ease: If a particular object turns out to be problematic, you can simply remove it from
  your application and plug in a different object as its replacement. This is analogous to fixing mechanical problems in
  the real world. If a bolt breaks, you replace it, not the entire machine.

## What Is a Class?

A class is a blueprint or prototype from which objects are created. This section defines a class that models the
property and behavior of a real-world object. It intentionally focuses on the basics, showing how even a simple class
can cleanly model property and behavior.

In the real world, you'll often find many individual objects all of the same kind. There may be thousands of other
bicycles in existence, all of the same make and model. Each bicycle was built from the same set of blueprints and
therefore contains the same components. In object-oriented terms, we say that your bicycle is an instance of the class
of objects known as bicycles. A class is the blueprint from which individual objects are created.

The following Bicycle class is one possible implementation of a bicycle:

```java
class Bicycle {

    int speed = 0;
    int gear = 1;

    void changeGear(int newValue) {
        gear = newValue;
    }

    void speedUp(int increment) {
        speed = speed + increment;
    }

    void applyBrakes(int decrement) {
        speed = speed - decrement;
    }

    void printProperties() {
        System.out.println("speed:" + speed + " gear:" + gear);
    }
}
```

The syntax of the Java programming language will look new to you, but the design of this class is based on the previous
discussion of bicycle objects. The fields speed, and gear represent the object's property, and the methods (changeGear,
speedUp etc.) define its interaction with the outside world.

## Constructors

A class contains constructors that are invoked to create objects from the class blueprint. Constructor declarations look
like method declarations—except that they use the name of the class and have no return type. For example, `Bicycle` has
the following constructors:

```java
public Bicycle(int startSpeed,int startGear){
        this.gear=startGear;
        this.speed=startSpeed;
}
public Bicycle(){
        this.gear=1;
        this.speed=0;
}
```

To create a new `Bicycle` object called `myBike`, a constructor is called by the new operator:

```java
Bicycle myBike=new Bicycle(0,8);
```

`Bicycle yourBike = new Bicycle();` invokes the no-argument constructor to create a new `Bicycle` object
called `yourBike`.

```java
Bicycle yourBike=new Bicycle();
yourBike.gear=5;
yourBike.speed=2;
```

Both constructors could have been declared in Bicycle because they have different argument lists. As with methods, the
Java platform differentiates constructors on the basis of the number of arguments in the list and their types. You
cannot write two constructors that have the same number and type of arguments for the same class, because the platform
would not be able to tell them apart. Doing so causes a compile-time error.

You don't have to provide any constructors for your class, but you must be careful when doing this. The compiler
automatically provides a no-argument, default constructor for any class without constructors. 

You may have noticed that the `Bicycle` class does not contain a main method. That's because it's not a complete
application; it's just the blueprint for bicycles that might be used in an application. The responsibility of creating
and using new `Bicycle` objects belongs to some other class in your application.

Here's a `BicycleDemo` class that creates two separate `Bicycle` objects and invokes their methods:

```java
class BicycleDemo {
    public static void main(String[] args) {

        // Create two different 
        // Bicycle objects
        Bicycle bike1 = new Bicycle();
        Bicycle bike2 = new Bicycle();

        // Invoke methods on 
        // those objects
        bike1.speedUp(10);
        bike1.changeGear(2);
        bike1.printProperties();

        bike2.speedUp(10);
        bike2.changeGear(2);
        bike2.speedUp(10);
        bike2.changeGear(3);
        bike2.printProperties();
    }
}

```

The output of this test prints the current speed, and gear for the two bicycles:

```
speed:10 gear:2
speed:20 gear:3
```

## Exercise

0. Create an empty class to represent a `Car`
1. Create an `Application` class with the `main` method.
2. Take some time to think about what properties a `Car` could have.
   - **At least 3 properties required.**
3. Take some time to think about what behaviors a `Car` could have.
   - 2 behaviors that change some properties
   - 2 behaviors that do not change any property
   - A `print` method that prints out the properties of the `Car`
4. Add a default no-arg constructor to `Car` and initialize the properties of `Car`
5. Add a constructor with arguments to `Car` and initialize the properties of `Car` from the arguments
6. In your `Application.main` method, create some cars. And make sure to use both constructors.
7. Execute all the behaviors of the `Car` with different parameters and print the `Car` after every behavior.

## Homework

[Please follow this link for the homework](https://github.com/tilmans/oop1-homework)

## Materials

- [Object-Oriented Programming Concepts by Oracle](https://docs.oracle.com/javase/tutorial/java/concepts/index.html)
- [Providing Constructors for Your Classes](https://docs.oracle.com/javase/tutorial/java/javaOO/constructors.html)
- [OOP: Everything you need to know about Object Oriented Programming](https://medium.com/from-the-scratch/oop-everything-you-need-to-know-about-object-oriented-programming-aee3c18e281b)

- [4 Pillars for Object Oriented Programming](https://www.linkedin.com/pulse/4-pillars-object-oriented-programming-pushkar-kumar/)

