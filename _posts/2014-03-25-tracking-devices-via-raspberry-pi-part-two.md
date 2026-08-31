---
layout: post
title: "Tracking Devices via Raspberry Pi (Part Two)"
date: 2014-03-25 11:49:33 +0000
permalink: /2014/03/25/tracking-devices-via-raspberry-pi-part-two/
author: "sven"
categories: ["hacking", "mapping", "raspberry pi", "linux"]
---

In the last post I described how it could be possible to [build a simple tracking device using a Raspberry Pi](https://www.yetanotherblog.com/2014/03/25/using-raspberry-pi-access-point-to-track-devices/ "Using Raspberry Pi Access Point to Track Devices") acting as a wireless network access point. In this post, I try it out for real. This isn't a detailed technical run-down, just the basics.
![IMG_20140325_105251](https://www.yetanotherblog.com/wp-content/uploads/2014/03/IMG_20140325_105251-300x267.jpg)
It seems to get this working you'll need just aÂ Raspberry Pi (Model B has extra USB + LAN so is easier to configure) and aÂ USB Wireless dongle. I started off with the Nano-USB TP-Link WN725N but this isn't supported by the default drivers. I managed to get it working thanks to [this thread on the Pi forums](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=46&t=25921), which describes recompiling direct from Realtek's website.
However, it seems that the Realtek drivers don't have the necessary hooks for responding to probe requests. My guess is this is usually handled at a lower level and hostapd merely makes use of callbacks to customise the handling of these requests. I didn't really fancy rewriting large chunks of code to support it, so I opted for Plan B, which is an Edimax 7711USn (the big white thing in the picture).
The EdimaxÂ *does* seem to work with the default nl80211 drivers and sure enough, when I fired up debug mode, the probe requests came through.
By default, the probe requests only appear with some really high debug level (makes sense - they're usually not that useful) and running in this mode would surely generate a whole load of debug messages I wouldn't need. The second snag is that there is no timestamp with these messages.
So, next step was to recompile hostapd with some customisations. At this stage, I merely wanted proof-of-concept so I moved the probe request notifications up to INFO level and added a timestamp using some existing functions. I then ran the program for a little while et voila, the requests started coming in. The screenshot below shows the requests being made (MAC address partially obscured) and the timestamp (a second counter).
![probereq](https://www.yetanotherblog.com/wp-content/uploads/2014/03/probereq1.png)
These requests will be coming from all sorts of wifi-enabled devices: my phone, my laptop, phones of passers-by. The key thing is that I did nothing to these devices to enable this - they automatically scan for wifi networks and this device is merely visualising it.
In little under forty minutes there were 1720 probe requests from sixteen separate devices. I'd call that a proven concept.
All in, the Raspberry Pi setup cost around thirty pounds. This is for a single device. My original plan was to see how this could be used for tracing paths through a space, such as a city or stadium. For this to work, one would need many more devices, both to triangulate the devices and to provide blanket wifi coverage.
The theory is: with enough of these devices in the right place it should be possible with reasonable accuracy to work out where people are, and where they go. At thirty quid\* a pop, this needn't be a hugely expensive task.
As it turns out, this is precisely the sort of work going on both in the commercial and development world:
[CreepyDOL is a networked tracking tool](http://www.gizmag.com/wi-fi-track-smartphone-creepydol/28585/) - sniffs network traffic and tracks users. As the name suggests, the powers 'in the wrong hands' are creepy indeed.
Wifi tracking of the kind I describe has been in use for a couple of years now, and it's already used to [track customers in supermarkets](http://www.itworld.com/it-management/336828/attention-shoppers-retailers-can-follow-you-around-mall-way-web-trackers-do-onl).
Sure enough, just as I was working on my project, The Register published an article about how [Asda and EE in the UK are using wifi to achieve precisely this](http://m.theregister.co.uk/2014/03/24/ee_watches_over_phones_and_wi_fi/).
 
There are quite obvious privacy implications to all of this. MAC addresses are unique and, even if we can't directly identify someone from them, it may be possible to get their identity from all the clues available (such as where they shop, where they dwell, and by sniffing wifi traffic). Privacy is a huge concern and any technique such as this - even if used with the best intentionsÂ *and no direct logging* - must still be dealt with with care. Last year, it was widely reported that wifi trackers were embedded in some of London's bins. [Officials ordered the company to stop amid privacy concerns](http://arstechnica.com/security/2013/08/street-side-trashcans-that-track-your-smartphone-banished-from-london/), and - despite the company's protestations that all is anonymous - it has clearly hit a nerve with privacy advocates. There may well be no attempt whatsoever to track individuals, but a poorly executed plan will be met with harsh criticism irrespective of the actual risks.
I have a couple more articles planned to follow up these points - any comments are most welcome.
\* There are, of course, all kinds of additional costs: You probably want a case, decent power, and public liability insurance. The Raspberry Pi is also not likely to be a great choice in the long run, for reasons which I hope to pick up later.
