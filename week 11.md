# Week 11

## What I learned working on my [first Pull Request.](https://github.com/JabRef/jabref/pull/7151)

This past week I had the chance to work on my first Pull Request for an Open Source project. I faced many challenges while doing so, I'll try to share them with you.

### **The issue**

The issue I was working on was quite simple and straight forward. I'm working on a project that helps researchers to have their articles and citations organized in a software desktop solution made in Java. With this solution you can have your work on a local file or you can connect it to a Postgresql/Mysql database.

The problem was that the user was able to click a button to "Pull changes from database" and if there was no database configured it raised an exception. Obviously the user was not supposed to see that.

From the beginning I had some information to start working on, but still I had to do a lot of research on my own to actually understand how the code was working.
Some of the key concepts I had to learn were:
- How do [Bindings and Properties](https://docs.oracle.com/javafx/2/binding/jfxpub-binding.htm) work in Java FX.
- [Java lambdas](https://luis-valdez.github.io/Learning-Journal/articles/java-lambdas) (Yes, I used my own article as reference)
- [BooleanExpression Class](https://docs.oracle.com/javase/8/javafx/api/javafx/beans/binding/BooleanExpression.html)
- How Java FX implements the [Observable design pattern](https://docs.oracle.com/javase/8/javafx/api/javafx/beans/Observable.html)

### Negative Results

Unfortunately, I couldn't complete two Pull Requests during the available time. This was mainly because finding  an issue that it's attractive and it's not taken it's actually hard in the Open Source community. You'll be surprised how much people want to work for free. So I spent too much time looking for issues instead of actually working on them.

### Positive Results
I think I had good communication with the contributors of the project, I even spoke with the creator of the repository. I never spent too much time blocked because I was constantly sharing my progress and asking for guidance in the right direction and thanks to this I wasn't stucked in a rabbit hole for long.
