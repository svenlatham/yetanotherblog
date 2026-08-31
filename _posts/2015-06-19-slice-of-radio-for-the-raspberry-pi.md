---
layout: post
title: "Slice of Radio for the Raspberry Pi"
date: 2015-06-19 09:36:01 +0000
permalink: /2015/06/19/slice-of-radio-for-the-raspberry-pi/
author: "sven"
categories: ["Uncategorized"]
tags: ["radio"]
---

As part of an ongoing project I have been trying to get multiple Raspberry Pis to talk to each other across a city centre. First, they used wifi for ad-hoc networks. In some cases I've used 3G dongles to connect over the Internet. Both have their downsides. Now, I am looking at radio communications to build a mesh of devices.  
After a bit of investigation I've purchased three [Ciseco Slice of Radio devices from Pimoroni](http://shop.pimoroni.com/products/slice-of-radio-wireless-rf-transciever-for-the-raspberry-pi) or [Ciseco themselves](https://store-8d73a.mybigcommerce.com/slice-of-radio-wireless-rf-transciever-for-the-raspberry-pi/). These are fairly straightforward devices that enable the Pis to communicate over radio via the serial port.  
There'a a fair amount of information out there about configuring them (although you need to look for the chip itself - SRF - rather than 'Slice of Radio' in Google) - [this is the best resource](http://openmicros.org/index.php/articles/88-ciseco-product-documentation/258-srf-description) I found (with handy links at the bottom).  
These devices send 12 byte packets by default, so I've written a low level protocol to support a mesh-style network. This will allow the individual devices to relay messages through the network and eventually communicate with a server on the Internet. More on that soon.  
Meanwhile, the range of the devices *as bought* is somewhat limited. I have two devices successfully talking to each other over radio, from the front of the house to the garage in the back garden. Straight-line this is going through two internal walls, an external wall and a metal garage door - so not too bad.  
In production this is likely to be more challenging, so I will need to try adding an antenna to the device. There are two types I can use - u.FL and a simple (vertical) wire.  
I'm an absolute novice with radio so please excuse/correct me if something is wrong! These are more notes than anything concrete!  
u.FL supports the 'standard' coaxial aerial found on wifi hubs and - as far as I can tell - this is the connector (presuming u = micro). One can then get a u.FL to SMA (bigger) connector and start adding standard antennae.  
[Here's a fairly good overview from Instructables.](http://www.instructables.com/id/interfacing-ufl-connectors/)  
Option two is to use a 'wire whip' or 'whip antenna' connected directly to the board. For an 868Mhz device this needs an 82.2mm vertical wire.  
In terms of aesthetics and practicality I'd rather not have a vertical wire coming directly out of the Pi - [as shown here](http://asliceofraspberrypi.blogspot.co.uk/2013/08/wireless-serial-communication-with.html) - and need to figure out the options.  
For the antenna, then it looks like I'll need the following:  
[u.FL connection for mounting on the board itself](http://shop.ciseco.co.uk/d046-u-fl-surface-mount-connector/). - £1.00  
[u.FL to SMA cable](http://shop.ciseco.co.uk/u-fl-to-sma-pigtail/) - £3.33  
[SMA 'rubber duck' aerial.](http://shop.ciseco.co.uk/868-915mhz-rubber-duck-antenna/) - £4.58  
Total material cost of adding the aerial is therefore £8.91 + VAT  
There are various other issues to deal with, but this seems like it'll give a significant signal boost for the devices. As I explore further, expect more updates!
