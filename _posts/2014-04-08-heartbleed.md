---
layout: post
title: "Heartbleed"
date: 2014-04-08 13:08:31 +0000
permalink: /2014/04/08/heartbleed/
author: "sven"
categories: ["google", "server", "linux"]
---

A vulnerability has been found in the encryption library OpenSSL, used by a huge proportion of web and Internet services. This bug allows malicious users to access bits of memory on the server and potentially read enough information to render the encryption useless.  
Worse, having obtained the right data, they could compromise the security of past and future communications allowing eavesdropping, impersonation and stealing of data.  
The vulnerability, known as [Heartbleed](http://www.heartbleed.com/), was found by researchers at Google and Codenomicon. While publicly announced only yesterday (7 Apr), it seems the bug has been present since December 2011, and was part of a release in March 2012.  
The various affected Linux distributions have been speedily updated and I updated our servers this morning. We must now wait and see how quickly the fixes will be applied to other servers and systems.  
The effect of this bug is serious: it undermines the security protocols used throughout the Internet, and an attack is apparently undetectable in ordinary logs. This means that high-profile websites might be well-advised to renew their security certificates, so that any 'exposed' details cannot be used in a future attack.

* [Heartbleed website](http://heartbleed.com/)  
* [Online tool for testing websites](http://filippo.io/Heartbleed/)
