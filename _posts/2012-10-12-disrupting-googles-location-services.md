---
layout: post
title: "Disrupting Google's Location Services"
date: 2012-10-12 17:45:39 +0000
permalink: /2012/10/12/disrupting-googles-location-services/
author: "sven"
categories: ["Uncategorized"]
---

A few weeks ago, while staying in a hotel in continental Europe, my phone alarm went off at the usual time ... except it didn't. It was an hour late. Odd - and annoying.
In my bag of goodies I often carry a small wireless access point with me. The reason is simple, some of the hotels I stay in have wired Internet only. Not so good when you're packing a tablet and phone (and don't want to get the laptop out).
Turns out it was my wireless AP that caused the phone to think it was back in the UK. The last time I'd used the AP was in England (GMT+1), so when the phone detected the AP again, thanks to the wonders of Google's location services, it put me back in the UK and an hour behind. The clock, the weather forecast - everything was "updated".
Clearly Google had spotted my AP, placed it in the UK and relied on that information to set the phone's location. Interestingly, the phone never took into consideration the twenty-or-so other access points visible around the hotel - this was the strongest.
Lesson learnt: be careful of geolocation facilities. Computers can be smart and dumb at the same time.
