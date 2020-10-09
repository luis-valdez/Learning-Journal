### [Go back to index](https://luis-valdez.github.io/Learning-Journal/)

## Week 3 - 05/10/2020 to 09/10/2020

### Overview
- The Myth of the Genius Programmer.
- #PerfMatters


We have a lot of ground to cover so get ready to get a peek about everything I learned this week. I hope you enjoy it as much as I did.

***
### [The Myth of the Genius Programmer](https://www.youtube.com/watch?v=0SARbwvhupQ)
The talk begins with the two presenters talking about these programming legends that a lot of us start admiring at the beginning of our journey as developers like Guido van Rossum or Linus Torvalds, and how this builds up to people wanting to be perceived as geniuses that commits no mistakes. They use this very funny analogy as how people want to get locked up in their genius cave and then come out to the world with this perfect product already finished and with 0 flaws. 

I felt personally identified with this, because there was a point in University time, that when I didn't know something from a class, instead of asking I waited until the class ended and tried to learn it on my own. And now that I see it in retrospective I realize how stupid that was, the purpose of the class was that, clear my doubts and get knowledge. But instead I wanted to be perceived as a smart guy and we all know that smart guys don't make mistakes, right?

From my example we can see that the consequences weren't that bad, I just wasted some time and eventually I started pushing myself to ask questions and show my vulnerability. But in the talk is mentioned that there's people who can waste months or years working in what they think would be the next great idea in the industry. And in reality their idea can suck or not be as good as they believe. The problem is that if they don't get any exposure early on, there would be no one to critize them and tell them their flaws or mistakes.

Other than this, they mentioned a very interesting comparison between working with Open Source software and traveling with a group of people, there's a sweet-spot of 2 to 3 people at the beginning of a project to gain different perspective but also being able to agree on what direction give the project. I found this particularly funny, because I experiencied this myself whent traveling with friends. When the group gets too big, there is just no way for everyone to agree and take decisions on time. You will just spend your time in corners talking about what you should do withoud doing anything.

***
### [#perfmatters](https://www.youtube.com/watch?v=8MMmg3bDOjc)
This particular video talked about the performance of web pages, particularly in cell phones. To be honest I was completely non-familiar with the topic of this video, great opportunity to learn, right?

These are some of my main takeaways:
- What you can measure you can optimize
- There is a loop for performance improvement, it goes like this: Gather Data >> Make Insights >> Take Action >> Repeat
- There are 3 pillars of web performance:
  1. Network -> Optimize Critical Path.
  2. Render -> Reduce number of paints.
  3. Compute -> Reduce JS execution time.
- I really didn't know what was Paint in this concept, but from what I searched is this: Paint is when the web browser creates a visual representation.
- Browsers cannot paint until critical path is resolved.

***
###[Variable Length Codes](https://www.youtube.com/watch?v=6rnF2Mo80x0)
With this video I learned a lot how we encode form characters to binary code, and that this can be done in two ways.
First, the most simple one is by using an 8 bit number for each letter of the alphabet. Like this:

Encoding:
```
A -> 01000001
```

Decoding:
```
01000010 -> B
```

The other way we can do this is by taking the account the frequency of each letter to assign it a smaller binary number, there are some restrictions we have to follow when doing this. There's something called the 
**Prefix Property**: once a code has been assigned to a symbol, no other code can start with that pattern.
This is to avoid the confusion when decoding your stream.

I think is a very good introduction for people who are beginners in this topic, I personally enjoyed learning about how compression works thanks to Variable Length Codes and I will dig deeper in the next video (that's the next topic in this blog).

***
### [The LZ77 Compression Family](https://www.youtube.com/watch?v=Jqc418tQDkg)
This video was a little hard to grasp. So I will proceed to write everything I understood in bulletpoints:
- Considerating adjacency between symbols is important for compression.
- The LZ77 is a family of tokenization algorithms, that that has been relevant for more than 30 years to date.
- It's used in very common things that I use, such as: GitZip, Winrar and 7zip.

***
### [Markov Chain Compression](https://www.youtube.com/watch?v=05RFEGWNxts)

***
### [The Art of Organization Manipulation](https://www.youtube.com/watch?v=OTCuYzAw31Y)
The goal of this talk can be resummed in 3 bulletpoints:
- How the ideal working environment should be.
- How the working environment actually is in some places (not great)
- How to work on a not so great environment

Basically this great environment should be a place were employees have the freedom to take the initiative and where managers facilitate the work of their employees, all of this while maintaining good communication between all parties.

Of course most of us would love to work in a place like this, but Brian and Ben know that it's not possible for everyone.
A lot of people work in a place where is kind of the opposite I described above (especially big corporations). Having initiative and taking risks isn't really appreciated as much as giving the impression that you're doing a lot without actually doing much. You are at the company to please the manager, the employees can be burdened with unrealistic expectations. And generally there is a directional chaos between 7 different bosses.

The described above was the worst possible scenario, so in reality people will end up working in a combination of the two previous described work places. There are some things you can do to change this, among them are:
- Ask for forgiveness, not permission. If you want to implement something you can just do it and see how people respond to it, of course make sure you can make it reversable so you won't lose your job.
- Always wonder how people are perceiving your actions. This is an important part that sometimes we don't realize because we don't like getting involved in politics, but it's necessary for climbing the ladder in a company like this.
- Get in front of people. Be known. This can be specially hard for people that can be passive, If I was in a big company I will be facing this problem because I don't love the idea of being the center of attention.

All this talk made me reflect a lot about how the software industry works in Mexico, because I think that around 99% of the companies tend to be like the crappy company described (remember 75% of statistics are made up). Of course this is anecdothical from what I've heard/read, but still I think there's a lot of room of improvement in the way that companies (specially big ones) operate. But to be honest I don't know if this idea is too naive because I'm just starting my career. Anyway I like to stay in the positive side of things.

***
### [Programming Well With Others: Social Skills for Geeks](https://www.youtube.com/watch?v=q-7l8cnpI4k)
This particular video is very similar to The Myth of The Genius Programmer. It's made by the same two guys, Ben and Fitz. But there are some interesting points that went over my head in the last video or that weren't in there that I will adress in this section.

**The bus factor:** imagine if a member of a team, that is very specialized in some part of the system gets hit by a bus (I know it sounds bad, but bear with me) what would happen to the team? would there be anyone to be able to deal with the problems that this guy was dealing? That's what the bus factor means, keeping a team that is well rounded and at least has some notions about the system in general. A great way to achieve a big bus factor, is by doing code review, this way you have people checking code for parts of the system that other people wrote and they get to know that part of the system. It's a win-win situation.

**Documentation:** previously, I thought that documentation was only for the functionality of the system. But this video gave me a broader perspective. Documentation can be used as a way of capturing what ideas have already been tried and failed, so in the future if someone wants to try that there's evidence that it won't work, or maybe it can be a starting point to learn what not to do.
Also they say there are other things that are worth documenting, like cultural behavior, so you can avoid discussions in the future, because there will be an agreement of how things are supposed to work.

**You're not your code.** I really liked this phrase, for me it means that you shouldn't link yourself too emotionally to your code or your project. If you manage to do this, you can take feedback a lot easier because it will allow to don't take criticism personally.

***
### [Developing Expertise](https://www.infoq.com/presentations/Developing-Expertise-Dave-Thomas/)
