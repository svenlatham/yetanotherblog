---
layout: post
title: "Post from Blogger API"
date: 2003-09-28 22:29:43 +0000
permalink: /2003/09/28/post-from-blogger-api/
author: "sven"
categories: ["Uncategorized"]
---

If you have a Nokia 3650 and are using some kind of bluetooth connection to it you've probably found that when you try to connect to it from the computer it crashes, probably taking explorer with it. It sucks. This assumes the drivers are installed, as well as mRouter and your phone software.

This is an annoying consequence of the way the connections are made. Basically when you connect to the Nokia 3650 it'll immediately disconnect and try to initiate a connection back to your PC. My Bluetooth thingy can't cope with this and usually crashes.

The solution lies in how you connect in the first place, and which COM ports are allocated. If you right click the Bluetooth icon in the system tray and choose 'Advanced Configuration' you can check/tweak which COM ports are used. By default (I think!) Incoming connections come in on COM3 (Local Services tab) and outgoing on COM4 (Client Applications tab). If they aren't like this you ought to fix them (and then probably reboot).

Now, double click the mRouter icon in your system tray. You should get a list of Connections, many will be labeled 'Bluetooth'. Make sure COM3 is checked. Then, make sure COM4 is checked. If COM4 is already checked de-select it then re-check it

Basically the process of checking COM4 initiates a connection to your phone. When prompted (assuming you haven't paired and authorised the connection), the phone will connect back on COM3. Therefore in your PC Suite use COM3 as your phone comms port.

If you found this article useful let me know. I spent ages trying to figure out how to connect my phone. Then ages more trying to figure out how to connect in such a way that it didn't crash Explorer on the way!
