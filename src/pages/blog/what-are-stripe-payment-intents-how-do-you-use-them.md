---
templateKey: blog-post
title: What Are Stripe Payment Intents & How Do You Use Them?
date: 2019-11-23T20:42:29.144Z
description: >-
  Stronger regulatory rules and an increasing number of online transactions
  means one thing: merchants need to upgrade their security procedures for
  handling payments. 
featuredpost: false
featuredimage: /img/home-jumbotron.jpg
tags:
  - Engineering
---
Over the past decade, there has been an enourmous uptick in the number of online businesses.  Nowadays, if you can think of it, you can buy it online.  Many see this increased choice and convenience as liberating, but it comes with a lot of security problems.  How do you know that someone isn't using your card for online purchases?

That question is often posed in the context of consumer security, but it's also the businesses accepting these cards that need to be careful.  If your're an online retialer, too many chargebacks or fraudulent purchases can have a hugely negative impact on the rates you receive from your payment provider.  This can completely kill a businesses margins, and ruin a consumers trust in the platform as a whole.  So what's the solution?

While not a silver bullet, Stripe has an answer to some of these problems: [Payment Intents](https://stripe.com/docs/payments/payment-intents).  Most notably, payment intents come with built in support for [Strong Customer Authentication](https://stripe.com/docs/strong-customer-authentication) (SCA), giving merchants a better stronger gaurantee that the card a customer is using belongs to them.

So with that little intro out of the way, let's take a look at how Payment Intents work.

## A Closer Look

The simplest way to look at Stripe Payment Intents is to compare them to Stripe Charges.  A checkout flow using the Charges API looks like the following:

1. Collect the users card information in a form using Stripe Elements.
2. Use Stripe.js to tokenize the card information.
3. Send the token to your server and create a charge.
4. Return a success or failure immediately to the browser.

This flow is simple for a couple reasons.  For starters, your server does not directly handle customer card information, meaning there is no requirement for PCI compliance.  Secondly, this flow is synchronous.  Sending the token to your server results in an immediate success or failure from Stirpes servers, which you can use to update the frontend.  Unfortunately, this is where the differences between Payment Intents and Charges becomes obvious.  

The following flow is an example of how a Payment Intent would look:

1. Create a Payment Intent on your server with the desired amount and return the `client_secret` to the browser.
2. Colelct the customers card information with Stripe elements.
3. Tokenize the customers card information, and use the token + `client_secret` to confirm the payment intent.
4. Use a webhook to fulfill the customers order, or mark as payment failed.

Same number of steps, but quite a difference.  As you can see, using Stripe Payment Intents is a lot more complicated.  Not only is there an entirely new step required to begin using them, but the actual confirmation of payment happens asynchronously in a webhook.  This brings up a question:

> How does the browser know that the order is fulfilled?

Now this can obviously be done with sockets, notifications, or polling an endpoint.  But again, you see this requires yet another step just to complete a customers order.  So why is this necessary?  Why can't Payment Intents use the same synchronous flow that Charges use?

Well the answer to that is the very same answer to the first paragraph of this post.

## 3D Secure

Stripe implements [3D Secure](https://stripe.com/docs/payments/3d-secure), which is an additional authentication step required before payment may be completed.  The biggest benefit to implementing this yourself is simple: A customer authenticated with 3D Secure shifts the liability from yourself, the merchant, to the card issuer.  This is absolutely huge for retailers that have large numbers of fraudulent transactions.  Now because of the way this flow works, your browser is not notified of success or failure by Stripe.  Instead, they send this information vie a webhook.
