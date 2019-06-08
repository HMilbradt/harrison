---
templateKey: blog-post
title: How to Choose Between Static Site Generating And Server Side Rendering
date: 2019-06-05T17:17:01.715Z
description: >-
  For many, the choice between SSG (Static Site Generation), and SSR (Server
  Side Rendering), is not as clear cut as it's made out to be.  Today, I'll
  share some examples of when you might choose one over the other.
featuredpost: false
featuredimage: /img/berlin-wall.jpeg
tags:
  - engineering
---
# Brief Introduction

With the introduction of JAMStack, it seems like you can't get away from the debate between static site rendering and server side rendering.  And there's a pretty good reason for it.  JAMStack has been one of the easiest stacks to get up and running with (This blog was built with it).

However, I don't see static site rendering sweeping the industry, and there's a few important reasons why.  Today, I'll be talking about those reasons, learned through experience from working with both methods.

# SEO

This is one I hear all the time, with a lot of mystery and confusion surrounding it.  In the past, SEO bots had a difficult time interpreting client side rendered apps, and you'd often end up with no metadata displayed on your search results.

Nowadays, you're given a few options, each with their own set of ideosyncracies.  Let's start from least complex, and work our way up, using a dynamic, single page application as our starting point

## Don't Do Anything

Google has finally [cracked the SPA](https://searchengineland.com/tested-googlebot-crawls-javascript-heres-learned-220157), and can now wait for your dynamic content to load before indexing your page.  

This is great news to those of us with older sites that aren't worth the hassle of changing, but keep in mind that this is still in its infancy.  Other SEO crawlers and social media bots may still have issues indexing your site, so I wouldn't rely on this if that's an important feature for your site.

## Prerendering

Moving a step up, [prerendering](https://www.netlify.com/blog/2016/11/22/prerendering-explained/) is a really great way to get your site indexed properly without a lot of work.  Seriously, read that article.  It explains it far better than I could, and explains when you shouldn't use it.

In the case of Netlify, this is as simple as clicking a button to enable this feature.  Note, you'd generally only use this on content that is not already rendered, or does not need to be indexed.

## Static Site Generation

The previous two solutions didn't require a lot of work on our end, but depending on your project, this one could require some changes.  

One of the major hurdles with setting this up is getting a build system working.  Whether you're pulling your page data from local files or an API like [Prismic](https://prismic.io), your rendering agent needs some way of knowing which pages to render.

There's a lot of guides and templates out there, so I won't go into this in too much detail.  Make sure to check out NetlifyCMS's [examples](https://www.netlifycms.org/docs/examples/), they're a great learning tool for JAMStack applications.

## Server Side Rendering

At this point, all the given combinations of the previous solutions haven't worked out, and we need a little more flexibility in our project.  This is most likely going to require server side rendering.

I'm going to cover the tradeoffs in a lot more detail in the next section, but you'd generally only pick this option if you have a lot of dynamically loaded content that needs to be indexed, alongside a complicated application.

#  Project Complexity

Let's switch gears now and move over to the technical mumbo jumbo.  At this point in the article, we've covered a lot of really great solutions, but you've probably noticed a recurring theme.  Each new solution adds a new layer of complexity and a swarm of new challenges.

This is particularly true of the jump from SSG to SSR.  Involving a server in anything requires a lot of forethought, and should only be used if absolutely necessary.  Now there's going to be server costs, maintenance, and random bugs that can only be described as glitches in the matrix.  

If all you're doing is running a blog or portfolio, you should probably just stick to a statically rendered site, or even just rely on Googles crawling capabilities (Although we've had some terrible luck with it).

# Other Considerations

Something that's often overlooked with static sites, which I thought I should mention, is the way it works.  Generally, every time you want to publish new content, you have to rebuild the entire site.  As a single blogger or developer, this is hardly a problem.

But imagine a team of bloggers, constantly producing content.  Each change has to run through a build process, and depending on the amount of content and the machine that's doing the rendering, this can start to slow down over time.  Keep this in mind when building a site that's going to be deployed to frequently with new content.
