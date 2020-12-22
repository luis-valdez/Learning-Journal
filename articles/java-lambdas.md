# How do Lambda expressions work on Java?
In order to answer this question, lets start with a more simple one.

## 1. What is a Lambda?
According to O'Reilly book 'Java in a Nutshell', the definition of a lambda is:
>A lambda expression is essentially a function that does not have a name, and can be treated as a value in the language. As Java does not allow code to run around on its own outside of classes.


The synax of the lambda function:
```java
( paramlist ) -> { statements }
```
And the traditional example is:
```java
Runnable r = () -> System.out.println("Hello World");
```
Here we are assigning the lambda to a variable that is an instance of the class `Runnable`.

## 2. Examples
A pretty common use for lambdas is passing them as parameters to other methods. For example:
```java
import java.util.ArrayList;
public class Main {
  public static void main(String[] args) {
    ArrayList<Integer> numbers = new ArrayList<Integer>();
    numbers.add(5);
    numbers.add(9);
    numbers.add(8);
    numbers.add(1);
    numbers.forEach( (n) -> { System.out.println(n); } );
  }
}
```
Here we are creating an ArrayList of numbers and then using the forEach method that comes with the object. Then we pass a lambda as a parameter to that method. In each iteration of the `.forEach` we will be using the lambda function. Passing it a specific number from the `numbers` iteration and then using a good old print for each number.

Lambdas can be used for many purposes. Another cool example I found online was for filtering a list:
```java
File dir = new File("/src"); // The directory to list
String[] filelist = dir.list((d, fName) -> fName.endsWith(".java"));
```
Here we have a variable called dir that contains an instance of File that represents a directory. We access a list with `dir.list` and then we pass the lambda as a parameter. In this lambda we have two parameters. `d` that represents each element on the list and `fName` that is the name of each file.
Then in the second part of the lambda (the statement), we just put a simple conditional to decide if we're going to include a certain file in our `filelist`. That criteria is just a simple method that returns true if the file name ends with `.java`


## 3. Are lambdas defined as some part of a class?

According to the documentation
>At run time, evaluation of a lambda expression is similar to evaluation of a class instance creation expression, insofar as normal completion produces a reference to an object.

This is related with the fact that when we use a lambda, we generally use a functional interface. For example:
```java
Predicate<Integer> greaterThan5 = x -> x > 5;
System.out.println(greaterThan5.test(6)); // Prints true
```
Here `Predicate` is a functional interface, and we're creating an instance of it taking advantage of the Lambda. This is very similar to a `Anonymous Class`.

To answer the question, depending on where and how you use the Lambda it will be used to instance a functional interface. There is nothing like "Lambda Class" in java.

The way it works is that when the compiler sees a lambda expression, it tries to convert it to an instance of the functional interface type you are trying to target. It's just a special syntax in java, not a particular class.

## 4. Can you do operations with Lambdas?
The short answer is no. However you can do operations inside Lambdas and use it with a functional interface. For example:
```java
BinaryOperator<Double> addDoubles = (x, y) -> x + y;
System.out.println(addDoubles.apply( 1.1, 1.1) + 1); //Prints 3.2
```
The other question you might be asking could be

### 4.1 Why can't you do operations with Lambdas?
Lambdas are useful for defining some behavior and passing it to a functional interface for them to use it. Trying to make operations with Lambdas would be like trying to make a sum with the initialization of two objects.

## 5. Do they have any special restrictions?
The Lambda Expression can be written in different ways, so the syntax changes depending on the case. There exist many combinations that represent different scenarios, here are the main aspects that can vary:

### 5.1. The functional interface takes 0 parameters and has no return value

```java
public interface MyFunction {
    public void apply();
}
```
The implementation: 
```java
public static void main(String [] args){
	MyFunction myPrinter = () -> { System.out.println("Hello World"); };
	myPrinter.apply();
}
```
Because the functional interface has no parameters and no return value, the lambda follows that same structure.

**Note**: Because we're only using a single statement we can write our lambda body without curly braces.
```java
MyFunction myPrinter = () -> System.out.println("Hello World");
```
### 5.2. The functional interface takes 1 paremeter and has no return value
```java
public interface MyFunction {
    public void apply (String text);
}
```
The implementation:
```java
public static void main(String [] args){
	MyFunction myPrinter = (String text) ->  { System.out.println(text); };
	myPrinter.apply("Hello World"); //prints Hello World
}
```
See that now we have to pass a parameter?

**Notes:** 

- Our lambda can infer that the parameter is a String, because it's already defined in the interface. So we can omit the `String` keyword in the parameters.
- Because we're only passing a single parameter, we can omit the parentheses.

This is how our lambda would look like implementing all of the previous notes:
```java
MyFunction myPrinter = text -> System.out.println(text);
```
As you can see the syntax got much shorter, but the functionality reminds the same.

### 5.3. The functional interface takes 2 parameters and has a return value
```java
public interface MyFunction {
    public String greet (String firstName, String lastName);
}
```
The shortest implementation:
```java
public static void main(String [] args){
	MyFunction myPrinter = (firstName, lastName) -> "Hi! "+ firstName + " " + lastName;
	System.out.println(myPrinter.greet("Luis","Valdez")); //prints Hi! Luis Valdez
}
```
**Notes**: 
- Here the parentheses are obligatory because we have more than one parameter, if we try too omit them we would get an error.
- The body of the lambda represents the return value, which is a String.
- We have to meet with the conditions of the interface, our lambda must have two parameters and a return value of the type String. Otherwise we will get an error.

### 6. Conclusion
Lambdas are a extensive subject, but you don't need to be an expert to actually take advantage of them and start using them. This article aimed for the main functionality of Lambda Expressions, which will get you started.

It's important to to notice that there a lot of ways to implement them, some of them are matter of personal preference, such as including curly brackets or parentheses, and some of them are a matter of the specific case you're facing.
