---
title: Maps (HashMap, TreeMap)
nav_order: 13
has_children: true
---

# Lesson 13: Maps (HashMap, TreeMap)

## Goals

- Learn how and when to use the two most used implementations: `HashMap` and `TreeMap`
- know the difference between `HashMap` and `TreeMap`
- **Practice!**

## Slides

[Google Slides](https://docs.google.com/presentation/d/e/2PACX-1vStTwKJBl_FwEWMe1jBoCbFqbu7tLILPk4O8Ch5s_BrbqRTRUTCU_5fpbQem331aL0gZ3Z8Q7qZ9WJl/embed) .

## Common Map Operations

```java
// creating a new map
Map<String, String> map = new HashMap<>();

// putting elements in a map
map.put("key1", "value1");
map.put("key2", "value2");

// getting element from a map & printing
String value1 = map.get("key1");
System.out.println(value1);

// getting all the keys of a map
Set<String> keys = map.keySet();

// getting all the values of a map
Collection<String> values = map.values();

// getting the size of a map
map.size();

// removing an element from a map
map.remove("key2");

// iterating over a map
for (Map.Entry<String, String> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " : " + entry.getValue());
}
```

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
 