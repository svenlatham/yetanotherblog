---
layout: post
title: "Crash a Mac"
date: 2013-02-03 14:03:00 +0000
permalink: /2013/02/03/crash-a-mac/
author: "sven"
categories: ["Uncategorized"]
---

It seems that typing File:/// in a Mac application [will crash the Mac](http://thenextweb.com/shareables/2013/02/02/typing-these-eight-characters-will-crash-almost-any-application-on-your-mac/) (OS X Mountain Lion). Most applications appear to be vulnerable, and this is something to do with URI handlers.  
A long time ago, there was a bug in Windows which caused a blue screen ... accessing C:\CON\CON\ would immediately cause a BSOD. Something to do with DOS redirects for comms ports.  
In my foolish youth days, I turned this into a bit of a cruel prank against some friends, by sending them a link to a website which would then attempt to open the above path. Sure enough, it would crash Windows. I then stupidly fell for it myself ...  
Anyway, it seems this is fine in Chrome and Firefox, but it looks like Safari is vulnerable. Can any Mac users confirm (once you've saved all your files!) if the following link successfully crashes the browser? [Here it is](File:///).  
I don't have a Mac to test, but it looks like the bug is more to do with text entry than anything else ... so perhaps creating an INPUT type=text field and autopopulating the field would also work?
