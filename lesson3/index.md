---
title: Git
nav_order: 3
has_children: true
---

# Lesson 3: Git, GitHub & Integration with Intellij

## Goals
* Learn about Git & GitHub
* Create a GitHub account
* Connect Intellij & GitHub
* Import a project from GitHub
* Export a project to GitHub
* Apply changes and save them with GitHub
* Look in the changes log
* More java if we have time 🤩

## Recap & Homework check
Let's look into the homework from lesson 1 & 2

## Version Control
Version control is like a savings program for your project. 
By tracking and logging the changes you make to your file or file sets over time, a version-control system gives you the power to review or even restore earlier versions. 
Version control takes snapshots of every revision to your project. You can then access these versions to compare or restore them as needed.

Questions that Version control helps to answer
- Which changes were made?
- Who made the changes?
- When were the changes made?
- Why were changes needed?

## Git
Git is an extremely popular version control system that is at the heart of a wide variety of high-profile projects.
Git is a distributed version-control system for tracking changes in source code during software development. 
It is designed for coordinating work among programmers, but it can be used to track changes in any set of files

![git-logo](git-logo.png)

### Install Git 
https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

## GitHub
GitHub is a cloud-based hosting service that lets you manage Git repositories.
https://github.com/

![github-logo](github-logo.jpg)

Let's create a free account at GitHub (Demo)

Other Git repository hosting services also exist: GitLab, BitBucket, and SourceForge 

## Git Commands
Some of the git commands that are behind Intellij Magic 
* git add
* git commit
* git push 
* git pull (fetch & merge)
* git init
* git clone

### git add
Adds a change in the working directory
Tells Git that you want to include updates to a particular file in the next commit. 
Doesn't really affect the repository in any significant way

### git commit
Is used to save your changes to the local repository.
You have to explicitly tell Git which changes you want to include in a commit 
A file won't be automatically included in the next commit just because it was changed.

### git push 
Is used to upload local repository content to a remote repository. 
Pushing is how you transfer commits from your local repository to a remote repo.

### git pull
Is used to fetch and download content from a remote repository and immediately update the local repository to match that content. 
Is actually a combination of two other commands, git fetch followed by git merge.

### git clone
Cloning a local or remote repository

## Intellij & GitHub Integration
- In Intellij: Integrate Intellij with GitHub (Demo)

## GitHub -> Intellij
- In GitHub: Create a project
- In Intellij: Import project from GitHub (File -> New -> Project from Version Control)
- In Intellij: Change files, commit and push changes to GitHub
- In Intellij: Add a new file, commit and push changes to GitHub
- In Intellij: Remove a file from the project, commit and push changes to GitHub

## Intellij -> GitHub
- In Intellij: Create a new project, add a Java class
- In Intellij: Share your Project on GitHub 
    - VCS -> Commit
    - VCS -> Import into Version Control -> Share Project on GitHub
- In Intellij: Change files, commit and push changes to GitHub
- In Intellij: Add a new file, commit and push changes to GitHub
- In Intellij: Remove a file from the project, commit and push changes to GitHub

## History 
Check version control history
- In Intellij: Version Control -> Log
- In GitHub: Your Repository -> Code -> Commits 

![git-history](git-history.png)

## Some Java
### Integer array stats
Write a Java Program that finds a minimum value in the given array of integers. 
Add it to your GitHub profile.

Add a method to find a maximum value. 
Add it to your GitHub profile.

Add a method to find an average. 
Add it to your GitHub profile.

Can you do it in 1 loop?
Add the changes to your GitHub profile.

Look into the git history 

### Palindrome string
Write a Program that checks that a given string is a palindrome. 
A string is Palindrome if position of each character remain the same in case even string is reversed. 
For example 'MADAM' is a palindrome string as position of each character remain same even if string 'MADAM' is reversed.

Add it to your GitHub profile

### Vowels counter
Write a Java method to count all vowels (English Alphabet) in a string.

- Test Data: Input the string: this is a String.
- Expected Output: Number of  Vowels in the string: 4

- Test Data: Input the string: Are you checking Upper case?
- Expected Output: Number of  Vowels in the string: 10

Add it to your GitHub profile.

### Longest word
Given an array of Strings, find the longest String in the array.
Add it to your GitHub profile

Add a method to find a longest word in the sentence, assume that input has only english alphabet and spaces
Add it to your GitHub profile

Can you reuse the first method in the second method?
If there are some changes, you know what to do -> add it to your GitHub profile!

### Factorial 
Write a program that calculates the factorial of a positive integer n, factorial is the product of all positive integers less than or equal to n: 
For example, The value of 0! is 1, according to the convention for an empty product
4! = 1*2*3*4 = 24

Add it to your GitHub profile

## Homework
Upload your code from the previous classes to your GitHub profile & Finish the java tasks

## Materials
- https://git-scm.com/ 
- https://www.jetbrains.com/help/idea/github.html
- https://guides.github.com/introduction/git-handbook/
