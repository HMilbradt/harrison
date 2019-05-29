---
templateKey: blog-post
title: Testing Stripe Webhooks Locally
date: 2019-05-28T14:04:10.000Z
description: "Testing web hooks doesn't have to be frustrating.  Learn how to use Stripe with Ngrok to receive web hooks locally, supercharging your development process \U0001F64F"
featuredpost: true
featuredimage: /img/frost.jpg
tags:
  - engineering javascript
---
![frost](/img/frost.jpg "Frost")

## Setup

I'm assuming you've hit this post because of similar frustrations I've had in the past, so I'll just dive right in.  Go ahead and clone the following repo:

`git clone https://github.com/HMilbradt/stripe-ngrok.git`

Once finished, run the following:

`cd stripe-ngrok && npm install`

That's it for the code setup.  The next step is to make sure you've got Ngrok installed.

## Ngrok

Let's get Ngrok installed.  You can use this command to add Ngrok to your machine:

`brew cask install ngrok`

While that's installing, go ahead and sign up for an account on their [site](https://ngrok.com).

To finish off, let's get you signed into Ngrok in your terminal.  Your token can be found [here](https://dashboard.ngrok.com/auth), which you can then place in the following command.  Make sure to fill in your auth token.

`ngrok authtoken <your-token-here>`

## Stripe

If you don't already have an account with [Stripe](https://stripe.com), go ahead and create one.  If you do, sign in and grab your private key.  It can be found by clicking "View test data", then in Developers > API Keys.  Make sure you grab the one labelled "Secret Key".

We're also going to need to add a webhook at this stage, but you may have already noticed a problem; This server isn't running anywhere accessible for Stripe.  But that's what we're going to fix.

In a separate terminal, run the following command:

`ngrok http 3000`

This is going to start Ngrok, which is going to forward all traffic received to localhost on port 3000.  Incidentally, this is the port our app will be listening on 👌.  The URL Ngrok will spit out for us should look a little something like this:

`https://88096e42.ngrok.io`

Now head to Developers > Webhooks, and click "Add Webhook", then paste in the URL Ngrok gave us.  For events, just select "Account".  In the future, you would check off the webhooks you need to receive here, and Stripe would handle filtering the ones you don't need.

Once finished, you should see a section called "Signing Secret".  Make note of that, we're going to need it shortly.

## Fire Up The Server

In order to do that, we're going to need a couple things.  First, open up `index.js` and on line 4, paste in your Stripe secret key.

Next, paste in the Stripe signing secret on line 5.

We should be ready to go, so in a new terminal (Remember, don't close your Ngrok terminal) run the following:

`npm start`

Opening the link this gives you should be met by a message containg a 😎.  If so, you've almost made it.  If not, make sure all your secrets are filled in properly.

## Sending A Test Webhook

With the server running on port 3000, and Ngrok forwarding requests in the background, it's time for us to head back over to Stripe and send off our first test webhook.

Navigate to Developers > Webhooks, then click "Send Test Webhook", then click the Send button.  With any luck, you should see "200" appear in the response box.  This is the status code of the request, so 200 means everything worked.  Head to the terminal that's running node to see if this worked.

You should see the Stripe webhook body, along with a message saying "Event successfully parsed locally."

Congratulations!  You're now set up to debug and test your Stripe integration locally.

## Final Notes

This guide also teaches you how to check the webhooks signature, which is recommended by Stripe as a best practice.  You can read more about this [here](https://stripe.com/docs/webhooks/signatures).

Important to note, Ngrok will not start with the same URL every time, unless you have a reserved URL on their paid plan.  This means that when starting up your environment, there's a checklist that you need to follow:

1. Start Ngrok listening on the port you need
2. Edit your old Stripe webhook to use the new URL
3. Ensure the Stripe signing secret is the same.

That's all for this guide.  Hope it helps some of you out there.  Stay tuned for the next post!

Thanks for reading 🙏
