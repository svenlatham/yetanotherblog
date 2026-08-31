---
layout: post
title: "N770 Keeping Screen Display on"
date: 2009-12-02 11:03:08 +0000
permalink: /2009/12/02/n770-keeping-screen-display-on/
author: "sven"
categories: ["Uncategorized"]
---

I have begun to use my old Nokia 770 as a sort-of dashboard for our company's stats - a bit like a health screen. To achieve this I have created a webpage which just fits on the screen (in fullscreen mode) and periodically refreshes.
To keep the Nokia 770 display running, you'll need the following instructions (note, not manufacturer approved, use at your own risk!)
Install XTerm and run two gconftool-2 commands (all shown on [this page](http://labs.ideo.com/2008/11/10/tips-prototyping-on-the-nokia-770-tablet/)) - note, those gconftool commands do indeed extend for three lines. You need to enter them as one command.
Install Display daemon 'acmonitor' from [here](http://pupnik.de/800powr.html). This will allow you to set the display profile when on charge and on battery. Ideally you'll not want the tablet running at full brightness when it's on battery power!
I added 86400 (a day) which will show in your Display control panel as '1440 minutes' - that should be enough!
