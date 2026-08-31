---
layout: post
title: "Avoiding SD Card Corruption on a Raspberry Pi"
date: 2015-09-04 11:16:14 +0000
permalink: /2015/09/04/avoiding-sd-card-corruption-on-a-raspberry-pi/
author: "sven"
categories: ["raspberry pi"]
---

As part of my visitorÂ mapping project, the bulk of my time has been spent throwingÂ curse words at the SD cards.
Raspberry Pis depend on SD cards. There's little other choice. More specifically, the newer devices use Micro SD cards. It's fairly incredible to realise just how much data can be stored on somethingÂ around the size of a thumbnail, but I digress.
The problem with these cards (& flash memory in general) is that they're very sensitive to corruption. Any power fluctuation or problem writing isÂ a potential problem, with a real chance that the next boot will end in failure/disaster.
In my experience (ten devices in lab conditions; regular reboots) failure rate was as high as one in ten reboots. Slightly oddly,Â software resets (i.e. rebooting from the command line) appeared to fail more oftenÂ than unpredictable power loss.
**Read-Only is a winner**
There is a way to boot a Raspberry Pi in read-only mode, although it requires a bit of care. I found a couple of ways to do this, by editing the boot config file and by setting the fstab to boot as read only.
The consequences are hopefully clear - nothing is retained. However, it's also possible to temporarily remount the file system in writeable mode (and revert shortly after).Â My softwareÂ is capable of self-updating, and writes its logs to the filesystem in case of Internet problems. Both work very well.
[This website](https://hallard.me/raspberry-pi-read-only/) gave the bestÂ instructions. It includes removing a bunch of daemons that - frankly - I had no need for. I also removed fake-hwclock (for reasons which I'll describe on another post)Â andÂ preferred mounting ramfs on places like /var/log/ over linking.
The results have been pretty impressive. Since switching to this method I haven't had a single corruption issue (despite many tens of reboots)
**Power is a concern**
I suspect that one of the big problems is power, and began testing with a voltmeter. My suspicion is that brownouts - i.e. dips in power - were causing reboots and corruption.
The latest Raspberry Pi hardware supports a configuration that boosts the current to USB drives. Setting max\_usb\_current=1 in /boot/config.txt appears to [increase the per-device supply](http://raspberrypi.stackexchange.com/questions/27708/is-setting-max-usb-current-1-to-give-more-power-to-usb-devices-a-bad-idea) to 1.2A which avoids many of the power-related issues on high-demand peripherals.
My non-scientific and unmeasured experience confirms this. I've seen much betterÂ performance and reliability as a result, and - although can't be sure - I suspect this has helped the SD card woes as well.
In any case - touch wood and all that - this appears to have solved the corruption issues.
