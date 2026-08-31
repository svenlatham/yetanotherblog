---
layout: post
title: "Tip of the Day"
date: 2003-11-21 07:06:02 +0000
permalink: /2003/11/21/tip-of-the-day/
author: "sven"
categories: ["Uncategorized"]
---

Samba Server can be a real bastard to get working sometimes.

If you ever get the error *'getpeername failed. Error was Transport endpoint is not connected'* try:  
`smbpasswd -a nobody`  
then hit Enter twice (for a blank password). It just worked for me, after about an hour's reinstallation and Google searching. Why can't error messages be less unfriendly :'(
