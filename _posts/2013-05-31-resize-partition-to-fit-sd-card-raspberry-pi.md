---
layout: post
title: "Resize partition to fit SD card [Raspberry Pi]"
date: 2013-05-31 08:45:18 +0000
permalink: /2013/05/31/resize-partition-to-fit-sd-card-raspberry-pi/
author: "sven"
categories: ["raspberry pi", "linux"]
---

I often need this... originally from [tomahhunt on the Arch Linux forums](http://archlinuxarm.org/forum/viewtopic.php?f=31&t=3119#p18160)  
The following commands resize the main partition of a new Arch Linux installation on a Raspberry Pi to fit the full disk.

Switch to root (sudo or su)  
fdisk /dev/mmcblk0

Delete the second partition /dev/mmcblk0p2:  
d > 2

Create a new primary partition and use default sizes prompted. This will then create a partition that fills the disk:  
n > p > 2 > enter >enter

Save and exit fdisk:  
w

Now reboot. Once rebooted:  
resize2fs /dev/mmcblk0p2

Done!
