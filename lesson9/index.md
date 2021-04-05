---
title: Recap & Practicing OOP
nav_order: 9
has_children: false
nav_exclude: false
---

# Lesson 8: Recap & Practicing OOP

## Goals

- Check-in
- Recap OOP

## Check-in
How is everybody doing?

## Recap homework and previous class.

[Google Slides](https://docs.google.com/presentation/d/17cQhIiittot1Gv73OrVQbSRNWzShdMTjKmLWiL-IplQ/embed)

Try to answer the following questions:

- What is Object Oriented Programming?
- What is the difference between a class and an object?
- What is a constructor?
- What are the different parts of a method?
- What are the different visibilities we have in Java?
- What is Inheritance?
- What class visibilities can be inherited?
- What is method overriding?
- What method visibilities can be overridden?
- Can a constructor be overridden?
- Can a static method be overridden?
- What is method overloading?


## Exercice

In this exercice we will implement a game. This game consist of Characters and Weapons.
We have 3 Characters (Human, Alien, Robot), 3 Weapons (Gun, LightSaber, Hammer)

Each character have:
- health points between 0 and 100, 100 means the character's health is full, 0 means the character is dead.
- default damage points, when a character does not have a weapon, this is the default damage points to use when attacking.
- weapon
- attack: a method used to attack other character.
- defend: a method used when being attacked.

Each weapon have:
- damage points: when attacking the amount of points to remove from a player's health.


PS: feel free to choose the different values for characters and weapons.

1. Implement all the different classes and their related methods needed for this game.
2. Implement a game class where you have the following:
    1. have 10 characters in the game. (choose weapon or no weapon for each character).
        1. bonus: generate weapon and no weapon randomly.
    2. Choose a random amount of turns or you can use `Random` (see example below).
    3. On each turn select randomly two characters, the first one will attack the second one.
    4. When the turns end, print the surviving characters.

example of random:
```java
import java.util.Random;

Random rand = new Random();
int upperbound = 25;
//generate random values from 0-24
int int_random = rand.nextInt(upperbound);
```

## Homework

Let's spice up our game a bit. We want to add special effects that can be used by characters. In order to achieve that we need to add for each character:
- mana points between 0 and 100. when mana is at 100, the character uses the special effects if they have them when attacking or being attacked.
- mana regeneration points. Each time the character is being attacked, the mana is increased by mana regeneration points.
- special effect
Also we have to add 2 special effects DoubleHitPoint and SuperDefence:
- DoubleHitPoint: when used that damage inflected is doubled
- SuperDefence: when being attacked, the SuperDefence allow the character to recieve no damage.

In the game class try to randomly add special effects to character after each turn and see how the game evolve.

### extra challenge
Add to the weapon a decay functionnality, this means that a weapon can be used only for a certain amount of time.
For each weapon add: 
- usability between 0 and 100. When a weapon reach 0 usability, it cannot be used any more.
- decay rate: on each usage of the weapon the rate the weapon's usability is decreased by.

In the game class try to randomly add weapons to characters when they reach the decay point.

