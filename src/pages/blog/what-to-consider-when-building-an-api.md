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
Designing an API can be a daunting task for newer developers.  It's often their first departure from writing small projects that only they will use, and requires a lot more thought than simply solving the problem.  Who is going to use their API?  How do they intend for it to be used?  How are other people actually going to use their API?  And how will their API handle changes in the future?  These are all really hard questions to answer, but critical to the longevity of any successful API.

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

This, in my opinion, is the most important part in creating any new API.  Before this stage, everything you've built exists purely as an unvalidated concept in your head.  It's extremely important when designing a new API that you ship an MVP as early as possible to begin collecting feedback and bugs.

Notice that this ties in with the last section.  In order to plan for an MVP, you first need to know what features are critical, and which features may be shipped in `V1.1`.  If possible, aim to gatehr this feedback before your first release.  Often, your own projects can serve to validate the API in the beta stages, but always aim for a second opinion.

During this stage, you'll witness people completely breaking your API, abusing methods and fucntions for things you never intended them to be used for, and immediately request a feature you hadn't even thought of.  All of this can be translated into more planning, a better roadmap, and much better documentation.

## Focus On The Interface

Too often you see a friend, colleague, or peer, get stuck building the internals of their system, yet leave their API interface in an unfinished state.  You should always be aiming to finish your interface **first**.  Remember: if the API works, then your user is happy.  They don't care whether the underlying functions read from a file or a database, return static data or dynamically computed data.  This has two enormous benefits.

1. You can get feedback quicker, empowering you to make better decisions.
2. You can put off the non-critical pieces, while you work on building out more important functionality.

For example, your API may offer a method to return a list of personalized movie recommendations for a user.  The critical piece is that a user receives a list of movies, while the slightly less critical piece is that the recommendations are personalized.  Instead of building out the entire system recommendation, you could instead just return a static or randomized list of movies, giving you more time to build out the other supporting pieces of the API, such as saving a movie to a users "watch list".

Planning again is a precursor to being able to make these decisions.  Always be forward thinking in the work that's needed to be completed, and **when** that work needs to be completed.  If you find yourself working on something for more than a couple hours, chances are it's time to wrap it up, and focus on another piece of the system.

## Clearly Document The API

This goes without saying, but a well documented API makes for a happy developer, which means they're likely to continue to use your product.  My favourite example of amazing documentation is [Stripe](https://stripe.com/docs/api).  The thought that's gone into the layout, wording, and hierarchy is clearly on another level.  This is my go to for inspiration when wiritng my own documentation.

Just rememeber, it's not just about writing what your method does.  It's about laying it out in a way a layman can understand, even when it's a more experienced developer than yourself reading it.  Adding too much information is just as much a sin as adding too little, and adding information that isn't required to understand what's happening can lead to confusion.

## Closing Thoughts

I'll repeat this one more time for the sake of consistency: Plan your API's.  If you can do that, then following any advice from this article, or any other source, becomes trivial, and allows you to make the best decisions with the best information possible.  Don't be initmidated, be excited.  Bulding a new API is one of the most rewarding projects in a developers line of work.
