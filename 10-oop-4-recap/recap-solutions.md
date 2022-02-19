---
title: "Solutions to recap OOP4"
nav_order: 2
parent: "10 - OOP4 Classes, Abstract Classes & Interfaces Recap"
nav_exclude: false
---

## Java trivia

### Question 1 - Constructors

Which numbers will be printed out:

```java
public class JavaTriviaOne {

  public JavaTriviaOne() {
    System.out.println(number);
    number = 5;
  }

  public static void main(String[] args) {
    JavaTriviaOne one = new JavaTriviaOne();
    System.out.println(one.number);
  }

}
```

**Answer**: the program will not compile as it is. We need to first `declare` a class variable `number`. Note the terminology use here: we declare a variable in the beginning of the class, and then instantiate it (assigning memory space) in the constructor.
After being corrected, our program will then print out in the first line `0` (zero), since java has predefined values for primitive data types (and `null` as a default for all Objects). More information can be found in [Oracle documentation here](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
In the second line it will print 5.


### Question 2 - Constructors

Which number will be printed out:

```java
public class JavaTriviaTwo {

  public JavaTriviaTwo() {
    number = 5;
  }

  public static void main(String[] args) {
    JavaTriviaTwo one = new JavaTriviaTwo();
    System.out.println(one.number);
  }

  private int number = 3;

  {
    number = 4;
  }

}
```

**Answer**: The correct answer is: 5.

### Question 3 - Constructors

Which numbers will be printed out:
```java

public class JavaTriviaThree {

  int num1;
  int num2;
  int num3;

  public JavaTriviaThree() {
    int num1, num2, num3 = 5;
    this.num1 = num1;
    this.num2 = num2;
    this.num3 = num3;
  }

  public static void main(String[] args) {
    JavaTriviaThree one = new JavaTriviaThree();
    System.out.println(one.num1);
    System.out.println(one.num2);
    System.out.println(one.num3);
  }

}
```

**Answer**: this program does not compile, because variable `num1` and `num2` are declared but not initialized.
Local variables are different, in that java will not assign a default value to them. The compiler never assigns a default value to an uninitialized local variable. If you cannot initialize your local variable where it is declared, make sure to assign it a value before you attempt to use it. Accessing an uninitialized local variable will result in a compile-time error.
Thus, one example how to fix this code would be:

```java
int num1 = 2, num2 = 1, num3 = 5;
```

### Question 4 - methods

Why doesn't this code compile?
```java
public class JavaTriviaFour {

  private final int questionNumber;

  public JavaTriviaFour() {
    questionNumber = 4;
  }

  void public think() {
    System.out.println("To compile or not compile, that is the question");
  }

}
```

**Answer**: the order of method declaration does matter. Access modifiers (public/protected/private) have to come before return type (for example `void` or `String`).

More information available [here](https://docs.oracle.com/javase/tutorial/java/javaOO/methods.html)

### Question 5 - classes

We want to define a general concept for any type of bird that serves as a base for other developers to extend. Thus, we created the following `Bird` class:
```java

// file 'Bird.java'
class Bird {
   public String getName() { return null; }
   public void printName() {
      System.out.print(getName());
   }
}
 
// .. and in another file 'Stork.java'
public class Stork extends Bird {
   public String getName() { return "Stork!"; }
   public static void main(String[] args) {
      new Stork().printName();
   }
}
```

How could this code be improved?

- we do not want other developers to instantiate any Bird class;
- if other developers forget to override the getName() they will print 'null' when calling printName(), which is not what we want.

Solution:

```java
// file 'Bird.java'
abstract class Bird {
    public abstract String getName();
    public void printName() { 
        System.out.print(getName()); 
    }
}

// .. and in another file 'Stork.java'
public class Stork extends Bird {
    @Override
    public String getName() { return "Stork!"; }
    public static void main(String[] args) { 
        new Stork().printName(); 
    }
}
```

### Question 6 - classes

We want to define a general concept for any type of animal that serves as a base for other developers to extend. Therefore, we created the following `Animal` class:
```java
// file 'Animal.java'
public class abstract Animal { 
   
    public Animal() {
        System.out.println("Trust me, I'm an animal.")
    }
    
    public String abstract getSpecies() {
        return "dog";
    }
}

// file 'Bear.java'
public class Bear extends Animal {
  public static void main(String[] args) {
    Animal grizzly = new Bear();
  }
}
```

How could this code be improved?

This code does not even compile successfully, for it has several mistakes embedded into it. Let us list those mistakes:
- **invalid class declaration**: the `abstact` keyword needs to be declared before `class` keyword; like the `final` modifier, the `abstract` modifier can be placed before or after the access modifier in class declarations, so one correct way would be: `public abstract class Animal {`
- **invalid method declaration**: wrong order of method declaration again; the `abstract` modifier can be placed before or after the access modifier in method declarations, so one correct way would be: `abstract public String getSpecies() {`
- **abstract methods cannot be implemented**: one can only declare an abstract method, but not implement it. Even an empty declaration would not compile: `abstract public String getSpecies() {}`; The correct way would be: `abstract public String getSpecies();`

In case you were thinking that the compiler will not accept the absence of constructor in the `Bear` class, that is OK.
The compiler inserts a default no-argument constructor into the `Bear` class, which first calls `super()` in the `Bear` class.


### Question 7: Improvements to `Product` class

What could be improved in this `Product` class:
```java
public class product {

  String color;
  int price;

  public product(String color, int price) {
    this.color = color;
  }
  
  public String GetColor() {
      return null;
  }

}

```

There are several things that could be improved in the previous class `Product`, and by now we have the knowledge to do it:
- **Naming conventions related improvements**:
  class names first letter of each internal word capitalized; methods should be verbs, in mixed case with the first letter lowercase, with the first letter of each internal word capitalized. More information about java naming conventions available [here](https://www.oracle.com/java/technologies/javase/codeconventions-namingconventions.html)
- **Make class variables private**: this is also referred to as [encapsulation](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming)), and the point is to keep internal data hidden from other classes, which should only access behavior by calling methods on the class, not by changing the values directly;

```java
public class ProductImproved {

  private String color;
  private int price;

  public ProductImproved(String color, int price) {
    this.color = color;
    this.price = price;
  }

  public String getColor() {
    return color;
  }

  public int getPrice() {
    return price;
  }

  public void setColor(String color) {
    this.color = color;
  }

  public void setPrice(int price) {
    if (price < 0) {
      System.out.println("Price cannot be negative!");
      return;
    }
    this.price = price;
  }

  @Override
  public boolean equals(Object o) {
    if (this == o) {
      return true;
    }
    if (!(o instanceof ProductImproved)) {
      return false;
    }

    final ProductImproved that = (ProductImproved) o;

    if (getPrice() != that.getPrice()) {
      return false;
    }
    return getColor().equals(that.getColor());
  }


  @Override
  public int hashCode() {
    int result = getColor().hashCode();
    result = 31 * result + getPrice();
    return result;
  }


  @Override
  public String toString() {
    return "Product{" +
           "color='" + color + '\'' +
           ", price=" + price +
           '}';
  }
  
}
```

## Assignment

## [Abstract classes and interfaces assignment](https://classroom.github.com/a/nlIfekz9)


### Task 1 - start by implementing text normalization in `TextProcessor` class

```java

@Override
public String removeNewLineSeparators(String text) {
        return text.replaceAll(System.getProperty("line.separator"), " ");
}


@Override
public String removePunctuation(String text) {
        return text.replaceAll("[^a-zA-Z0-9 ]", "");
}


@Override
public String lowerCaseAllWords(String text) {
        return text.toLowerCase();
}

```

### Task 2: implement interface methods of `StatisticsAnalyzer` in `SentimentProcessor` class

```java

@Override
public Set<String> extractRelevantWords(List<String> words) {
final Set<String> relevant = new HashSet<>();
        for (String word: words) {
            if (dictionary.getAllWords().contains(word)) {
                relevant.add(word);
            }
        }
        return relevant;
}

@Override
public Map<String, Integer> extractRelevantWordsCount(List<String> words) {
    final Map<String, Integer> counts = new HashMap<>();
    for (String token: words) {
        if (dictionary.getAllWords().contains(token)) {
            final Integer count = counts.getOrDefault(token, 0);
            counts.put(token, count + 1);
        }
    }
    return counts;
}

```

### Task 3: implement interface method of `SentimentAnalyzer` in `SentimentProcessor` class

```java

@Override
public Sentiment extractMood(final Map<String, Integer> wordCount) {
        int countPositive = 0;
        int countNegative = 0;
        for (Map.Entry<String, Integer> entry: wordCount.entrySet()) {
            if(dictionary.getPositive().contains(entry.getKey())) {
                countPositive += entry.getValue();
            } else if (dictionary.getNegative().contains(entry.getKey())) {
                countNegative += entry.getValue();
            }
        }
        if (countPositive > countNegative) {
            return Sentiment.POSITIVE;
        } else if (countPositive == countNegative) {
            return Sentiment.NEUTRAL;
        } else {
            return Sentiment.NEGATIVE;
        }
}
```
