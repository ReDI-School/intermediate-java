---
title: 14 - Project Instructions and Ideas
nav_order: 15
has_children: false
nav_exclude: false
---

# Final Project

## Project rules

- **Find a colleague to work with!**
- Choose and share your idea in the class' Slack channel before 23.05
- You will be working on the project until the end of the course
  - Teachers will follow the progress and support you
  - There will be an intermediate delivery
- Try to use what we learnt during the course
- You are free to use something that was not covered during the course
- The following ideas are meant as inspiration: you can use them, but why not coming up with your own?
- **Groups of maximum 3 people!**

## Schedule

- **16.05.2022**: Introduction (this class)
- **22.05.2022**: Final date for submission of group members and selected project 
- **23.05.2022**: Start of Project (creation of GitHub repository and sharing with teachers)
- **25.05.2022**: Working on the project
- **30.05.2022**: Working on the project
- **06.06.2022**: Intermediate delivery
- **08.06.2022**: Working on the project
- **13.06.2022**: Working on the project
- **15.06.2022**: Demo Day (final delivery)

## Project ideas

### 1 - Text analysis

#### Description:

Users enter text using the console. The application calculates statistics and show them to the user:

- amount of sentences
- amount of words
- the longest word
- the longest sentence
- top 5 most popular words in the text

#### Bonus:

If this is too simple, here some ideas how you can make the project more complex, potentially using more tools too:

- Read text from a file instead of from the console
- Application receives a path to a folder, checks all files in this folder and create a statistics as a json file for
  each file + a statistics for the folder, that contains:
    - How many files were processed
    - The longest text
    - The shortest text
    - The longest sentence
    - The longest word
    - The top 5 the most popular words across all the texts
- Read text from a web URL, or from an API (Twitter?)
- Add tests for your application

### 2 - Book Library

#### Description:

Build an application that allows us to catalogue and organize the books we lend to our users.

- Every book has an ISBN
- Using the ISBN we should be able to retrieve the details of the book from a public API e.g.
    - https://isbndb.com/
    - https://openlibrary.org/dev/docs/api/books
- We must be able to register a new book to the library. Note that we can have multiple copies of the same book.
- We must be able to remove a book from the store.
- Our users must be able to register at our library for a fee of 50 euros and when they do, they receive a library card.
- Users can visit the library to borrow one or multiple books for 1 euro each which is immediately withdrawn from the
  library card.
- The user cannot borrow a book if there is no money in the card.
- The user can then recharge the library card with more money.
- Every borrowed book must be returned after a week.
- Late returns are charged 10 cents for every day after the return period.
- The user can request to see their activity history.

### 3 - Phone Index

#### Description:

Using an interactive program operating through the console users should be able to

- save a new contact
    - First name
    - Last name
    - Phone numbers and label e.g. work, mobile, personal, private
    - addresses and label
    - additional information
- list all saved contact and their info
- modify existing contact
- delete existing contact
- search for contacts by name or phone number

#### Bonus:

If this is too simple, here some ideas how you can make the project more complex, potentially using more tools too:

- save contacts to file
- load contacts from a previously saved file
- generate a [QR Code](https://fileinfo.com/extension/vcf) for a contact.
- generate a [VCF file](https://fileinfo.com/extension/vcf) for a contact.
- generate a [CSV file](https://fileinfo.com/extension/csv) for all contacts.

### 4 - Accounting software

#### Description:

Users should be able to:

- add expenses and earnings through the console
- retrieve all previously inserted expenses and earnings
- receive summaries and balances

#### Bonus:

If this is too simple, here some ideas how you can make the project more complex, potentially using more tools too:

- save and load data to and from file, to use it later on
- have a simple user management system that allows different users to register and log in the system, and store their
  data in different files
- use a real db!

### 5 - Twitter analysis

#### Description:

A lot of things are said on Twitter every day - the analysis of tweets can be very valuable!
The user of your program should be able to select a tag/topic, anx the program could fetch the last tweets on the topic
and return some basic statistics

- most mentioned words (removing very common words?)
- most used emojis
- most active user

#### Bonus:

If this is too simple, here some ideas how you can make the project more complex, potentially using more tools too:

- you could use a graphing library to actually output nice graphs!

### 6 - Exercise Tracker (with persistence)

#### Description:

Users should be able to:

- select from a static list of possible exercises and enter when they did it & specific exercise-relevant information,
  e.g.
    - for running and biking: Duration & Distance
    - for weightlifting exercises: Weight & Repetitions
    - for football, basketball, ... : Duration, # of matches played
- get an easily readable list of exercises they did in the last x days/weeks/months
- The data they entered should not be lost when the application is closed - either with a database or a file-based
  storage.

#### Bonus:

If this is too simple, here some ideas how you can make the project more complex, potentially using more tools too:

- keeping track of the data of multiple users in parallel
- allowing the user to put in their weight and keep track of their weight change over the last x days/weeks/months
- calculating the calories burned whenever someone enters an exercise based on the exercise type, the provided details &
  the persons weight.

### 7 - Pacman console version

#### Description

In this project we would like to create a simple version of the famous game Pacman. You will have a 20 by 27 maze (you
can freely choose a different one than the original game), the maze contains dots, large flashing dots, ghosts and
pacman itself. For this simple version the game will be turn based, so each time you will get a prompt in the console to
choose in which direction pacman will go, of course the ghost move randomly, on each turn you move by one case only.
Game rule:

- Pacman has 3 life point, when pacman reach 0 life the game ends.
- Pacman has 2 state:
    - Defensive: pacman is eaten by the ghost.
    - Offensive: pacman can eat the ghost
- Pacman by default is in defensive state, only when he eats the large flashing dot he is an offensive state. The
  offensive state ends after 15 moves.
- When pacman is in defensive state and he is in the same case as a ghost, pacman dies, lose a life, los and go back to
  the initial case, the ghosts too return to the initial case.
- When pacman is in offensive state and he is in the same case as a ghost, he kills the ghost, the ghost goes back to
  the initial case. When pacman eats a ghost you can +100 in the score.
- When eating any type of dots, you get +5 in the score.
- If pacman manage to eat all the dots, the game end and pacman win.

PS: you can show the maze in the console as in the image below. G is for ghosts, P for pacman, O for large dots, . for
dots the others are obstacles.

![Pacman maze](pacman_console_grid.png)

#### Bonus

1. Add a leaderboard system, you can use files to save old scores.
2. Use a UI library to render the maze and the different characters in the game. You can use `libgdx` or search for
   a `Java 2d games library`.
3. Change the game to no be turn based but more dynamic as the original pacman game. (This is a tricky one)

### 8 - Groceries Delivery

Users should be able to (through the terminal):

- lookup for different product in different groups (bread, dairy, meat, fish, vegan)
- choose what products they want to deliver and how much
- see the order, before the confirmation
- confirm the order

#### Bonus:

If this is too simple, here some ideas how you can make the project more complex, potentially using more tools too:

- Read products and groups of the products from a file
- Use a db or a file to save all orders
- User should be able to:
    - see previous orders of this user
    - see statistics how much they paid per month
    - see statistics what product was ordered the most for the user
- Superuser (admin) should be able to
    - see all orders
    - see all users
    - see the most popular product
    - change any product price
- Add support for the distribution centers (so some product could be out of stock after the orders)
- Add tests for your application

### 9 - CV generator

Users should be able to:

- add personal details
- add contact details
- add a link to a photo
- generate a pdf version of the CV based on the entered data

#### Hint

- A library for pdf generation:
- https://www.baeldung.com/java-pdf-creation
- https://www.dunebook.com/best-java-pdf-generation-libraries/

### 10 - Instagram API
Use the instagram API to make something cool, for example:

Users should be able to enter a hashtag and get a list of accounts they can follow that use that hashtag.

The details of how you select these accounts is up to you - there's different ways with different levels of difficulty:
- Easy: Take the first 10 accounts you find that use that hashtag
- Medium: Recommend accounts first that have the most posts/followers/...
- Hard: Let the user select what's most important to them (follower #, post count, recently active, ...) 

**Note: An important part of this task will be reading the Instagram API documentation and understanding how to interact with it.**

### 11 - Spotify API

Use the spotify API to do something cool, for example:
User should be able to enter an artist and get 10 song recommendations

The details of how you select these songs is up to you - there's different ways with different levels of difficulty:
- Easy: Take the 10 most streaed songs of that artist
- Medium: Let the user pick an album, pick songs from that album first
- Hard: Mix in songs from similar artists


**Note: An important part of this task will be reading the Spotify API documentation and understanding how to interact with it.**

### 12 - Image Analysis

Java provides libraries to analyze images. You can do something cool with that, like:

Easy: User should be able to provide the path to a local image and the application prints the most dominant colors in that image
Medium: User should be able to provide the path to a folder with images and the user can search for colors. The application lists the images that use that color a lot.
Hard: After performing image analysis, store the information per image locally. Allow the user to add custom tags on top of the automatic color analysis. Provide the User the ability to search the folder based on tags. Tags should not be lost when the application restarts!

### 13 - Degrees

A Java program that would tell us how many "degrees of separation" apart two actors are.

You will be provided with two sets of CSV data files: one set in the large directory and one set in the small directory. Each contains files with the same names, and the same structure, but small is a much smaller dataset for ease of testing and experimentation.

Each dataset consists of three CSV files. A CSV file, if unfamiliar, is just a way of organizing data in a text-based format: each row corresponds to one data entry, with commas in the row separating the values for that entry.

Each dataset includes three files: 
1. `people.csv` in which you’ll see that each person has a unique id, corresponding with their id in IMDb’s database. They also have a name, and a birth year.
2. `movies.csv` in which you’ll see here that each movie also has a unique id, in addition to a title and the year in which the movie was released.
3. Finally, `stars.csv` which establishes a relationship between the people in `people.csv` and the movies in `movies.csv`. Each row is a pair of a `person_id` value and `movie_id` value. 

You can start with just outputting any relation between the two given actors. If you want a challenge think try to get **the shortest relation** between the actors!

### 14 - Image filtering app

A Java program that would take a path to an image through the command line and then offers the user a list of filters that they can apply to the image. The program would apply the filter to the image and save the new image on disk. The more filters the better!

For a bonus you can build a GUI for it (that IS how Instagram started, you know!) 

