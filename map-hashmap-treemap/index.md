---
title: Maps (HashMap, TreeMap)
nav_order: 0
has_children: true
nav_exclude: true
---

# Lesson 13: Maps (HashMap, TreeMap)

## Goals

- Learn how and when to use `Maps`
- Learn the difference between `HashMap` and `TreeMap`

## What are Maps
Maps “map” a key to a value, making it easy to store something and find it again later on. Since this is one of the most common problems in programming they are used quite a lot to solve different kinds of problems. In some programming languages maps are called Dictionaries which makes the use case clearer. They allow you to find data by a key or identifier. 

| Key  | Value |
| ---- | ---- |
| 1      | Anna, Teacher |
| 2      | Mohamed, Student |
| 3      | Jorge, Student |

## What can you do with a Map
Maps are defined by their key and value type. Keys are usually simple values (string or number) and the values are more complex objects. A map is therefore defined with two types, first the key, then the value: `Map<String,Student>`. 
It is totally valid to use a complex object as the key but less common, for example `Map<Student, Int>`. More on that later.

## Common Map Operations
```java
// creating a new map
// The map is typed by key and value, in this case
// the key is a String and the value a Student
// (a custom class)
Map<String, Student> map = new HashMap<>();

// Put new values in a map
map.put("Mohamed", new Student(84758, "Mohamed"));
map.put("Anna", new Student(45344, "Anna"));

// getting the size of a map
map.size(); // 2

// Check if a map has a key with a value
map.containsKey("Juan"); // false

// Check if a map contains a value
map.containsValue(new Student(45344, "Anna")); // true

// Get a value from a map
Student anna = map.get("Anna");

// getting all the keys of a map
Set<String> keys = map.keySet();
// keys = ["Mohamed", "Anna"]

// getting all the values of a map
Collection<String> values = map.values();
// values = [Student "Anna", Student "Mohamed"]

// Remove a value from a map
Student mo = map.remove("Mohamed");
map.containsKey("Mohamed"); // false

// iterating over a map
for (Map.Entry<String, String> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " : " + entry.getValue());
}
```

## Different implementations
There are many different implementation of maps but the most common one is the HashMap. This is a safe go-to implementation if you don’t need any specific functionality beyond what the Map interface offers.
The TreeMap differs in that it sorts the keys, resulting in a sorted output when you retrieve the values:
```java
Map<String, Student> map = new TreeMap<>();
map.put("Mohamed", new Student(84758, "Mohamed"));
map.put("Anna", new Student(45344, "Anna"));
map.keySet(); // ["Anna","Mohamed"]
```

## Complex keys
Generally speaking, stay away from using complex types as keys. Maps rely on correct implementation of `equals`, `hashKey` and in the case of TreeMap `compareTo` . If these are implemented inefficiently or incorrectly then the map can get slow or behave incorrectly. 
Usually you will have a basic data type that uniquely identifies an object - use that.

## Exercises

### Exercise 1

Create a `Map` that associates the following employee IDs with names. 

Keys and values of Maps can be any Object type, so in real life you would probably have the key be a `String` and the associated value be a `Person` or an `Employee` object. To make things simpler on this exercise, you can use String for both the ID and the name, rather than bothering to create a Person or Employee class. 

The point here is to associate keys with values, then to retrieve the values later based on their keys.

| Id | Name |
|----|------|
| a1234 | Steve Jobs |
| a1235 | Bill Gates |
| a1236 | Jeff Bezos |
| a1237 | Larry Page |
| a1238 | Sergey Brin |


### Exercise 2 (based on exercise 1)

Go back to the previous problem and make your lookup method work with keys regardless of whether they are lower or uppercase. For example, both “a1234” and “A1234” should match Steve Jobs. Hint: very similar to the previous exercise, so if your solution is complex, you are overlooking the obvious.


### Exercise 3

Write a method that acts as a english-german dictionary. It takes one parameter - english word - and returns german translation. 
If word is not found it returns "Sorry, I don't know such a word".

### Exercise 4

<ResponsiveImage src="/people-map.jpg"></ResponsiveImage>

Write a program that creates a `Map` of *students* and the *country* they are from. Add 5 students from our class to this map.

- use `HashMap`
- what are the data types for key and value?

1. Print to the console the country of any of your classmates (using apropriate `Map` method)
2. Print all map entries, each entry in a format like this: `name: country`
3. Print all unique country names.

### Exercise 5

Write a method program that contains a pizza menu - we are interested only in pizza name and it's price. 
For simplification we can assume that all pizzas are sold in the same size and price is an `Integer`. 
Now, write a method that takes how much money there is in your wallet and then returns a `Map` containing only the pizzas and their prices, that you can afford.

### Exercise 6

Write a program that calculates average price of a second hand car based on the list of prices found on eBay. Example list:

- Toyota: 10000, 15000, 18000
- BMW: 20000, 23000, 50000
- Audi: 35000, 43000, 18000, 50000

The method should return a map where `key` is a car name and `value` is a average price.


## Additional Resources

 - [📖 Java HashMap vs TreeMap](https://www.baeldung.com/java-treemap-vs-hashmap)
 - [📖 Java HashMap vs TreeMap (similarities and differences)](https://stackabuse.com/hashmap-and-treemap-in-java-differences-and-similarities)
 - [📺 How HashMap works internally](https://www.youtube.com/watch?v=CojCE-ojdGY)
 - [📄 Map Javadoc](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html)
 - [📄 HashMap Javadoc](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html)
 - [📄 TreeMap Javadoc](https://docs.oracle.com/javase/8/docs/api/java/util/TreeMap.html)
 
