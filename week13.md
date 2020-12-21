# Week 13

This was my 13th week working in the Academy internship, and as always there was a lot of learning involved. Let's begin.

## Java Learnings

### Dependency Injection
As part of my preparation for my upcoming interview I'm working on some fundamentals, among them, Dependency Injection.

In OOP objects often have depencencies, you create an object that needs from another object. This is how this looks without DI:
```java
public class Store {
    private Item item;
 
    public Store() {
        item = new ItemImpl1();    
    }
}
```
 And this is how we would do it with DI:
 ```java
 public class Store {
    private Item item;
    public Store(Item item) {
        this.item = item;
    }
}
```
 As you can see, the difference relies in how you don't actually instantiate the Item object inside the constructor. Instead you pass it as a parameter and make a reference that you will be using the item correspondent to the instance of that Store.
 
 The big advantage that this architecture provides is that it makes your code less tightly coupled and it gives you the chance to later switch to a different implementation.


### The 4 principles of OOP
This week was a great opportunity to revisit the 4 principles of OOP. Here's each one of them and how I undersand them with my own words:

**Encapsulation:** Is the practice of making the data of a certain class private or only accessible through the methods of the class.


**Abstraction:** Is the practice of defining how a certain class should behave or be constituted with worrying about the how. In java this is achieved thanks to interfaces and abstract classes.
 
**Inheritance:** In java inheritance is when a parent class passes it fields and methods to a child class. This is achieved thanks to the `extends` keyword when you define a class. Inheritance is useful because it lets you make an abstraction of a bigger object like Vehicle, and pass it to a specific, like Car.


**Polymorphism:** In OOP polymorphism is when the same method can be implemented in several ways, it’s related to inheritance. Because the parent class can define the method in a certain way, but when the child classes inherit it, they can implement it in a different form of which was declared in the parent class.

## Git/Github learning
This was a simple detail, but an important to have in mind. I didn't had my github credentials well set. I was able to make commits and push to repositories. But I didn't appear as a  contributor. This was because I had to set my global user from the terminal like this:
```
$ git config --global user.email "MY_NAME@example.com"
```

## Positive Outcomes
- I was able to  open 2 PR [first](https://github.com/meilisearch/meilisearch-java/pull/89) and [second](https://github.com/meilisearch/meilisearch-java/pull/88), that I feel proud of (mostly the 2nd)
- I was added as a collaborator in the repo I'm working on
- I'm learning a lot of Java details I didn't know
## Negative Outcomes
- I have several contributions, and because of the mistake I made with my github credentials, I'm not appearing as a contributor yet.
- I haven't answered the questions Luis' made me from this phase. I'll take care of it this week.
