---
title: Putting it all together
nav_order: 16
has_children: true
nav_exclude: false
---

# Lesson 16: Putting it all together

## Goals

- Learn how we can use the data structures we've learned about in order to solve real problems
- Use object oriented paradigms together with complex data structures
- *Get more confident transforming requirements into code*

## Lesson

Today's lesson is completely in the form of a long, interactive excercise. Here you find the outline of what we'll build. Afterwards, you can find a similar exercise to try later.

### Where do we spend money?

Today we will work for a Bank. Our bank wants to implement a new feature for our users. Our users would like to get Statistics where do they spend money and how much. The bank stores information about different payment. Each 
Payment has a unique id, amount, type (for example groceries, entertainment, cafes, house holding, transport ...) and month and year when the payment happened. Our users want to get 
statistics what was the most expensive payment, what was the biggest income that they got, how much they spend and earned in total and how much they paid for each type of the payment.

#### Let's start with structures
What structures do we need? Let's create them!
 
#### Let's add some data
Let's add some payments in our bank. Pay attention, how we make sure that the payments are unique? How are we going 
to store them?

#### Let's do some calculations!
Show the user their the most expensive payment:

```
The biggest payment is: 2001003 [-200$, "Groceries", 2019, October]
```
 
#### Let's do some calculations! 
Show the user their total income:

```
The total income is: 2000$
```
  
#### Let's do some grouping!
Show the user their spending grouped by type, alphabetically ordered by the type name:

```
How do spend your money:
Cafes: 128$
Entertainment: 26$
Groceries: 150$
...
```  

#### Let's get some input from the user 
Give the user opportunity to choose what statistics they want to see:
```
> Enter what statistics you want to see: 
1 - My biggest payment
2 - My total income
3 - How do I spend my money
0 - exit

```

#### Tip - How switch works: 
```java
public class SwitchDemo {
    public static void main(String[] args) {

        int month = 8;
        String monthString;
        switch (month) {
            case 1:  monthString = "January";
                     break;
            case 2:  monthString = "February";
                     break;
            case 3:  monthString = "March";
                     break;
            case 4:  monthString = "April";
                     break;
            case 5:  monthString = "May";
                     break;
            case 6:  monthString = "June";
                     break;
            case 7:  monthString = "July";
                     break;
            case 8:  monthString = "August";
                     break;
            case 9:  monthString = "September";
                     break;
            case 10: monthString = "October";
                     break;
            case 11: monthString = "November";
                     break;
            case 12: monthString = "December";
                     break;
            default: monthString = "Invalid month";
                     break;
        }
        System.out.println(monthString);
    }
}
```

#### Let's do some calculations! 
Show the user their biggest income:

```
The biggest income is: 2001003 [1200$, "Income", 2019, October]
```

#### Let's do some calculations! 
Show the user their total spending:

```
You spent in total: -278$
```

#### Let's do some grouping!
Show the user their spendings & earnings grouped by month during this year, chronologically ordered. Make sure that 
you print the month even if there are no payments.

```
In January you spent: 143$ and earned: 2300$
In February you spent: 260$ and earned: 2300$
In March you spent: 0$ and earned: 2300$
In April you spent: 107$ and earned: 2500$
...
```

#### Let's do some grouping!
Show the user their spendings & earnings grouped by month during chosen year, chronologically ordered. Make sure that 
you print the month even if there are no payments. For that you will need to make the bank terminal menu more 
interactive:
```
> Enter what statistics you want to see: 
1 - My biggest payment
2 - My total income
3 - How do I spend my money
4 - Statistics for 1 year
0 - exit

User's input> 4

> Enter a year: 

User's input> 2018

In January 2018 you spent: 143$ and earned: 2300$
In February 2018 you spent: 260$ and earned: 2300$
In March 2018 you spent: 0$ and earned: 2300$
In April 2018 you spent: 107$ and earned: 2500$
...
```

#### Let's add some people 
"Split the bill" application. Two or more people can use this application to see who owes money to whom. Each payment is made by one user for others. 
Show the previous statistics for the users. How much a user has payed each month. How much money should be payed back or received by this user from other users. 

When add a payment specify what user made this payment. 

In the menu that was implemented in the previous tasks add as the first step choosing the user,than show statistics for the chosen user. 
