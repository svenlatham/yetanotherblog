---
layout: post
title: "When is a Copy not a Copy?"
date: 2013-08-12 11:07:00 +0000
permalink: /2013/08/12/when-is-a-copy-not-a-copy/
author: "sven"
categories: ["Uncategorized"]
---

Xerox has received some likely unwelcome attention recently, with the discovery that their scanner-photocopiers are changing numbers under certain conditions.  
The issue was [highlighted by computer scientist David Kriesel](http://www.dkriesel.com/en/blog/2013/0802_xerox-workcentres_are_switching_written_numbers_when_scanning), who discovered that figures in a scanned construction plan did not add up: in the original one room is listed as 21.11m³, in scans this number changed to 14.13m³. Other errors were also evident, with different tests yielding different errors.  
[caption id="attachment\_871" align="alignnone" width="300"]![](https://www.yetanotherblog.com/wp-content/uploads/2013/08/7535-zahlenkolonnen-vorher-300x174.png) ![](https://www.yetanotherblog.com/wp-content/uploads/2013/08/7535-zahlenkolonnen-nachher.png)  
Before & After scanning - *David Kriesel*[/caption]  
Blame appears to be apportioned to the compression method used when saving the scan. Dot-for-dot reproductions of pages are quite large files, so various techniques are used to reduce the file size needed.  
It is suggested that if a document contains several similar-looking patterns on a page (such as a series of numbers) the scanner would record that both patterns are effectively the same and the reproduction would simply say 'this patch is the same as that patch, so just duplicate it again here' rather than recording both patches independently. If the quality is low enough, this might be *incorrectly* applied to two patches of a page which might look *similar*, when in fact they are slightly different.  
Again, this is hypothetical and does not appear to have been solidly confirmed, but would indeed be a potential side-effect of compression and is consistent with the results seen.  
Such errors might cause mere inconvenience, or they might lead to more substantial effects. Invoices and other financial documents could be subtly changed; doses of medical prescriptions modified, or incorrect construction plans leading to structural failure. One hopes that in many cases, trained practitioners might spot an error or question a seemingly erroneous value. After all, human errors (typos) are also likely to occur from time to time.  
Nonetheless, this demonstrates a flaw in a system users would hope to place some degree of trust in: changing digits is not the expected behaviour of any reproduction system!  
Xerox has [issued their own statement](http://realbusinessatxerox.blogs.xerox.com/2013/08/07/update-on-scanning-issue-software-patches-to-come/), and are planning to release a patch shortly.
