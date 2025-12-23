---
title: "Exercise - Video Store"
nav_order: 0
parent: "09 - Data Structure - Set & Map"
nav_exclude: false
---

# Lesson 9: Data Structure - HashMap

1. Create a new class Movie with title, director and year.
2. Add a toString, equals and hashCode function to the class
3. Create some instances of the Movie class in the Main method, add them to a hashmap (Hashmap<Movie, Integer> where the second parameter represents the number of available copies of this movie) and test if your implementation works as expected.
4. Think about other properties of the movie class and adjust the methods mentioned in 2.
5. Extract the code from 3 into a new class Movie-Store, where a user can buy a movie, which will reduce the number of movies in the stock.
6. Build an text menu for your program where a user can buy a movie from the store.
- The program shall ask a user for his actions:
1. For list all available movies (Method signature public void printAvailableMovies())
2. Buy a movie (Method signature public void buyMovie(String title, String director, int year))
3. Quit the process
The user can execute the program when choosing option 3
