---
layout: post
title: "HSBC Site not Working?"
date: 2008-05-14 21:38:22 +0000
permalink: /2008/05/14/hsbc-site-not-working/
author: "sven"
categories: ["Uncategorized"]
tags: ["website", "hsbc", "gzip", "server"]
---

Interesting - the HSBC website www.hsbc.co.uk appears to *only* deliver content in GZip. Any user agent trying to get to it that does not support GZip (through the Accept-Encoding header) will just get nothing from the server (it holds the connection but delivers nothing).  
If, for whatever reason, you're trying to get to the HSBC website with a simpler (ie. non-mainstream) browser this might be why. I've been getting very slow and funky (ie. corrupt) images in Firefox for a while - wonder if it's related?
