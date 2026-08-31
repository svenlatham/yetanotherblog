---
layout: post
title: "Now in HTTPS"
date: 2013-07-05 14:40:20 +0000
permalink: /2013/07/05/now-in-https/
author: "sven"
categories: ["Uncategorized"]
---

This blog should now be served over HTTPS. As of today, I've switched all traffic coming in on regular ol' port 80 to its more secure cousin, 443.  
In human terms? Most websites use 'HTTP' - your computer asks for a page (or an image, or anything else) and the server dutifully sends it back. In most cases, nothing is encrypted which means that everything you see and do on a webpage can be viewed by a third party.  
If you're in your local coffee shop using their free wifi, somebody could well be watching everything you do.  
HTTPS is the secure version of this. By using this, everything between your computer and the website itself is encrypted. Nobody in-between can tamper with, or listen in on what you are looking at.  
**Why is this important? It's just a blog.**  
Quite right - most people probably don't care that they can now read this site over a secure connection - they've nothing to hide. :-)  
However, anybody making comments or registering an account here will potentially be giving their email or other personal details as part of the process. Furthermore, I write articles on this blog from various locations and I want to ensure my own details and credentials are not stolen.  
**What are the downsides?**  
For starters, HTTPS slows down websites a little. It's not much (maybe a tenth of a second) but it is a measurable side-effect.  
Second, the technique used does not work for Internet Explorer users on Windows XP ([and a few other cases](http://en.wikipedia.org/wiki/Server_Name_Indication#Client_side)). This is potentially still quite a big audience, but the stats for this blog show that it's of little concern in my particular case.  
Third, it costs a bit of money to get a certificate. Not a huge amount, but greater than zero.
 
All in, I do think the benefits outweigh the negatives and, while the use on a blog is of marginal benefit, I have plenty of other sites and web apps which I am also trialling on SSL.
