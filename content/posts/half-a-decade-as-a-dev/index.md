---
title: Half a decades of lessons in 5 minutes.
date: 2024-02-22
draft: false
---
# I've now been a professional developer for longer than I was at University.
Now that depressing statement is out of the way, I atually have some reflections & insights on those years I'd like to jot down.

Although, before I go on, there's a an Albert Einstein quote I've recently read & it rings very true.

> "The more I learn, the more I realise how much I don't know."
                                    

In the last 5 years, I've worked for two companies who couldn't be further from each other in retrospect. I won't go too much into it but my first had 7 Developers when I joined & second had 70+. That being said it was the one of the main points of me switching companies. I wanted to see the difference in organisation's, the way the software teams work, the technology. Truth be told I've had great experiences from both & as you can tell, learnt quite a lot! *often the hard way.*

## Take a step back when explaining your work

Anytime I think of advice given to me in my career this is the by far the first thing that comes to my mind. Very early into my career I was given one piece of advice.

> "Everyone can write code, what will get you far is being able to explain the technical to the non-technical."

*Shout out James Ball*

At the time, I was definitely confused by this. *Everyone can code???* 

Though as time passed it started to make more sense. People could complete tickets but when it came to explaining that work to shareholders, or product owner's with questions, they wouldn't be able to translate from the depths of the code to the reality of day to day use of said software.

They more than likely don't know or even more likely don't care how you've produced the goods, they just want a working product. You need to be able to explain to them, how things work, why development is going well, why it's going bad & often estimating how long something will take.

## You're a programmer not a copywriter

Programming is fundamentally about solving problems. 

I think in the ever growing world of AI this is just as important as ever, *although in the growing world of AI this post may not be relevant in 5 years*. Critical thinking & problem solving are the most important skills in being a software developer in my opinion, if you quantify them they'd be required on every CV.

Copying code from ChatGPT, Stack Overflow, Anywhere else **without understanding what it does** is just a recipe for disaster. You're just trying to shove anything in to stop the leak, instead of thinking about the best way to solve the leak.

I'll draw on experience to help paint the picture, a month or two into my first job I was working on a type of integration into the platform that had been done over 10 times before. So it was a very simple structure to follow, I followed an example, wrote my tests, plugged in the new API connection, worked on transforming the data back into our data structure. All going swimmingly, *right?* 

Well I ran into an issue.

{{< figure
    src="surprised-pikachu.png"
    alt="Surprised Pikachu"
    >}}

I spent 2 days trying to get my tests to work or CLI run of the local integration to work but no look. I looked over every example I could find trying to see where I differed. I eventually spoke to my colleague who asked me "Have you followed the error?", I replied *"of course I have"*, explained how it takes me to this line but all the other integrations use that so it's can't be that. **It was that**.

He then clicked through to the abstract everything was using & debugged, I sat there looking at this abstract logic like it was magic. He started to explain to me where it was going wrong & where to look. That's when I found out, it wasn't possible in the current system.

Trying to understand the magic is where you truly start to figure out what's going on, nothing magically works in software. In my case the system wasn't built to handle whatever I was trying to do. I had to **solve the problem** that was in front of me, this new integration required a solution to the problem that I had to develop. I'd willingly bet my first solution was probably not what we went with, but it's much easier to understand the solution when your being steer'd in it than dealing with more *magic*.

## Pull Request comments aren't a negative thing.

A lot of stigma around pull request comments tend to come from:
1. Comment = You've done something wrong.
2. Feedback Fatigue - Dealing with a never ending sea of comments.

How terrifying, not only have you done something wrong but everyone can publicly see that you've done something wrong. *You might as well hand in your notice!* Let's address one by one shall we before you do that.

A comment isn't always to condemn, in recent months more than ever I leave comments on pull requests at work to understand the logic being applied. I want to understand why specific logic is being applied in places, It's a conversation. There **comments** you have comment sections & discussions on most social media platforms, I'm not saying post your life story on them but they can be conversations. 

On this from the flip side as well, be mindful of the tone of comments. In the age of teams & remote working gauging the tone of a comment is hard. For example, saying "Good approach however, have you considered X?" instead of "Why didn't you do X?", or "Do X." without any resource or explanation on why that should be implemented, these can make a big difference I've found.

Lots of comments is always a favourite of mine, would you rather spend one extra day working on resolutions of bugs/edge cases someone may have spotted or move your ticket to done & then spend the next sprint on bug tickets for said issue? The number of comments don't matter at the end of the day, once it's merged, who even remembers? Don't worry about it.

However I will say one thing on this as Feedback Fatigue is a real thing unfortunately, not everything needs to be under such a microscope to the point of blocking a PR.
