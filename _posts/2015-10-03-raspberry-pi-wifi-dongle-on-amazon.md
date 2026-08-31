---
layout: post
title: "Raspberry Pi Wifi Dongle on Amazon"
date: 2015-10-03 14:56:23 +0000
permalink: /2015/10/03/raspberry-pi-wifi-dongle-on-amazon/
author: "sven"
categories: ["raspberry pi"]
---

Slightly annoyed to discover that my most recent batch of USB wifi adapters, sold as "for Raspberry Pi" are not quite compatible.  
For my various wifi projects, I've been buying up lots of little wifi adapters. All are labelled in the same way "USB Wifi Adapters for the Raspberry Pi - By New IT". It looks like they're all [based on this](https://www.newit.co.uk/shop/all-raspberry-pi/Pi-Networking/WiFi_Nano) from supplier 'New [![IMG_20150927_095541](https://www.yetanotherblog.com/wp-content/uploads/2015/09/IMG_20150927_095541-300x192.jpg)](https://www.yetanotherblog.com/wp-content/uploads/2015/09/IMG_20150927_095541.jpg)IT' (whom I've no reason to believe are involved in the issues here).  
The first few batches worked exactly as I wanted. Plug and play.  
The most recent batch has, however, been an entirely different story. They're simply different.  
The picture shows two USB devices. On the left is the most recent, non-working device. On the right is the working device. The most notable difference is the '802.11n' label is on a different side for each.  
**What's the difference?**  
It's all in the internals. Despite there being hundreds of wifi products they're all based on a surprisingly small number of variants.  
The working version is based on a chipset from Ralink, the RT5370. This works out of the box for the Raspberry Pi, seems to be a good performer, and - crucially for me - supports monitor mode (so it can act as an access point too).  
The problematic version uses the Ralink 8188 (RT8188) chipset. This doesn't have full support in the Raspberry Pi, and frankly it's been a pain in the backside to work with. I have a box full of old USB wifi dongles; most seem to be based on RT8188 and never really had much luck with them.  
It's possible to get them up and running, by compiling special drivers, but frankly it isn't worth the effort and I've had lots of memory leaks and other issues with them.  
**Be careful what you buy**  
So, back to Amazon. It seems that some devices sold as 'for Raspberry Pi' are in fact not ideal - and take a lot of work to get going. This shows up in the reviews as it looks like a few people have been stung.  
The whole thing isn't helped by Amazon's peculiar supplier system, where it opts for the cheapest supplier based on the product you choose. It looks like one or two suppliers have these RT8188 chips and are selling them under the wrong label - no idea if intentional or not.  
Thankfully it's fairly easy to pick the right supplier. Make sure you choose 'New IT'. I've just ordered another four devices from them and they work fine, straight out of the box, for the Raspberry Pi. Yes, they're a bit more expensive but they work!  
Now to decide whether it's worth my effort negotiating Amazon's support line and sending the two dud devices back...
