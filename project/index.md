---
title: Project ideas
nav_order: 100
has_children: true
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
