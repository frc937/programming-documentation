---
description: A brief overview of basic Java concepts.
---

# Java Basics

This page is an _extremely_ brief overview of the basic concepts in Java, the language we program in on Team 937 (and which, according to our scouting data, roughly 80% of teams at the 2023 GKC regional used).

_Note to instructor_: If you are teaching this page as curriculum, I would recommend having students work through each concept by actually writing out code. The easiest way to do that for basic java is usually with an [online interpreter](https://www.onlinegdb.com/online\_java\_compiler). **If you're just reading through**, trying out examples in an editor like that can be helpful as well.

## Syntax

Java, like most programming languages, has some weird quirks of syntax—arguably, the most annoying part of programming.&#x20;

Code is separated into _lines,_ each line containing an instruction of some sort—usually a variable declaration or method call, which we'll learn about later. Each line ends with a _semicolon_ (`;`). Don't forget the semicolons, or your code won't run. For example:

```java
thisIsAValidLineOfJavaCode();
thisIsNotAValidLineOfJavaCode() // missing semicolon
```

Notice those two slashes in the example above? Those denote what is called a _comment_, which is a special bit of text in our code that we tell the compiler (basically, the piece of software that runs our code) to ignore. They're very useful for temporarily preventing a bit of code from being compiled or adding some information about your code that isn't immediately obvious from the code itself. Java also has a tool called JavaDoc, which takes a special kind of comment and auto-generates documentation from it—we'll learn more about it later. You'll see them a lot in the examples throughout the rest of this page. For example:

```java
// This is a Java comment
/* This is a Java comment
that spans multiple lines */
```

Java also has some components that require "blocks" of code. These are basically a header of some kind followed by some curly braces `{}` which then contain the code that that particular header requires. Examples of this include methods, loops, if statements, and classes; all of which we'll learn about later. For example:

```java
public SomeBlock {
    // We always indent the code inside the block to make it more readable
    // Code goes here, ofc
}
```

Lastly, we need to talk about _whitespace_, which is a programming term meaning any space or character that is blank, like spaces, tabs, or line breaks. Generally, in Java, spaces have meaning, while other kinds of whitespace do not.

For example, in the header for a block, there are generally several keywords and a name for that block, all of which need to be separated by spaces for our code to work. However, one could _technically_ write an entire java program on one line, because no returns nor tabs are actually required for the compiler to understand the code—in fact, the compiler completely ignores such characters. However, it is absolutely not recommended to do that, because it makes your code virtually completely unreadable. For example:

<pre class="language-java"><code class="lang-java">// The spaces in this declaration are required
public static void someBlock() {
<strong>    // Tecnically neither the line return nor the tab preceding this comment are
</strong>    // *required*, but if you ever don't include them I will go into your code and
    // add them for you.
}

public static void someBlock() { /* once again, technically, this is valid java code - but if you ever do this I will force you to not do it */ }
</code></pre>

## Variables

_Variables_ are one of the most basic concepts in Java (and programming in general). They are a way to store information. Essentially, if you have a piece of information that you need to keep track of, you can place it in a variable. You can then call that variable by its name to retrieve the value.

### Data Types

Every variable has a data type. This defines what kind of data the variable stores. There exist these basic data types (called "primitive data types"), out of which other data types can be constructed (we'll learn about that later):

* `int`
  * Whole numbers, also known as integers
* `double`
  * Numbers with decimals
* `boolean`
  * True/false values
* `char`
  * A single character
  * We don't use these much in FRC programming
* `String`
  * A string of characters, like a word or phrase
    * For example: "The quick brown fox jumps over the lazy dog"
  * These are actually constructed out of a series of char data types

Some data types can be converted to each other, like integers and doubles. Additionally, you can do basic arithmetic in variable assignments.

### Examples

```java
// Declaring variables
int myInt = 82;
double myDouble = 55.5;
boolean isRoboticsCool = true;
char myChar = 'A';
String myVar = "Hello!"

// Math in var assignments
int myMathInt = 82 + 45 * 16 / 8; // I have no idea what number that is

// Can also do math with other vars
int mySuperMathInt = myInt * myMathInt / myInt;
myInt += myMathInt; // same as myInt = myInt + myMathInt
myInt *= myMathInt; // same as myInt = myInt * myMathInt, same logic applies to -= and /=
myInt++; // adds one to myInt
myInt--; // subtracts one from myInt

// Converting between datatypes
double myDoubleFromInt = (double)myInt;
```

## Methods

Methods (as they are called in Java, most other languages call them functions) are essentially sections containing a few (or sometimes many) lines of code that we can then "call" from elsewhere in our code, basically running many lines of code by only typing one. They're extremely useful for when you need to reuse a piece of code, which actually happens a lot.&#x20;

Methods can also _return_ a piece of information, which means that they spit a value out when they're done running. This is useful if you'd like to take some data as input (that's another thing they can also do), do something to it, and then _return_ the modified data.&#x20;

This means that in Java, methods must have a _return type_, which tells our program which data type it should expect our method to return.

### Examples

```java
// Basic method, just prints out "Hello, world!"
// The `void` return type means it doesn't return anything
// We'll learn what the "private" part means in a minute
private void hello() {
    // Hey, look! We're calling another method within our method!
    // We'll learn what the `System.out` part is for in a minute
    System.out.println("Hello, world!");
}

// More complicated method, takes a couple of numbers and adds them together
private double addNumbers(double num1, double num2) {
    // This is technically a less efficient way to do this,
    // but it shows a bit more of what's going on
    double result = num1 + num2;
    return result;
}
```

## Classes and Objects

### Classes

Remember earlier, where we talked about how we can create our own data types? Classes are how we do that.

Classes have both variables and methods that belong to them. They generally represent, well, _something_.

Classes also have a constructor, which is a method that runs when a new _instance_ of the class is created (we'll learn more about that in a minute).

A common example of a class is a "dog" class. Such a class might have variables like `breed`, `color`, or `size`, which would be set by the constructor, and methods like `fetch()` or `sleep()`.

#### Example

```java
// Class names always start with upper-case letters
public class Dog {
    // These are instance variables, each instance of the object has a different
    // value for them
    // We'll learn more about them later
    private String breed;
    private String color;
    private String size;
    
    public Dog(String breed, String color, String size) {
        // New thing! The `this` keyword
        // It references the current object, we'll learn more about that later
        this.breed = breed;
        this.color = color;
        this.size = size;
    }
    
    public void fetch() {
        System.out.println("Bark!");
        System.out.println("*hands you a slobber-covered ball*");
    }
    
    public void sleep() {
        System.out.println("Zzzz...");
    }
}
```

At this point, you've probably noticed all the `public` and `private` keywords. Basically, something that is `public` can be accessed by other classes, while something that is `private` can't.

We _always_ make instance variables _private_, because that makes it so we can control how other classes can alter our instance variables. This makes it so that another class can't randomly set one of our instance variables to a value that would break our class—for example, if we had a counter variable that can only count up in one of our classes, we wouldn't want some other class to randomly reset our counter.

But then, how _do_ other classes change (or view) instance variables? With _getter_ and _setter methods_, of course! These do about what they sound like: getter methods return the value of an instance var, and setter methods set the value.

#### Example

```java
public class Dog {
    // (insert logic we already wrote for the dog class)
    
    // Getter method
    public String getBreed() {
        return this.breed;
    }
    
    // Setter method
    public void setBreed(String breed) {
        // A note about this: Java always prefers the parameter (the thing in
        // parentheses above) over the instance var, which is why we have to specify
        // that we mean the instance var with the `this` keyword
        this.breed = breed;
    }
}
```

### Objects

Objects are _instances_ of classes (you may remember instances because they were mentioned a couple of times in the classes section).&#x20;

You can think of each class like a blueprint for an object, and each object like a copy of something that was built with that blueprint.

You create objects by running the constructor for the object's class with the `new` keyword. Every object has _state_ that is independent of other objects of the same class, meaning that each object from a given class has _separate_ instance variables.

#### Example

```java
// Creating an instance of our Dog class from earlier
Dog myDog = new Dog("Chocolate Lab", "Brown", "Large");

// Will print out "Zzzz..."
myDog.sleep();

// Another instance
Dog myOtherdog = new Dog("Shiba Inu", "Tan", "Medium");
System.out.println(myDog.getBreed()); // Will print "Chocolate Lab"
System.out.println(myOtherDog.getBreed()); // Will print "Shiba Inu" - separate state!
```

#### Static Methods

Most methods must be a part of an instantiated object in order to work, that object's state. However, we can also declare methods—and even entire classes—with the `static` keyword, which makes it so that they can be run by simply calling the class name without having to first instantiate an object and then call the method on that object—but they also can't be called on an instantiated object.

#### Examples

```java
// Dummy class for example's sake (pretend its in a different file)
public class SomeClass {
    // ...
    
    // Defining a static method
    public static double doMath(double num1, double num2) {
        result = num1 * num2 / num1 + 10;
        return result;
    }
}

// Calling
double num = SomeClass.doMath(8, 15);
System.out.println(num);

// The Math class is also very useful, it's a built-in class that contains lots of
// methods for more advanced math than the basic arithmetic we can do with signs and
// symbols
System.out.println(Math.abs(-22)); // absolute value
System.out.println(Math.sqrt(64)); // square root
System.out.println(Math.pow(4, 2)); // 4 raised to the power of 2
```

## If/Else Statements

These are bits of code that only execute if a condition is met.

So IF (condition) is true, then do THING, ELSE IF (other condition) is true, do OTHER THING, ELSE (otherwise) do YET ANOTHER THING.

### Operators

But how, exactly, do we write out those conditions? With operators! (You can also use a method that returns a boolean.)

#### Comparison Operators

These are used to compare two values. They can be used to create boolean variables and are especially useful for creating conditions for if statements.

| Operator              | Sign |
| --------------------- | ---- |
| Equal                 | ==   |
| Not Equal             | !=   |
| Less Than             | <    |
| Greater Than          | >    |
| Less than or equal    | <=   |
| Greater than or equal | >=   |

#### Logical Operators

Allow you to combine multiple booleans or boolean expressions into one big boolean expression.

{% hint style="info" %}
**Lesson from Gabe:**

Be careful with these. It's WAY too easy to make massively long expressions that are impossible to read. (Or so she thinks, anyway.)
{% endhint %}

* NOT (!)
  * Evaluates a condition to the opposite boolean value
  * `!true = false`
* OR (||)
  * Evaluates true if ANY conditions in the expression are true
  * ONLY if all statements are false will the final expression be false
  * `true || false = true; true || true = True; false || false = false`
* AND (&&)
  * Evaluates true if ALL conditions in the expression are true
  * ONLY if all statements are true will the final expression be true
  * `true && true = true; true && false = false; false && false = false`

### Examples

```java
if (1 == 1) {
    // This code will run!
}

if (1 != 1) {
    // This code won't!
} else {
    // But this code will!
}

if (1 == 1 || 1 != 1) {
    // This code will run!
} else if (true || false) {
    // This code won't, even though the statement in parentheses is true, because
    // since if one if statement is true, all the other else-if statements are
    // skipped
} else {
    // This also won't run
}
```

## Loops

Loops do what they sound like, they allow us to execute a block of code over and over again until we decide we don't want to anymore.

### While Loops

While loops execute a block of code over and over again until a specified condition is false, or, in other words, WHILE a condition is true.

#### Examples

```java
while (true) {
    // This loop will run forever! (DON'T do this)
}

while (someMethodThatReturnsABoolean()) {
    // This loop will run until the method returns false
}

while (someVar > someOtherVar) {
    // This loop will run until someVar <= someOtherVar
}
```

### For Loops

For loops execute a block of code a specified number of times. _Technically_ anything you can do with a for loop, you can also do with a while loop, but using a for loop is generally more readable unless you're doing something _really_ weird.

For loops in Java look like this: `for (initialization; condition; increment)`.

1. The `initialization` is run first and only once. This allows you to initialize the variable you'll use to count how many iterations the for loop has gone through.
2. The `condition` is checked each time before the loop runs. Like a while loop, it is a statement that outputs a boolean, and if the bool is true, the loop keeps running, otherwise, it stops.
3. The `increment` is run each time after the loop. It is used to increment the variable that counts the loop's iterations.

#### Examples

```java
// This simple loop will execute a bit of code 10 times
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}

// It's technically the same as this while loop, but it's a lot cleaner
int i = 0;
while (i < 10) {
    System.out.println(i);
    
    i++;
}
```

## JavaDoc

Remember how we talked about comments all the way back at the beginning, and briefly mentioned a special type of comments called JavaDoc comments that help document your code?

JavaDoc comments can technically go above any kind of declaration, and will provide documentation for the declaration. This includes everything from variable declarations to methods to entire classes. However, they're most commonly used for methods and classes; rarely do we actually need to document the purpose of every single variable in every single class, especially since most of them are private.

Using tools provided by our build environment, we can actually make the JavaDoc comments into actual viewable documentation. The old-fashioned way of doing this is to generate an actual webpage out of it, which is actually still used quite a bit today—for example, you can view the JavaDoc for Phoenix V5, a library that we use a lot, here: [https://api.ctr-electronics.com/phoenix/release/java/](https://api.ctr-electronics.com/phoenix/release/java/). However, when writing our own code, we most commonly use the popup that's auto-generated by VS Code, which is the software we use for writing code for our robot.

### Examples

```java
// This comment won't be part of the JavaDoc for this class, but the one below it will
/**
 * This is Javadoc
 * <p>This class is an example class to teach about JavaDoc
 * <p>Oh, by the way, you can use some HTML tags in JavaDoc, if you know what those
 * are. Much like regular Java, JavaDoc ignores line returns, so if you want a line 
 * break in your JavaDoc, you'll need to.
 */
public class ExampleJavaDocClass {
    /** 
     * This JavaDoc will document myString, though we don't usually use JavaDoc
     * for variables
     */
    private String myString;
    
    // JavaDoc for methods is the most common use of JavaDoc
    // The @param below is a special type of syntax that JavaDoc uses, it allows us
    // to notate what different methods return and take as parameters, among other
    // things
    /**
     * Constructs a new ExampleJavaDocClass
     * @param myString Value to be stored in myString of ExampleJavaDocClass
     */
    public ExampleJavaDocClass(String myString) {
        this.myString = myString;
    }
    
    /**
     * Getter method for myString
     * @return The value of myString
     */
    public getMyString() {
        return myString;
    }
}
```
