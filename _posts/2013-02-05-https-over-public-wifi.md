---
layout: post
title: "HTTPS over public wifi"
date: 2013-02-05 12:31:59 +0000
permalink: /2013/02/05/https-over-public-wifi/
author: "sven"
categories: ["Uncategorized"]
---

LinkedIn supports HTTPS connections. If you go to <https://www.linkedin.com/> your connection will be secure and your session & data kept private.  
This is fine, and works well, until you click View Profile or click on a Notification. At this point it appears the site dives back to plain old HTTP. If you're not paying attention, you won't even notice.  
Why is this a possible cause for concern? First, this suggests the cookie does not have its secure flag set, which means the authentication cookie is also being sent in 'plain text' and is therefore sniffable by a third party.  
Second, any website being transmitted over HTTP is susceptible to manipulation. For instance, a third party could act as a proxy on a public wifi network and inject a piece of HTML or Javascript to, say, pop-up a dialog window asking you to re-authenticate.  
Note - this is all a fair amount of conjecture - I need to build a proof-of-concept (actually, [I'm sure many already exist](http://security.stackexchange.com/questions/14606/html-payload-rewriting)), and LinkedIn is certainly not the only example. I should also point out that at least this website asks for reauthentication when viewing/editing sensitive data, which is a plus point.
