---
layout: post
title: "Search Optimisations"
date: 2006-01-08 01:56:19 +0000
permalink: /2006/01/08/search-optimisations/
author: "sven"
categories: ["Blogwise"]
---

I'm still hacking away at the [Blogwise search](http://www.blogwise.com/search), trying to improve things. My latest move seems to have cut cached requests by up to a half (and sliced 0.5/0.6 seconds off the uncached search results). As ever, [Grabperf](http://www.grabperf.org/graph_hourly_multi_test-geomean.php?msmts=69&days=5) shows the details.  
The latest speed increase is because I've rewritten the aggregator as a HTTP server of its own (previously it was run from mini\_httpd). DBI and all the other modules are loaded in the server itself, so individual requests can be delivered immediately.  
In fact, the aggregator is clocking in at about 0.09 seconds for cached results - the 0.5+ seconds you see on Grabperf reflect other bits, such as page rendering & transmission, DNS lookups and TCP connection (Grabperf's servers are in the States).  
At some point, if anybody is interested, I'll write up how I'm doing this in detail.
