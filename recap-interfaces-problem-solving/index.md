---
title: Recap Interfaces. Problem solving
nav_order: 0
has_children: true
nav_exclude: true
---

# Lesson 18: Recap Interfaces. Problem solving

## Goals

- Recap Interfaces and Abstract classes
- Coding and Problem solving

## Recap Interfaces and Abstract classes

[A presentation from the previous semester](https://redi-j2.netlify.app/lessons/10-interfaces-and-abstract-classes.html)

## Coding: Problem solving
Let's do some Netflix 🎥 🍿 

See an example of Plans in `Netfix` [link](https://www.netflix.com/signup/planform) and let's implement it as Inheritance (there are several ways, we try Inheritance today)
- Create a interface `Device` and its subclasses Laptop, TV, Phone, Tablet with some characteristics
- Create an abstract class `User` with fields `email`, `price`, `numberOfParalellScreens` 
- Add a method `watch(Device device, String movie)` that prints `user {email} watches {film}`
- Create a class `BasicUser` that is subclass of the class `User`
- Create a class `StandardUser` that is a subclass of `BasicUser` and has a method `watchHd(Device device, String movie)` 
that prints `user {email} watches {film} in HD` 
- Create a class `PremiumUser` that is a subclass of `StandardUser` and has a method `watchUltraHd(Device device, String movie)` 
that prints `user {email} watches {film} in UltraHD`
- Make sure that your methods `watch`, `watchHd`, `watchUltraHd` take into consideration `numberOfParallScreens` available for the user
- (Complex) Add a method to `stopWatch()`, that will make one screen available, if it was used 
- (Complex) Promote more expensive plans! if a user doesn't have enough available screens when they try to watch something show them a message that they can upgrade to the next plan:
 BasicUser -> StandardUser, StandardUser -> PremiumUser. PremiumUser -> Register another account. Remember this promotion should happen for all methods: `watch`, `watchHd`, `watchUltraHd`
