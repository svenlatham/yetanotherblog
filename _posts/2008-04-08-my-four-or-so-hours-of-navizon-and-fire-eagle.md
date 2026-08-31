---
layout: post
title: "My four-or-so hours of Navizon and Fire Eagle"
date: 2008-04-08 13:22:21 +0000
permalink: /2008/04/08/my-four-or-so-hours-of-navizon-and-fire-eagle/
author: "sven"
categories: ["Uncategorized"]
tags: ["gps", "navizon", "fire eagle", "yahoo", "location", "triangulation"]
---

Here's an idea that I've been wanting for a while. When I'm on the road, heading to a client's office, and I get caught up in traffic or running early, I'd like to let the client know automatically.
Generally, you can text (not an option while driving), email (ditto) or phone the client. Personally even with a bluetooth headset I try to avoid calling people. You could pull over, but I've heard they frown on that on motorways, and if you're late it's only going to make you later...
So here's an idea I've been playing with for a while: set up your phone with GPS and have it text or email the client to say 'running 10min late...' or 'ETA 11.35 - stick the kettle on'. Being a web-savvy kinda person I'd have a webpage set up with Google Maps and a near real-time trace of my position.
Along comes [Yahoo Fire Eagle](http://fireeagle.yahoo.net/), a web service designed (as far as I can tell) as a hub for all one's location-based services. Something tells Fire Eagle 'I am here' and it dutifully tells all the subscribed services where you are.
Great. And I managed to get an invite too - double great.
The problem is, Fire Eagle is as new as you can get. It works as a service, but there's very little talking to it and very few services that use it. Then again, that's the point of inviting a whole load of developers to play with it.
That is until I spotted [Navizon](http://www.navizon.com/). This program (the Lite version is free) sits on your mobile phone and uses a combination of Celltower triangulation, Wifi AP triangulation and good ol' GPS to figure out where you are. Joy of joys, it publishes to Fire Eagle too.
After about an hour of faffing around with Navizon's weirdly ugly user interface, I finally discover that to actually publish to the server (and on to Fire Eagle) I must enable something in my Buddies(!) menu. Yes I know - RTFM and all that, but frankly there's something to be said for making user interfaces vaguely intuitive as well.
I still don't know what my 'Home Area' is about or what it has to do with anything. I can only assume it's a privacy thing to stop people finding your exact home, but goodness me everything about their website is counter-intuitive.
For a while, it worked. Navizon worked out where I was (accurately, and brilliantly) purely based on Wireless APs (mine included, it seems). I walked to the shops and it followed me. I went to the next town and - apart from placing me 200yds in the sea - it was fairly accurate.
Then I noticed something that upset me. The program running on my Windows Mobile PDA/Phone was slow to begin with, but I gave it the benefit of the doubt. When I tried *closing* Navizon the entire thing crashed. Later on, I tried it again - same result.
While playing with the program I also noticed that the phone was noticeably hotter than usual, and realised that the thing was sucking battery juice. I have to say that this is not necessarily Navizon's fault as such. Wireless sucks the life out of phones at the best of times, and with Wifi AP locating switched off the system would rely on the far less accurate cell triangulation or the perpetual tethering to a bluetooth GPS. Unfortunately I could never figure out how to switch off Wireless AP locating, and I was mobile so reading the manual was not an option.
Which brings me into the close of my little foray into the world of location updating. What started off as high hopes for a service I've been looking forward to for a long time has turned into a complete disappointment. The biggest turn-off for me was how utterly unintuitive and resource-hungry Navizon's phone app seemed to be. I hope Navizon can get their product straightened out, and if they do I'll be right back to try it again. Alternatively I hope somebody else (perhaps spurred by the interest in Fire Eagle) will develop a slimmer, simpler triangulation/location app that publishes to the Internet.
Until either happens, I'll continue dreaming up new services that might one day exist!
