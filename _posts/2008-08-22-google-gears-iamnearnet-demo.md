---
layout: post
title: "Google Gears + iamnear.net Demo"
date: 2008-08-22 09:24:33 +0000
permalink: /2008/08/22/google-gears-iamnearnet-demo/
author: "sven"
categories: ["Uncategorized"]
tags: ["google", "gears", "iamnear", "geolocation"]
---

Finally, I'm back into doing something that I love - fiddling with new ideas.  
Today, Google released [Google Gears 0.4](http://gearsblog.blogspot.com/2008/08/gears-04-is-here.html) with geolocation. For those of you not yet aware of Google Gears, it's an attempt by the big G to enhance the client-side with a variety of rich add-ons, such as local databases, offline services and smoother integration with the host OS.  
Gears is also available for Windows Mobile devices and, with the addition of geolocation, adds some exciting spice to the mobile platform.  
Previously I've made aborted attempts to use a combination of [Navizon](http://www.navizon.com/) (a mobile tracking service), [Fire Eagle](http://fireeagle.yahoo.net/) (Yahoo!'s location "platform") and iamnear.net ([Tom Taylor](http://www.tomtaylor.co.uk/blog/)'s very handy directory of POIs). It works to a point, but is a hopelessly elongated way of serving geo-aware content from a web browser.  
With Gears 0.4 it's now possible for the browser to interrogate directly the user's location, through a combination of cell IDs and GPS (where available). The natural conclusion is to slap this tool onto the front of something like iamnear.net, *et voila*, you have a location-aware website puling information directly from the client.  
Without further ado, check out my painfully basic [demo](http://m.svenlat.com/iamnear/) - you'll need Windows Mobile 5/6 and Google Gears (if it is not detected, it'll prompt you to install).  
As a bonus, the site will also work on your desktop, but I'm presuming that'd only be available with a GPS dongle of some kind?  
I'd love to spice it up a bit - actually without presuming too much I'm fairly sure this is a natural upgrade to iamnear.net and other sites... if you have any thoughts feel free to post below ;-)
