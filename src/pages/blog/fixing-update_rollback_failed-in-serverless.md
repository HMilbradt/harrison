---
templateKey: blog-post
title: Fixing UPDATE_ROLLBACK_FAILED in Serverless
date: 2019-11-07T19:14:24.002Z
description: >-
  Recently, I ran into an issue with deploying my Serverless application.  After
  a lot of debugging, trial and error, and sweat, I was finally able to come up
  with a solution to the UPDATE_ROLLBACK_FAILED error.
featuredpost: false
featuredimage: /img/green-onion.jpg
tags:
  - Engineering
---
This is going to be a short one today, but something I searched for and was unable to find.  While deploying my lambda stack, I accidently tried deploying an artifact ~70MB.  For those that are unaware, Lmabda has a maximum artifact size allowed, which they list at around 50MB.  In practice, I find this limit to be a bit more than 50MB, but it's usually around there.

Anyways, this failed, and sent the stack into rollback when it returned a "CodeStorageExceededException".  That's usually fine, everything rolled back and I was able to try to reduce that artifact size and try again.  And try again I did, with a bundle around 65MB. 

## UPDATE_ROLLBACK_FAILED

Thinking I had outsmarted AWS and found the perfect artifact size, I attempted another deployment, and sent my stack into an endless loop.  More attempts to redeploy the stack with a smaller bundle size immediately failed, returning an error along the lines of "Stack:arn... is in UPDATE_ROLLBACK_FAILED state and can not be updated".  Panic.

Or don't, this issue, while really annoying, is pretty simple to fix.  The first help I found was on Github, at [this](https://github.com/serverless/serverless/issues/3146) issue.  This linked to an AWS [article](https://aws.amazon.com/blogs/devops/continue-rolling-back-an-update-for-aws-cloudformation-stacks-in-the-update_rollback_failed-state/) which announed a new fix.

Prior to this fix, there were to options:

1. Delete the stack
2. Contact support

Now there's a 3rd option, found at "Actions > Continue Update Rollback" in the Cloudformation console.  Another option which really helped fix this for me was hidden under a dropdown inside the popup that "Continue Update Rollback" shows.  I think it was called "Additional Troubleshooting", but it lets you specify resources to ignore during the stack update.  This let me just toggle off all my lambdas to push the stack through.

If your stack is like mine though, this still will not work.  I was receiving more errors for Lambdas that would not show up under additional troubleshooting.  To fix this, I had to turn to the AWS CLI:

`aws cloudformation continue-update-rollback --stack-name my-stack --resources-to-skip failed-resource1 failed-resource2`

After running this command on the remainder of my failing resources, the rollback completed.  The truth is, you could run this command at any time to rollback.

**Disclaimer:** This will leave your stack in an undefined state.  Make sure you redeploy a fresh stack as soon as you're able to to prevent this.
