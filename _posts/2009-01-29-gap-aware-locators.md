---
layout: post
title: "Gap-aware locators"
date: 2009-01-29 17:07:17 +0000
permalink: /2009/01/29/gap-aware-locators/
author: "sven"
categories: ["Uncategorized"]
tags: ["location", "geolocation", "maplin", "search", "distance", "haversine"]
---

One notable thing about most location software is that it is usually fairly crude.
Most programmers take the easy route and simply work out the distance between two points via a bit of trig. Some smarter programmers are aware of the Earth's curviture and [bear this in mind](http://en.wikipedia.org/wiki/Haversine_formula).
Usually - this is as far as it goes. The classic "find my nearest" search is great for most places but is a rough 'as the crow flies' measurement.
Living for a while on the Isle of Wight, I came to appreciate that while this normally works OK, on an island it's a profoundly dumb system.
If, for instance, you live in [Ryde](http://maps.google.co.uk/maps?f=q&source=s_q&hl=en&geocode=&q=ryde&sll=50.926346,-1.189061&sspn=0.007452,0.013819&g=Hampshire,+SO32+2HU&ie=UTF8&ll=50.747753,-1.249695&spn=0.478777,0.884399&z=10) (north coast of the Isle of Wight) most systems will recommend a shop in Portsmouth or Gosport before the more sensible option in Newport or elsewhere on the island. A bit daft really, considering to get to the 'closer' shop might be one or two ferries at the least.
Today, I noticed that the [Maplin](http://www.maplin.co.uk)Â website actually *excludes*Â shops which might fall in the radius of consideration, but are much trickier to get to.
Searching for an item from my [Fareham (mainland) address](http://www.maplin.co.uk/NearestStore.aspx?OrderCode=A21HY&source=17&location=po15%205tt) gives plenty of options, but the Newport store (10.7mi as the crow flies) is not included.
Similarly, searching from an [island postcode](http://www.maplin.co.uk/NearestStore.aspx?OrderCode=A21HY&source=17&location=po33%208hd) gives the Newport store only as an option.
I suspect that - instead of running calculations by travel time - somebody has manually identified island postcodes, mainland postcodes and separated them by zone so only those postcodes in the same 'zone' appear in the search... that's certainly my first instinct (I'd love to think they're doing a full journey check, but I somehow doubt it ;-) )
While it's not perfect (maybe the Newport address could be grouped separately, in case I happened to be going over to the island anyway), it's a step further than most location-based searches out there.
