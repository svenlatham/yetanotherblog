---
layout: post
title: "Improving boot speed of Raspberry Pi (Jessie)"
date: 2016-12-06 15:52:34 +0000
permalink: /2016/12/06/improving-boot-speed-of-raspberry-pi-jessie/
author: "sven"
categories: ["Uncategorized"]
---

A quick note for myself:  
Raspberry Pi hangs on "a start job is running for lsb no limit" - this is the network interface manager trying to start up its connections. If you have interfaces listed in /etc/networking/interfaces which do not exist, you might see a timeout or delay here.  
**Solution:** create a new file (and possibly folder if needed) in /etc/systemd/system/networking.service.d/reduce-timeout.conf

```
[Service]
TimeoutStartSec=5
```

This will drastically reduce the starting timeout for interfaces. I haven't tested in detail, but it looks like new interfaces will still load normally after boot.  
Worth noting that systemd first looks in /lib/systemd/ for various default configs, then looks in /etc/systemd/ for additional configs, before merging them all. The exact chain of configs as applied can be seen by running **systemctl status networking.service**  
[Source](http://unix.stackexchange.com/questions/186162/how-to-change-timeout-in-systemctl)
