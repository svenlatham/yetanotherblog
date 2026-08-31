---
layout: post
title: "Blogwise Improvements"
date: 2004-08-29 15:33:20 +0000
permalink: /2004/08/29/blogwise-improvements/
author: "sven"
categories: ["Uncategorized"]
---

In the past month or so, Blogwise's performance has been through the floor. This is because most of the scripts used for maintenance of Blogwise are run on the server itself. The site has grown much faster than I expected, and the bits and pieces that run in the background are starting to feel the strain.

Classic example: one script which I ran at 2am daily was designed to go through and grab particular bits of data from every site listed. This was nice and simple originally, so I set it up as a cron task. Earlier this year it got to a point where the run-time was longer than 24 hours - instant slowdown. Since then, I've had the bots run only if an existing instance is not already active.

These scripts shouldn't normally cause too much of a problem, but another factor - spam - is really causing me a headache now. Some lovely individual out there decided to send a whole load of emails out with the From: address at [{randomstring}@1do3.com](mailto:{randomstring}@1do3.com). Result: every bounce came back to us. At its peak it was hitting 3,100 messages per minute. That is going to put a strain on any system. I've set up secondary and tertiary mail servers but UK2's DNS manager refuses to acknowledge my updates (grrr....) to the domain name.

So anyway, I've spent the past few weekends trying to optimise the Blogwise code (and its underlying system) and it seems to be giving some positive effects. Front page load time is better (albeit still a bit sluggish), and I've also shifted a lot of the maintenance responsibility to other computers, which can easily sit behind an ADSL line and just chug away.

It's remarkable how quickly a site can grow beyond what you expected, and how rapidly one must respond to changing circumstances - I'm hoping that now I can last for as long as possible without the (inevitable) need for a dedicated Blogwise server, particularly since that'll probably mean I'll need to set up a company to manage the assets.
