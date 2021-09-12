---
title: Project ideas
nav_order: 0
has_children: true
nav_exclude: true
---
# Project 

## Project rules 
- Find a colleague to work with!
- Choose and share your idea in the class' Slack channel before 25.11
- You are working on the project until the end of the course
- Try to use what we learnt during the course
- You are free to use something that was not covered during the course
- The following ideas are meant as inspiration: you can use them, but why not coming up with your own?

## Project ideas
### Text analysis 
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

####  From the course, you'll use:
- OOP
- Data Structures 
- Tests
- File IO

####  You will need to learn yourself: 
- String operations

###  Book Library
#### Description:
Build an application that allows us to catalogue and organize the books we lend to our users.

- Every book has an ISBN
- Using the ISBN we should be able to retrieve the details of the book from a public API e.g. 
  - https://isbndb.com/
  - https://openlibrary.org/dev/docs/api/books
- We must be able to register a new book to the library. Note that we can have multiple copies of the same book.
- We must be able to remove a book from the store.
- Our users must be able to register at our library for a fee of 50 euros and when they do, they receive a library card.
- Users can visit the library to borrow a one or more books for 1 euro which is immediately withdrawn from the library card.
- The user cannot borrow a book if there is no money in the card.
- The user can then recharge the library card with more money.
- Every borrowed book must be returned after a week.
- Late returns are charged 10 cents for every day after the return period.


###  Phone Index
#### Description:
Using an interactive program operatin through the console users should be able to 
- save a new phone number for a contact
- list all saved contact and their phone numbers
- add new numbers for already-saved contact, delete existing numbers
- search for contacts by name or phone number

#### Bonus: 
If this is too simple, here some ideas how you can make the project more complex, potentially using more tools too:

- save contacts to file
- load contacts from a previously saved file

####  From the course, you'll use:
- OOP
- Data Structures 
- Tests
- File IO

####  You will need to learn yourself:
- String operations

### Accounting software
#### Description:
Users should be able to:
- add expenses and earnings through the console
- retrieve all previously inserted expenses and earnings
- receive summaries and balances

#### Bonus: 
If this is too simple, here some ideas how you can make the project more complex, potentially using more tools too:

- save and load data to and from file, to use it later on
- have a simple user management system that allows different users to register and log in the system, and store their data in different files
- use a real db!

#### From the course, you'll use:
- OOP
- Data Structures 
- Tests
- File IO

####  You will need to learn yourself: 
- String operations
- Potentially, simple database operations

### Twitter analysis
#### Description:
A lot of things are said on Twitter every day - the analysis of tweets can be very valuable!
The user of your program should be able to select a tag/topic, anx the program could fetch the last tweets on the topic and return some basic statistics

- most mentioned words (removing very common words?)
- most used emojis
- most active user

#### Bonus:
If this is too simple, here some ideas how you can make the project more complex, potentially using more tools too:

- you could use a graphing library to actually output nice graphs!

####  From the course, you'll use:
- OOP
- Data Structures 
- Tests
- File IO

####  You will need to learn yourself: 
- using Twitter Java API (maybe [http://twitter4j.org/en/](http://twitter4j.org/en/)? )
- potentially, using a graphing library

### Exercice Tracker (with persistence)
#### Description:
Users should be able to:
- select from a static list of possible exercises and enter when they did it & specific exercice-relevant information, e.g.
  - for runnning and biking: Duration & Distance
  - for weightlifting exercices: Weight & Repetitions
  - for football, basketball, ... : Duration, # of matches played
- get an easily readable list of exercices they did in the last x days/weeks/months
- The data they entered should not be lost when the appliction is closed - either with a database or a file-based storage.

#### Bonus: 
If this is too simple, here some ideas how you can make the project more complex, potentially using more tools too:

- keeping track of the data of multiple users in parallel
- allowing the user to put in their weight and keep track of their weight change over the last x days/weeks/months
- calculating the calories burned whenever someone enters an exercice based on the exercice type, the provided details & the persons weight.

#### From the course, you'll use:
- OOP
- Data Structures 
- Tests
- File IO

####  You will need to learn yourself: 
- Potentially, simple database operations
=======

### Pacman console version

#### Description
In this project we would like to create a simple version of the famous game Pacman. You will have a 20 by 27 maze (you can freely choose a different one than the original game), the maze contains dots, large flashing dots, ghosts and pacmac itself. For this simple version the game will be turn based, so each time you will get a prompt in the console to choose in which direction pacman will go, of course the ghost move randomly, on each turn you move by one case only. 
Game rule:
- Pacman has 3 life point, when pacman reach 0 life the game ends.
- Pacman has 2 state:
    - Defensive: pacman is eaten by the ghosts.
    - Offensive: pacman can eat the ghots
- Pacman by default is in defensive state, only when he eats the large flashing dot he is an offensive state. The offensive state ends after 15 moves.
- When pacman is in defensive state and he is in the same case as a ghost, pacman dies, lose a life, los and go back to the initial case, the ghosts too return to the initial case.
- When pacman is in offensive state and he is in the same case as a ghost, he kills the ghost, the ghost goes back to the initial case. When pacman eats a ghost you can +100 in the score.
- When eating any type of dots, you get +5 in the score.
- If pacman manage to eat all the dots, the game end and pacman win.

PS: you can show the maze in the console as in the image below.
G is for ghosts, P for pacman, O for large dots, . for dots the others are obstacles.

![Pacman maze](pacman_console_grid.png)
#### Bonus
1. Add a leaderboard system, you can use files to save old scores.
2. Use a UI library to render the maze and the different characters in the game. You can use `libgdx` or search for a `Java 2d games library`.
3. Change the game to no be turn based but more dynamic as the original pacman game. (This is a tricky one)

### Groceries Delivery  
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
- Super user (admin) should be able to 
  - see all orders
  - see all users
  - see the most popular product
  - change any product price
- Add support for the distribution centers (so some product could be out of stock after the orders)
- Add tests for your application

####  From the course, you'll use:
- OOP
- Data Structures 
- Tests
- File IO

####  You will need to learn yourself: 
- Work with DBs, if you want to use the db

### CV generator

Users should be able to:
- add personal details
- add contact details
- add a link to a photo
- generate a pdf version of the CV based on the entered data

####  From the course, you'll use:
- OOP
- Data Structures 
- Tests
- File IO

#### Hint 

- A library for pdf generation: 
  - https://www.baeldung.com/java-pdf-creation
  - https://www.dunebook.com/best-java-pdf-generation-libraries/