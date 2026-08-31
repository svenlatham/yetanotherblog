---
layout: post
title: "Vodafone transparent proxy - BMI Javascript at 1.2.3.4"
date: 2007-08-20 12:33:51 +0000
permalink: /2007/08/20/vodafone-transparent-proxy-bmi-javascript-at-1234/
author: "sven"
categories: ["vodafone"]
---

Vodafone UK appear to run a transparent proxy on HTTP connections through its network. This is most apparent when using a laptop via a mobile phone to access the Internet.  
They inject HTML code at the beginning of most (but not all) webpages which forces the inclusion of an external Javascript file.  
`<script src="http://1.2.3.4/bmi-int-js/bmi.js" language="javascript"></script>`  
This code is used to replace on-page images with more highly compressed alternatives, presumably to reduce bandwidth usage on their network. This is most noticeable when browsing photo sites such as Flickr and Facebook albums.  
The code seems largely well-behaved (although I have seen reports that it can break XHTML/XML documents, I haven't experienced this personally) and is not a huge intrusion on my browsing experience ... if anything it may help to speed things up, and keep my data bill down!  
Still, if anybody is unaware of this occurring and is wondering why their photos look a bit rubbish, this is why!  
([Google link](http://groups.google.com/group/comp.lang.javascript/browse_thread/thread/2377c84c53e8183b/de71e15defce45d2?q=bmi_SafeAddOnload&rnum=2&hl=en#de71e15defce45d2))
