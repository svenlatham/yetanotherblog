---
layout: post
title: "Using Raspberry Pi Access Point to Track Devices"
date: 2014-03-25 09:15:15 +0000
permalink: /2014/03/25/using-raspberry-pi-access-point-to-track-devices/
author: "sven"
categories: ["hacking", "mapping", "raspberry pi", "linux"]
---

I've been looking recently at ways to measure population movements across a large outdoor area. There are various ways of doing this: we watch them, we ask them, or we infer. Watching is a popular option at stadia, city centres and large events. Automated footfall cameras can track movements and figure out how many people walk past a certain point in any period. Put enough cameras up and you can get a pretty good plan.  
However, this merely measures numbers of people. There is no connectivity. 200 people walk past point A, 400 past point B. Does that mean 600 in total at two locations, or did some of those in point A also walk past point B?  
This got me thinking about technical solutions (of course) and fairly quickly I got to wireless networks. Back in 2008, I wrote about [a scheme in Portsmouth's Gunwharf Quays to track mobile devices](https://www.yetanotherblog.com/2008/05/20/path-intelligence/). At the time I think [the company was using bluetooth](http://www.pathintelligence.com/) but since then we've had an astounding growth in smartphone usage. Wifi is pretty much standard and - I would perhaps wager - more likely to be turned on.  
Keen to see how this might be implemented, I did some research into how mobile phones discover wifi networks and found an interesting behaviour. Every few seconds or minutes, your phone will send out a signal "who's there" to probe local wifi networks. Any active access points will respond accordingly with their network name "Hi I'm BtHub\_12345". This surprised me a little, as the device itself has to ask for wifi - I was expecting the access points to broadcast themselves and send out signals every few seconds. [It seems this is to conserve battery](http://superuser.com/questions/128166/is-looking-for-wi-fi-access-points-purely-passive).  
Anyway, having established this, it seemed likely the device would be giving its MAC address away. To clarify, the MAC address is the hardware-level identifier for network devices. It's a bit like a serial number, so when two devices talk to each other they address each other by their MAC address so they know who's who. MAC addresses are supposed to be unique, so no two devices should ever have the same address.  
Curious to see how easy this would be, I have started to build a Raspberry Pi device that is capable of this. It seems possible - hostapd allows the Pi to act as a wifi network access point. This forms the basis for tools such as [Karma](http://www.digininja.org/karma/) (which achieves a lot more than I need) and clearly has the [capability to show probe requests](http://marc.info/?l=hostap&m=122737287518459)  
There are also some privacy issues that need to be tackled. What are the legal aspects of tracking MAC addresses? It seems that, provided the addresses are not tied to individuals, we do not need disclosure. Indeed, my aim is to aggregate data from the start. Once a path has been created, any trackable information should likely be discarded. I'll touch on these too.  
More updates to come...
