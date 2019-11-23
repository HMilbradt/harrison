---
templateKey: blog-post
title: What To Consider When Building An API
date: 2019-11-17T19:23:57.865Z
description: >-
  After spending an entire year building a production API serving thousands of
  requests per day,  I give my thoughts and opinions on how to approach API
  development and design.  If you're asking yourself "How do I even get started
  building and API?", then read this article.
featuredpost: false
featuredimage: /img/b065aa5b-7d3e-492d-ab19-13a229e2ac76.jpeg
tags:
  - Engineering
---
Designing an API can be a daunting task for newer developers.  It's often their first departure from writing small projects that only they will use, and requires a lot more thought than simply solving the problem.  Who is going to use their API?  How do they intend for it to be used?  How are other people actually going to use their API?  And how will they API handle to changes in the future?  These are all really hard questions to answer, but critical to the longevity of any successful API.

If you read that last paragraph and thought "Who cares? I'm the only one using this API.", then stop and take a step back.  You 6 weeks from now, or 6 months from now, is a completely different developer than the one sitting behind your computer screen right now.   You should never overestimate your ability to read your own code.

## Start On A Whiteboard

When I graduated from school, I remember thinking back on all the projects we had done.  Countless late nights were spent trying to get a project working the night before a due date.  We worked hard.  We worked really hard.  But then I thought about how many projects I had actually planned out, how many were whiteboarded or drawn up on pen and paper beforehand, and I realized that we had missed the point.

Software development has very little to do with coding.  It's about problem solving, thought processes, and planning.  It's about studying a problem, coming up with as many solutions to it as possible, and breaking each and every one a million different ways until a diamond reveals itself.  With this in mind, beginning your project with a line of code is the quickest way to implement and test exactly one of those potential solutions, which is almost never the solution.

So far everything I've said relates to software development as a whole, but it relates to API design as well.  Put careful thought specifcally into the public interface of your API.  in general, I ask myself the following questions:

* How will I structure the API?  Will all methods be exposed on a single object or path, or does a nested hierarchy make more sense?
* Are the names and properties that methods take crystal clear on what they do?
* What features will I need to add in the future?
* Will other users be able to find the methods they need easily?

## Get Feedback Early

This, in my opinion, is the most important part in creating any new API.  Before this stage, everything you've built exists purely as a
