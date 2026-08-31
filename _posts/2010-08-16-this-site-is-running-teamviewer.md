---
layout: post
title: "\"This site is running TeamViewer\""
date: 2010-08-16 09:42:15 +0000
permalink: /2010/08/16/this-site-is-running-teamviewer/
author: "sven"
categories: ["Uncategorized"]
---

Beware if you decide to use TeamViewer, a remote control app. It appears to launch a webserver on port 80 I think for some kind of NAT/firewall detection. In any case, if your computer is also used as a webserver this will cause a few issues :-)
The solution I have found (for Teamviewer 5 Windows) is to close the program (right click and exit; make sure it's completely closed). Then open the registry editor (Start menu > Run > regedit) and find your way to the following registry entry:
HKEY\_LOCAL\_MACHINE\Software\Teamviewer\Version 5\
and change ListenHttp from 1 to 0.
You must close Teamviewer first, I found that if you change it while Teamviewer is still running, the setting will be reset (back to 1) when the program is next closed.
