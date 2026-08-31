---
layout: post
title: "Odd Behaviour in Google?"
date: 2004-05-16 12:41:46 +0000
permalink: /2004/05/16/odd-behaviour-in-google/
author: "sven"
categories: ["Uncategorized"]
---

Argh. Google seem to have stopped obeying redirects properly.  
  
If you search for "Workx in progress" on Google (x is intentional), the  
top result looks like a Blogwise details page for that blog. When you  
click it it goes to a different site.  
  
What the Googlebots are doing is looking at similar.php (a script that  
finds similar sites, given a blog ID). similar.php redirects to the info  
page of the new blog. In the user's browser the URL changes (as it  
should). Google is not changing the URL however, retaining the similar.php  
URL, but analysing the new content.  
  
Since similar.php chooses its blogs on a semi-random basis, the user often  
gets a different blog to the one they think they're going to get.  
  
This is actually causing me quite a headache. I don't know why they've  
changed this behaviour (I'm sure there's a good reason?), but it means I'm  
getting quite a few emails from bemused Blogwise users, asking why this  
particular Google result goes to a different site.  
  
I suppose the best solution is to disable similar.php in robots.txt, but  
that doesn't fix Google itself!
