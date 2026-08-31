---
layout: post
title: "Speedy Search"
date: 2005-12-29 03:16:44 +0000
permalink: /2005/12/29/speedy-search/
author: "sven"
categories: ["Uncategorized"]
---

Of all the things I could've been doing over this holiday time, I've spent the time rewriting the search engine for Blogwise from scratch.  
  
Blogwise search is a bit of an embarassment at the moment - search results take forever to appear (that's 9 seconds +) and consistently holds the spot of the slowest search on [Grabperf](http://www.grabperf.org/).  
  
The reason for this is three-fold: lack of scalability, lack of decent hardware and lack of time. Over the past few months, page requests to the search have at least trebled. In the same time, the database itself has doubled in size. The search, which is currently live on Version 2, is a bit of a kludge. It has its own database system, thus removing the demand on the main server (a huge problem with Version 1), but it completely lacks any kind of scalability. When you run a search, you're effectively tying up an entire computer for the few seconds that it's dealing with your search.  
  
Although I originally had three servers load-balancing the search results, it wasn't distributing the load very well, so a search was taking 9 seconds on one server while the other two could have been idle.  
  
Version 3 was a first stab at resolving this, by breaking up the database into three chunks (assuming three servers) and having each one deal with a third of the database. With a blog database of 60,000 blogs this meant each one served results for 20,000 blogs - theoretically a better break-up of the load.  
  
I had to drop the rewrite suddenly due to the usual lack of time, and never really got back to it. However, with the glory of 9 straight days of home-time I've been able to get back in front of the computer and rewrite the entire search system as Version 4.  
  
Results are looking promising. Because of the way I've redesigned the database structure and the algorithms, the search is already giving results in under 1.2 seconds on a good day - that may not sound like much but this is before I put the new load balancing in place. The breakdown of the search results is the key bit - gathering search results takes almost all of the time; the final arrangement and rendering is a miniscule 0.1 second at the most.  
  
A good load-balancing system should see that time drop every time I increase the number of servers - with the three servers back in action on Version 4 code, search results should come in at around 0.4 seconds. That'll move me from the twenty slowest sites on Grabperf to just below the twenty fastest - neat!  
  
The load balancing system is already mapped out on paper. Every few hours the index will be refreshed. This is then divided up according to servers' various demands and resource availability. The new data is shipped to each search server and the aggregator is then updated with a new map of indexes. Give or take TCP and mapping overheads, this should crudely mean that more servers = faster speed. I like that kind of scalability!  
  
The search rewrite also coincides with a huge increase in the amount of data being searched - one thing I failed to mention is that the 1.2 seconds is inclusive of both the previous keyword index, but a new index of full-text RSS feeds. ie. the search will be indexing content as well as metadata (finally).  
  
As I get this thing rolled out, I'll write up more here. In the meantime, hope you're having a good time!
