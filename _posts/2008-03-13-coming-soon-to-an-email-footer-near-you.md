---
layout: post
title: "Coming soon to an email footer near you"
date: 2008-03-13 10:05:01 +0000
permalink: /2008/03/13/coming-soon-to-an-email-footer-near-you/
author: "sven"
categories: ["Uncategorized"]
tags: ["trees", "forest", "bunnies", "love", "peace", "unity", "environment", "co2", "carbon", "printer", "office", "fluffy"]
---

"Please consider the environment before printing this email"  
These simple words seem to be gracing a lot of my inbound email these days. It feels like a 2007 fad, whereby every participating business can tick another box in the 'we care' category by hardwiring a patronising bit of text into their outbound correspondence.  
How many people have read an email, gone to hit Print and stopped short after glancing at the message, thinking "oh dear, yes I must consider the environment"? Worse still, how many have rushed to the printer after mindlessly hitting Ctrl+P, noticed the tagline at the bottom, and promptly taken their own life for the horrible sin they've so callously committed?  
The irony is that if you *do* print an email, there's a small but real chance the "Please consider..." tagline will wrap onto a new page, thus wasting a sheet all by itself.  
It being the 21st century, 2008 and the year of Web 2.0 I suggest a more brutal assault on these evil corporate tree-killers, using the power of *stylesheets*:

<style type="text/css">  
#treekiller { display: none }  
@media print {  
#treekiller { font: 48pt arial, sans-serif; position: absolute; display: block; left: 0px; top: 0px }  
}  
</style>  
<div id="treekiller">I am a tree killer. I hate environmentalists. Al Gore is a smelly poo face. SUVs rule OK.</div>

Thus, any email printed will remind the reader of how horrible they are, and since it was paper wasted anyway they may as well revert to reading it on-screen.  
Try it out [here](https://www.yetanotherblog.com/wp-content/uploads/2008/03/print-test.html "Print Test") (although you might want to just use Print Preview...)
