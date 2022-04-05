---
title: "04 - OOP Assignment Solutions"
nav_order: 0
parent: "04 - OOP - Objects, Classes & Constructor"
nav_exclude: false
---

### Create the class Car

This is a possible implementation of the **Car** class

```java
package com.redi.j2;

import java.util.ArrayList;
import java.util.List;
import java.util.UUID;

public class Car {

    int speed = 0;
    int maxSpeed;
    String plateNumber;
    int numSeats;
    List<String> passengers = new ArrayList<>();

    public Car(String plateNumber, int maxSpeed, int numSeats) {
        this.plateNumber = plateNumber;
        this.maxSpeed = maxSpeed;
        this.numSeats = numSeats;
    }

    public Car(String plateNumber) {
        this.plateNumber = plateNumber;
        this.maxSpeed = 100;
        this.numSeats = 5;
    }

    public Car() {
        this.plateNumber = UUID.randomUUID().toString();
        this.maxSpeed = 100;
        this.numSeats = 5;
    }

    public void start() {
        if (speed>0) {
            System.out.println("The car is already moving at " + speed + " km/h.");
        } else {
            this.speed = 30;
        }
    }

    public void stop() {
        if (speed==0) {
            System.out.println("The car is already stopped.");
        } else {
            this.speed = 0;
        }
    }

    public void accelerate(int increase) {
        if (increase <= 0) {
            System.out.println("You're not really accelerating; please consider using decelerate()");
            return;
        }
        if (this.speed == maxSpeed ){
            System.out.println("The car is full steam ahead.");
        } else if (this.speed + increase > maxSpeed) {
            System.out.println("That's too much for this car, will go at max speed of " + maxSpeed);
            this.speed = maxSpeed;
        } else {
            this.speed += increase;
        }
    }

    public void decelerate(int reduce) {
        if (reduce <= 0) {
            System.out.println("Reduce of a negative number? consider using accelerate() instead.");
            return;
        }
        if (this.speed == 0) {
            System.out.println("This car is stop, cannot go slower than this!");
        } else if (this.speed - reduce < 0) {
            System.out.println("This car is not going that fast; will stop it.");
            this.speed = 0;
        } else {
            this.speed -= reduce;
        }
    }

    public boolean enter(String name){
        if (passengers.size() < numSeats) {
            if (passengers.contains(name)) {
                System.out.println(name + " is already in the car.");
            } else {
                passengers.add(name);
                System.out.println(name + " is now in the car.");
            }
        } else {
            System.out.println("This car is full, there's no seat for" + name);
            return false;
        }
        return true;
    }

    public boolean leave(String name){
        System.out.println(name + " will leave if it's in the car.");
        return passengers.remove(name);
    }

    @Override
    public String toString() {
        return "speed=" + speed +
                ", maxSpeed=" + maxSpeed +
                ", plateNumber='" + plateNumber + "'" +
                ", numSeats=" + numSeats +
                ", passengers=" + passengers;
    }
}
```