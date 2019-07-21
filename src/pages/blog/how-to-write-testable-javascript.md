---
templateKey: blog-post
title: How To Write Testable JavaScript
date: 2019-07-21T01:00:20.514Z
description: a
featuredpost: false
featuredimage: /img/aws-cloud.png
tags:
  - engineering
---
It should come as no surprise to anybody that works in web to hear that javascript is one of the most [popular](https://insights.stackoverflow.com/survey/2018#most-popular-technologies) languages out there.  

Unfortunately, the ease of picking up this language comes at a cost: with so much flexibility, and so many new features being constantly added, how do we stay consistent as a community and work together on each others code?  The answer is simple, but far from easy.

## Write Testable Code



## Let's Get Started

Instead of the usual blog-post tutorial starting off with "clone this repo, install dependencies, and check out the code I've provided", I'm going to walk you through the complete setup process of a new project, start writing out some code, and then try to implement some tests.  Not only will I show you how tests are written, but also my thought process for building applications with testing in mind.

In this tutorial, we're going to be making a simple NodeJS application that will open a file, read the contents, make some modifications, then write the updates to a new file.

First off, open up your favourite editor, your terminal, and brew a fresh cup of coffee ☕️.

## Setting The Stage

Let's start by creating the project.  Run the following command:

`mkdir testable-javascript && cd testable-javascript && touch index.js`

I'm going to be using vscode, but any editor will do.

`code .`

Pop open `index.js`, and let's create an entrypoint in our application:

```
function main() {
    console.log('🎬 Starting Application 🎬')
    
    console.log('Reading File From Disk')

    console.log('')
}
```

