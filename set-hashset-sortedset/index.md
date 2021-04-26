---
title: Sets
nav_order: 13
has_children: true
nav_exclude: false
---

# Lesson 7: Sets

## Goals

- What is a `Set`?
- When do I need a `Set`?
- `Set` vs `List`
- Understanding `Set`.
- Understanding `SortedSet`.

## Recap

- What is an `Array`?
- What is a `List`?
- What is the difference between an `Array` & a `List`?

## What is a Set?

A `Set` is a collection of items that contains no duplicate items.

A `Set` is a collection of items that contains only unique elements.

More formally, `Set`s contain no pair of items `e1` and `e2` such that `e1.equals(e2)`.

1. What is the size of this `Set` at then end?

  ```java
public class Main {
    public static void main(String[] args) {
        Set<Integer> set = emptySet();
        set.add(3);
        set.add(4);
        set.add(5);
        set.size(); ??
    }
}
  ```

2. What is the size of this `Set` at then end?

  ```java
public class Main {
    public static void main(String[] args) {
        Set<Integer> set = emptySet();
        set.add(3);
        set.add(4);
        set.add(3);
        set.size(); ??
    }
}
  ```

## When do I need a `Set`?

As stated above, you need a Set when you are interested in only unique items.

## What is a `SortedSet`?

A `SortedSet` is a `Set` with unique items that are always sorted in a well-defined ordering criteria.
e.g. `{3, 10, 12, 13, 20}`

You need a `SortedSet` when you are interested in only unique items that are sorted.

## The `Set` interface.

### Let us design `OurSet` interface.

```java
interface OurSet<T> {

    // adds an item to the set
    void add(T t);

    // removes an item from the set
    void remove(T t);

    // checks if the item is present in the set
    boolean contains(T t);

    // performs an operation on every item in the set
    void forEach(Consumer<T> consumer);

    // returns the size of this set
    int size();
}
```

### Let us design a `SortedSet` interface.

```java
interface OurSortedSet<T> extends Set<T> {

    // The first item in the Set
    T first();

    // The last item in the Set
    T last();

    // The Set containing items >= first and < last.
    SortedSet<T> subset(T first, T last);
}
```

### `Set` implementations

All implementations can be found [here](https://docs.oracle.com/javase/7/docs/api/java/util/Set.html). However, the most
common ones are:

- `HashSet`: This uses the `equals` and `hashcode` methods to ensure that the items in the Set are unique.
- `TreeSet`: This uses the `compareTo` method to ensure that items are unique and sorted. The type of items in this set
  must implement the `Comparable` interface.

This is how you can declare a set:

```java
public class Main {
    public static void main(String[] args) {
        Set<Integer> mySet = new HashSet<>();
        SortedSet<Integer> mySortedSet = new TreeSet<>();
        Set<Integer> anotherSet = new TreeSet<>();
    }
}
```

### HashSet

[HashSet](https://docs.oracle.com/javase/7/docs/api/java/util/HashSet.html) is the most commonly used set. It behaves
exactly as you would expect it from a set:

- Doesn't guarantee any order
- Doesn't contain any duplicate elements
- Is fast in checking whether an element is contained within the set or not

### TreeSet

[TreeSet](https://docs.oracle.com/javase/7/docs/api/java/util/TreeSet.html) is less commonly used, but has the advantage
that it can keep the elements ordered:

- Guarantees an order (either defined or the natural order)
- Doesn't contain any duplicate elements
- Is fast (but a bit slower than `HashSet`) in checking whether an element is contained within the set or not

## Quick Design

- `SimpleSet`: A simple implementation of the `OurSet` interface using only the `equals` method
- `HashSet`: A simple implementation of the `OurSet` interface using the `equals` and `hashCode` methods.
- `MySortedSet`: A simple implementation of the `OurSortedSet` interface using only the `equals` method and ensuring the
  containing collection is sorted.

## Exercises

### Exercise 1

- Write a method that takes an array with integers and return an array of unique values of the array
- Write a method that takes an array with integers and return the number of unique items in the array

### Exercise 2

- Write a method that takes a String and returns all unique characters of this String
- Write a method that takes a String and returns the number of unique characters of this String

### Exercise 3

Write a static method intersection that will return an intersection of two sets given by parameters. Note - sets given
by parameters may not be modified.

```java
public class SetUtils {
    public static <T> Set<T> intersection(Set<T> first, Set<T> second) {
        return null;
    }
}
```

### Exercise 4

Write a static method union that will return an union of two sets given by parameters. Note - sets given by parameters
may not be modified.

```java
public class SetUtils {
    public static <T> Set<T> union(Set<T> first, Set<T> second) {
        return null;
    }
}
```

### Exercise 5

Write a static method difference that will return a difference between two sets given by parameters. Note - sets given
by parameters may not be modified.

Given two sets `A` and `B` in that order, the difference of `A` and `B` i.e. `A - B` is the `Set` of items in `A` that
are not in `B`.

```java
public class SetUtils {
    public static <T> Set<T> difference(Set<T> first, Set<T> second) {
        return null;
    }
}
```
