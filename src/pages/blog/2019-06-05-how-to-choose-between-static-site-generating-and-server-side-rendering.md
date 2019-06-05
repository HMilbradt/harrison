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

Emphasis on the brief.  I won't dive too much into the basics, but here's some reading on SSG and SSR. Assuming you know the basics, let's get started.

# How To Decide

Instead of listing the benefits of each, I want to instead focus on some real examples, since ultimately every use case will fall somewhere in the middle of which is best.  Hopefully this helps clearly illustrate some of the problems each is good at solving, and gives you the tools necessary to make the right decision!

# A Blog

We'll start it off easy.  Taking this blog you're reading right now, would this be better implemented with SSG or SSR?  The answer should be clear, but if not, I'll explain why.

Since a blog is largely static, unchanging content, we can almost immediately conclude that this is a perfect use case for SSG.  And for this particular blog, that's exactly what I did.

An exception to this is the amount of content, and the frequency of updates to the content.  Each new post added requires an additional page be rendered at build time.  Down the road, you may have thousands of posts, each one needing to be rerendered every time your blog is udpated.

Along with amount of content, you also need to consider the frequency of updates.  Since every update is going to trigger a rebuild, this means you'll be waiting to see new content.  For a small site, this shouldn't be too long, but combined with a large amount of posts and you may be constantly building your site.



# More To Come
