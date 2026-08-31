---
layout: post
title: "Setting users' Home page to a HTTPS page"
date: 2012-08-17 19:25:00 +0000
permalink: /2012/08/17/setting-users-home-page-to-a-https-page/
author: "sven"
categories: ["Uncategorized"]
---

I've been working a fair bit on setting users' homepages within business recently. First temptation was to point directly to the secure Extranet page, but more recently I've come to the conclusion this is a bad idea:
- For security reasons you probably want authentication on this page ... even the basic authentication dialogue box takes a little while to load on slower systems. If the user wanted to do something else (normally go to Google...) this is nothing but an annoying interruption.
- Secure pages take longer to load than insecure pages. Any startup delay is simply irritating.
- The user may be in a non-private location or presenting something where displaying sensitive Intranet information is unwanted and could potentially be damaging to the business.
- Public wireless networks often redirect users to a sign-in portal. When this redirection occurs with HTTPS pages the user is often presented with a nasty and concerning security warning as the redirection system cannot interfere with HTTPS pages.
Thus, if setting users' homepages I now prefer to create a non-secure landing page with basic tools such as Google search box and links to useful sites (including Intranet and webmail - these are, after all, secured resources)
By the way, if you're using cookie-based authentication on your Intranet/Extranet don't forget to ensure your cookies are set to be. secure. That way, they won't leak on to an insecure network.
