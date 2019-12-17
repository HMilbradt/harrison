---
templateKey: blog-post
title: Netlify vs Amplify - A Look At Modern Web Application Platforms
date: 2019-10-12T16:26:20.330Z
description: >-
  Which platform is better for a new web project.  See how Amplify and Netlify
  stack up to one another, and find out which is the right choice for you
  application in 2020.
featuredpost: true
featuredimage: /img/fullsizeoutput_99d.jpeg
tags:
  - engineering
---
Over the past year, I've paid close attention to both [Amplify](https://aws-amplify.github.io) and [Netlify](https://www.netlify.com), watching as they add new features, close off pain points for their users, and pave the way towards modern web development.  But it wasn't until recently that I had to ask myself: which one should I choose?

In the following sections, I'll give a little summary of each, in case you don't jnow much about either, or haven't been following them in the past several months.

## What Is Netlify?

From the headline on their front page:

> Netlify is everything you need to build fast, modern websites: continuous deployment, serverless functions, and so much more.

![Netlify Logo](/img/full-logo-light.png "Netlify")

As you work more with Netlify, you begin to notice a trend: They've thought of everything.  Being primarily focused on the [JAMStack architecture](https://jamstack.org), they provide so many "nice-to-haves" on top of a normal host.  And to top it all off, they have a very sensible free tier, that will get hobbyists and small bloggers going with all their core features.

Truly automated build pipelines from the moment you connect your Github repo, managed authentication, easy [serverless function](https://www.netlify.com/docs/functions/) integrations built on top of AWS.  Possibly my favorite feature, while not actually part of Netlify, is the [NetlifyCMS](https://www.netlifycms.org).  It integrates so nicely with their Identity service to provide a JAMStack CMS.  This blog was built on it, and I would certainly pick it up again on another similar project.

As your application grows, you'll likely need at least some backend functionality, which Netlify covers with their serverless functions.  Just write the javascript, place it in a folder you've defined, and push it to have your serverless functions deployed.  You're able to define build time ENV variables to keep your secret keys safe, and pull them into your code at build time.

I highly recommend following their [blog](https://www.netlify.com/blog/) and their [development team](https://www.netlify.com/about/), both of which are fantastic.  Even if you don't end up using the project, they are a shining example of what a great development team can accomplish.

## What Is Amplify

I'll continue the trend of posting an excerpt from their home page:

> AWS Amplify makes it easy to create, configure, and implement scalable mobile and web apps powered by AWS. Amplify seamlessly provisions and manages your mobile backend and provides a simple framework to easily integrate your backend with your iOS, Android, Web, and React Native frontends.

![Amplify Logo](/img/amplify-logo-circle.3c79537237d8ac81726fc61fe5e0c03f288e64ae.png "Amplify")

Wow, that's a mouthful.  I can summarize that by saying Amplify consists of 3 products: A console, a CLI, and a component library.

The console shares a lot of the same features as Netlify, such as an automated build system, custom domains, rewrites/redirect customization, and selecting different domains for different branches.  It's very easy to navigate, and gives you a great overview of how your application is configured.

In order to unlock the rest of Amplify, such as authentication, backend API's and databases, and serverless functions, you'll need to configure the it with the CLI, which is another major selling point of their product.  The CLI allows you to create, manage, and delete all backend resources, and provides some amazing code/query generation features.

Finally, the component library allows you to write, javascript, iOS, and Android projects using the exact same underlying framework, giving you some ready-to-use UI components that integrate directly with all their servcies.  Need a sign in page?  Just use the SignIn component, and let them take care of password changes and MFA challenges.

To wrap up the rest of some "nice-to-haves" for the console, Amplify also provides project-wide or branch-specific environment variables for the build pipeline, device farm snapshots of your app on different mobile devices, password protected branches, and so much more.  Read through their docs to get an idea of the scale of this project.

## So Who Is The Better Pick?

This is the obligatory "it depends", but it's very easy to figure out which one of these systems is right for you.  As always, it's a mix-up of existing architecture, required functionality, future scalability, and flexibility.  Full disclosure, this blog is built on top of Netlify and NetlifyCMS, but I do have professional experience working with both.

In my opinion, Netlify is the right choice for beginners or smaller projects, like blogs, hobby projects, and prototypes.  it's extremely simple to set up, offers an incredibly rich set of free fucntionalities, and has some fantastic docs and starter projects to learn from.

On the other hand, Amplify is something I see scaling far better as a project becomes more complex, and begins to demand more from its backend.  Its tight integration with AWS Cognito allows users to leverage an enormous amount of services while still maintianing a secure application.  The ability to use the same library for a mobile app can make or break a project.

With some of the differences in mind, you should begin to see that it doesnt actually matter _that much_ who you decide to roll with.  Both have some great functionality, and can easily be integrated with any other servcies or projects you might have.  Obviously if your entire stack is AWS and you want to keep it that way, Amplify is the better choice.  But in other situations, it actually doesn't matter that much.  Both do a great job as a standalone static site host.

## Summary

I'll sum up the pros and cons of both platforms here, and give some closing thoughts on the two.

**Netlify pros:**

* Amazing documentation.
* Free tier is feature rich.
* Simple setup for new projects.
* Tight CMS integration for JAMStack apps.
* Easy integration of serverless functions & authentication.

**Netlify Cons:**

* Does not have any component libraries.
* Free tier can become limiting as site grows.
* Serverless configuration is limited out of the box (can contact support for changes).

**Amplify Pros:**

* Tight integration with AWS.
* Component library for web, android, and iOS.
* Automated GraphQL query generation.

**Amplify Cons:**

* Documentation, while complete, is dense.
* Some of their great selling points can cost money, usually pay as you go.
* Configuration can become quite complicated as you begin to need bigger features.
