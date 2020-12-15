# Week 12

### [Go back to index](http://luis-valdez.github.io/Learning-Journal)

## Overview

This past week I had the chance to work on my [second Pull Request.](https://github.com/meilisearch/meilisearch-java/pull/83)
This 2nd PR is in a new project called MeiliSearch. Resumed in one sentence, MeiliSearch is a text search engine. It's similar to ElasticSearch in some ways.
Specifically I'm working on a module of the project, that's a java client to consume the MeiliSearch API.

This week I'll share with you what I learned this past week, what I think I did right, and of course what I did wrong.

***
### Java Learning

The project I'm currently working is written in Java, so of course my java skills have been getting stronger. What comes to mind is:

1. **Java Generics:** I have been working with generics in java without knowing what they're called for a long time now. The most common example to illustrate what generics are, is an `ArrayList`. When you define an `ArrayList` you can do it like this:
```java
List list = new ArrayList();
```
This code works perfectly, the problem is that it won't provide a very useful list. If we wanted to add a String element and then use it as a String we would have to cast it each time. Like this:
```java
list.add("hello");
String s = (String) list.get(0);
```
Here's where Java Generics comes handy, you can use them as some sort of parameters to declare that our ArrayList will be of certain type, in this case a String:
```java
List<String> list = new ArrayList<String>();
list.add("hello");
String s = list.get(0);   // no cast
```

2. **Jackson Object Mapper:** This is a dependency that allows you to serialize and deserialize java classes into `.json` files. For example if we have the Car class:
```java
public class Car {

    private String color;
    private String type;

    // standard getters setters
}
```
You could very easily create a `.json` file with the data of an instance of a Car:
```java
ObjectMapper objectMapper = new ObjectMapper();
Car car = new Car("yellow", "renault");
objectMapper.writeValue(new File("target/car.json"), car);
```

3. **instanceOf operator:** I discovered that Java has an instanceOf operator that allows you to validate if certain object is an instance of some class. It's specially useful while testing. For example, the way I used it this week:
```java
assertTrue(index instanceof Index);
```

***
### Git/Github Knowledge

This week I learned a simple but useful thing. When you fork a repository and you make your first contribution it's exciting you've done it! you contributed!
But no one prepares you for what comes next. But do not fear my friend, I'm here to help you.

When you contribute in open source you will have to fork a project and have a local copy in your machine. And when the master branch of the original projects moves further you can't simply make a `git pull` and get all the changes to your local to stay updated. You'll only get the changes from your forked repo.
So should you just delete your forked repo and fork it again to be actualized? Well that wouldn't be a very cool/clean solution right?
Here's what you can do:
```
$ git remote add upstream https://github.com/[Original Owner Username]/[Original Repository].git
$ git fetch upstream
$ git checkout master
$ git merge upstream/master
$ git push
```
I won't dive deep into this steps because it's already very well detailed in [this tutorial.](https://digitaldrummerj.me/git-syncing-fork-with-original-repo/#:~:text=In%20order%20to%20pull%20the,repo%20as%20an%20upstream%20repository.&text=You%20are%20now%20ready%20to,to%20the%20your%20forked%20repository.)
***
### Positive Results

***
### Negative Results



