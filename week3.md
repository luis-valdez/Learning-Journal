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
### [Variable Length Codes](https://www.youtube.com/watch?v=6rnF2Mo80x0)
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
### [Developing Expertise: Herding Racehorses, Racing Sheep.](https://www.infoq.com/presentations/Developing-Expertise-Dave-Thomas/)
In this talk Dave Thomas talks about the different levels of expertise that exists for a certain ability. Let's get into that. We have five different levels, from lowest to highest:

1. **Novices:** They're just starting to learn. They need to be told exactly what to do with a lot of detail, but they don't need a lot of context of the bigger picture because they tendo to get scared or overwhelmed with this.
2. **Advance Beginners:** Similar to the Novices they still need to be told what to do, they tend to get really focused on what they're doing and can't seem to grasp the bigger picture yet. Still they have more experience than the novice.
3. **Competent:** In this level you start feeling good about yourself, you're starting to feel like you can do things without being told what to do. And that's what you start doing, and by doing so you reach the next level.
4. **Proficient:** Here you can actually feels like you are going backwards and you can lose that confidence that you gained in the previous level, this is because you start to see the bigger picture and actually realize everything that you don't know.
5. **Experts:** Finally, the highest level. This are the folks that are always seeking new information. They know how to do most things in their field, but they don't totally understand how exactly they're doing. This is because at this point they have the patterns so deep on their brains, that they start acting and deciding out of intuition.

The lesson about this video is that you shouldn't try everyone the same, everyone is in a different level of this scale. The upper you are the more autonomy and vision of the big picture you need, the lower you are the more detailed instructions and less context you need.
Personally, right now I feel in level 2, trying to make the transition to level 3. This is because I understand some key concepts and I'm able to work on simple tasks with clear instructions, but I feel that if I'm not told what to do I'll get confused. But of course, as I mentioned, I don't plan on staying in level 2 forever, I'm working very hard each day to eventually become a wizard (expert).

**Side Note:** I realized that Dave Thomas is the author of Pragmatic Programmer, I have been recommended that book many times and I have been wanting to read it for a while now. Maybe it's a sign to start it.

***
### [Perfection is an Unrealistic Goal](https://www.infoq.com/presentations/Perfection-Is-Unrealistic-Linda-Rising/)
Linda Rising presents the Agile methodology in a way that makes it sounds so human and so easy to connect. I hope I can transmit a little of her thoughts in here.

First what got my attention the most says how we humans are inherently Agile, because we work in cycles. She gives the example of sleep cycles, how we go from NREM sleep to REM sleep, and how we tend to sleep in 90 minutes cycles. She also happens to believe that the same phenomenon happens during daytime. She gives the example of this guy that worked in 90 minutes cycles and rested 30 minutes, and achieved a great productivity and how this also was backed by some studies.

I personally connected a lot with I just described because of 2 reasons:
1) Right now I'm reading a book called Why We Sleep that its written by a neuroscientist and talks about sleep and tries to demistify it, so the sleep cycles are something that I've read before.
2) I practice the Pomodoro Technique which is working 25 min and resting 5 min. But naively, I've never thought about how this had to do with sleep cycles and much less about how it had to do anything with agile.

So that's mind blowing for me, we started doing agile because evolution itself made us beings that tend to work or function in cycles. So unconsciously we decided to "invent" a whole methodology based in what was our inherent behavior all along.

Another amazing fact is that this video is connected to the "Making Badass Developers", from last week, and "Developing Expertise" videos from this week. And here is why, in MBD the author talked about how we have to get at least 200 exposures and our brain will pick up the pattern eventually without us knowing. Developing Expertise, sayed that experts don't really know how they get the knowledge, they just follow instinct and they're usually right. And to wrap up, here Linda says that there was an experiment where people were tested to see how much time it took for them to respond to a random light on a screen; eventually people began to know where was the light. Eventually scientists figured out that the people were solving their algoritm in their heads, but the thing is that they didn't realized it. They did it unconsciously.

![mind=blown](https://media.tenor.com/images/2e2f908309dd8a576d1193506c16f147/tenor.gif)

***
### [The Power of an Agile Mindset](https://www.infoq.com/presentations/power-agile-mindset/)
Linda bases this talk on the research that exists regarding the Growth Mindset vs Fixed Mindset. So I will start by that, quickly reviewing this types of people.

| Fixed Mindset | Growth Mindset |
| --- | ----------- |
| Thinks that skills are static | Believes in growth and improvement |
| Avoids Hard Challenges (doesn't want to look bad) | Embraces Challenge |
| Believes that effort is for those who have no talent | Knows that effort is the path to mastery |
| Presents helplessness against challenge | When challenge comes up, so does resilience. |

Basically, Fixed mindset people believe that the habilities that you have are decided when you born, either you got it or not. Growth mindset on the other way, is the opposite. It believes in improving and that of course you have some innate hability to do something, but that is just one factor; the other one is the ammount of effort that you put in to things.
To illustrate this, I really like this comic from Calvin and Hobbes:

![Calvin and Hobbes](https://pbs.twimg.com/media/EDNBsXdU8AAkO4E?format=jpg&name=900x900)

Previously to this video I had the chance to read about the work from Carol Dweck Regarding Growth Mindset, and it really changed the way I thing. I strongly recommend whoever si reading this to check this [Ted Talk](https://www.youtube.com/watch?v=_X0mgOOSpLU).

***
### [Collaboration, Bonobos and The Brain](https://www.infoq.com/interviews/linda-rising-agile-bonobos/)
Similar to previous talks, Linda remarks the idea that the conscious mind is only a small part of our brain. Most brain-power is contained in our unconscious mind, according to Linda.
With this premise she says that when facing a difficult decision you should gather a lot of information, then you should sleep on it and your subconscious will take care of working out the data for you.

Also she says that, similar to the bonobos,  we work better in small groups of people (10 max). And I have personally experienced this, once in university I had to work in a team of about 35 people in the same project. It didn't went out pretty well.

Similar to bonobos we can have great benefits by 'pairing', in the case of the software industry this would mean the pair programming. And this is also mentioned a lot by Ben and Fitz, that a simple lunch with your co-workers can improve a lot performance. I think this is pretty logical, if you feel good with your team and you realize that they're humans, you'll create a nice atmosphere and will be able to work better together.

***
### [Prejudices](https://www.infoq.com/interviews/Prejudices-Linda-Rising/)
I'll resume this in one paragraph.

We'll have prejudices against other people. But if we're conscious about those prejudices we can do something about it. Also a good thing to overcoming this first impressions, is putting people to work together, Agile accomplish this with things like pair programming. Once you actually get to know a person and work towards a common goal, it can change a lot about the way you perceive them.

***
### [Everything is a Remix](https://www.everythingisaremix.info/watch-the-series/)
This was a pretty cool video to watch, I will probably recommend it to some friends.
Basically, the idea is that every idea that we have is product of other ideas that other people had in the past. As Isaac Newton said: *"We stand on the shoulders of giants".* Quote that he copied from other guy. There were given many examples were great inventions are copied, to give a few:
- Music is full of samples
- Movies are full of copied scenes
- Inventions like the Mac

The're is also a whole thing going on regarding lawsuits of intellectual property. People are trying to fight and reclaim ideas, there are even people that make a whole bussines out of this. They don't create anything, they just try to make a dollar out of it.
The conclusion of this, is that in order to improve, we have to copy and transform other ideas. Is something in our nature, is something so present in us, even evolution works that way...
So, in my opinion, we shouldn't be protective with our ideas and try to be open to the idea of letting other people improve our ideas.

***
### [Missing semester: Shell tools and scripting](https://missing.csail.mit.edu/2020/shell-tools/)
This week I had the chance to get better with my Shell skills, I learned several comands, and how to run bash script from the Terminal. I'll tell you about everything.

```
#!/bin/bash.   <- this is what is called a shebang and it's used to indicate that a file is a bash script.
```

```
$PATH   <- this is an envorimental variable that tells you the dirs of executable programs in your computer.
```

```
tldr   <- this gives you a quick set of commands that's most likely what you're looking for i.e. tldr ls.
```

```
history   <- useful for getting a history of your commands
```

I'll also learned that are different commands for achieving the same things.
For example:
- **find and fd**. Both of this commands will help you find files matching the given pattern.
- **grep and rg**. search the current directory for a regex pattern. (file content)

There are also some powerful combinations, one that comes to mind is:
```
history | grep 'python'
```
this will help you find all commands you have executed that include the word python.
Phew. That was a lot of new commands for me.
