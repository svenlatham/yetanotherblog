---
layout: post
title: "In-Car Web Cameras"
date: 2013-05-03 18:59:16 +0000
permalink: /2013/05/03/in-car-web-cameras/
author: "sven"
categories: ["hacking", "social"]
---

Today and yesterday I've been spending a little bit of time putting together a Raspberry Pi-based webcam for my car. The idea is straightforward enough, I want something recording the road around me just in case - we're not quite at [Russian levels](http://www.youtube.com/watch?feature=player_detailpage&v=itMdLTd1l4E#t=366s) but it's a precaution I'd prefer to take. It also might come in handy if [meteors fall](http://www.youtube.com/watch?v=90Omh7_I8vI) or the [sea comes in](http://www.youtube.com/watch?feature=player_detailpage&v=IQqmp9OOE1E#t=37s).
Using [motion](http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome), a Creative LiveCam and the [instructions I found here](http://jeremyblythe.blogspot.co.uk/2012/06/battery-powered-wireless-motion.html) I set up something which appears to work reasonably well and doesn't instantly fill up theÂ paltryÂ 4GB card I have in the Raspberry Pi.
For those not yet aware, Raspberry Pis are very cheap computers - of the order of Â£20 - which can be powered from a phone charger (mains or, in this case, in-car) - which makes them incredibly good for fiddling about on projects like these.
I have the camera capturing at 1280x960 at one frame/second. This seems to give a reasonable balance between quality, sense of motion and processing capability. When the car is stationery and there is no visible activity it does nothing, however if motion is detected in the image the device begins to record both higher quality images and video.
[![01-19700101010608-00](https://www.yetanotherblog.com/wp-content/uploads/2013/05/01-19700101010608-00-300x225.jpg)](https://www.yetanotherblog.com/wp-content/uploads/2013/05/01-19700101010608-00.jpg)
I also have a small wifi dongle in the device, which means I can upload the images automatically when I'm in range of the home wifi, and I can use wifi triangulation to figure out where the car is (poor man's GPS, basically).
Technical issues so far:

* Supplying power to the Raspberry Pi is a bit tricky. I'm using the car stereo which has a reasonably clean 5V. The Pi resets when I start the car which isn't particularly surprising, but I risk corrupting the on-board storage if I do this.
* The webcam is not really ideal. It's good for indoor videoconferencing and will return to that job shortly. If I spend a few more quid I should be able to get a better quality image and decent night imagery.

However, technical issues are only one part of this experiment. I'm also trying to consider the social aspects. For one, the webcam is pretty obvious (and glows blue when operating). This is a good deterrent - but might attract undue interest.
I will also be driving in places where photography is usually forbidden - UK customs tend to frown on these things (I don't particularly think the French care less, they're so laid back :-) )- so I would be well advised to tip the camera away at the cross-channel port.
Finally - and this is the bit that really interests me - there is the data that could be collected. What right do I have to record others' movements? In public it's fair game provided I'm not using these for profit but consideration needs to be made particularly on private land and overseas.
However, this kind of capture really fascinates me ... imagine for a moment if these devices uploaded to the web - to some kind of central processing house (much like [Google Goggles](http://www.google.co.uk/mobile/goggles/#text) or [Waze](http://www.waze.com/)Â might aggregate your data to learn or otherwise use it). These images could be used in some form of Google Street View (albeit poor quality!), to build a remarkable timeline of environments' development, or by law enforcement officers to [track cars based on your numberplate (ANPR](http://en.wikipedia.org/wiki/Police-enforced_ANPR_in_the_UK)).
If nothing else, the more cameras there are on the road, the more often we will capture extraordinary events on video. For me though, this continues to be an interesting little technical side-project, hopefully with some positive benefits and some food for thought.
