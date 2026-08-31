---
layout: post
title: "Web Capture Redux"
date: 2004-06-13 17:44:51 +0000
permalink: /2004/06/13/web-capture-redux/
author: "sven"
categories: ["Uncategorized"]
---

Hooray for the Internet. I've finally managed to get a script together for capturing thumbnails of websites, for Blogwise's blog info pages.  
  
Last time I posted about this I was working on a Windows solution, and Brian started putting together a Java/IE combo tool (thanks Brian BTW). Both worked well but ideally I'd like a Linux based solution - that saves me leaving another computer on (which isn't a popular move in this household).  
  
A few weeks ago I spotted [this little program](http://www.boutell.com/webthumb/). Webthumb is a Perl script that launches Xvfb, a sort-of dummy windows environment, so you can run GUI-based programs within it but not have it display anywhere. It loads up a browser ([Mozilla Firefox](http://www.mozilla.org/products/firefox/)) within that virtual screen, and takes captures of a website. A little Perl script wrapper of my own, with appropriate resizing and cropping instructions and we're good to go.  
  
I also made use of a [Kiosk addition](http://tln.lib.mi.us/~amutch/pro/phoenix/fullscreen.htm) for Phoenix Firebirdfox to get rid of the toolbars, although it still needs some tweaking to get it working with the latest version of the browser.  
  
There are still a few slight snags. Popups still appear when a plugin is required (e.g. Flash) but they go away when the next website is requested. I still can't get Firefox to show full-screen either, so the captures are limited to 640x480, which is less than most sites are designed for these days. so I seem to get the top-left of any given website.  
  
These are all minor niggles though, and progress is certainly being made!
