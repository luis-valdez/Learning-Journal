### How do Lambda expressions work on Java?
​
**What is a Lambda?**
According to O'Reilly book 'Java in a Nutshell', the definition of a lambda goes like this:
>A lambda expression is essentially a function that does not have a name, and can be treated as a value in the language. As Java does not allow code to run around on its own outside of classes, in Java, this means that a lambda is an anonymous method that is defined on some class (that is possibly unknown to the developer).
​
The synax of the lambda function looks like this:
```java
( paramlist ) -> { statements }
```
And the traditional example is:
```java
Runnable r = () -> System.out.println("Hello World");
```
Here we are assigning the lambda to a variable that is an instance of the class `Runnable`.
​
A pretty common use for lambdas is passing them as parameters to other methods. For example:
```java
import java.util.ArrayList;
​
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
​
Lambdas can be used for many purposes. Another cool example that I found online was for filtering a list:
```java
File dir = new File("/src"); // The directory to list
String[] filelist = dir.list((d, fName) -> fName.endsWith(".java"));
```
Here we have a variable called dir that contains an instance of File that represents a directory. We access a lsit with `dir.list` and then we pass the lambra as a parameter. In this lambda we have to parameters. `d` that represents each element on the list and `fName` that is the name of each file.
Then in the second part of the lambda (the statement), we just put a simple conditional to decide if we're going to include a certain file in our `filelist`. That criteria is just a simple method that returns true if the file name ends with `.java`
​
Lambdas are a very extensive subject and also a very exciting one. The reason I chose to learn more about them is because I'm starting to get involved in an OpenSource project, and I'm trying to get familiar with the code, so naturally I walked upon to a lot of lambdas and was unable to understood them. That until I took the time to read about them and understood their potential.
​
