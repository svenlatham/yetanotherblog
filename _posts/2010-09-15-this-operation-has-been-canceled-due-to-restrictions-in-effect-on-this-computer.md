---
layout: post
title: "\"this operation has been canceled due to restrictions in effect on this computer\""
date: 2010-09-15 08:47:30 +0000
permalink: /2010/09/15/this-operation-has-been-canceled-due-to-restrictions-in-effect-on-this-computer/
author: "sven"
categories: ["Uncategorized"]
---

If you get the following message when clicking links on Outlook (2003, 2007, 2010):
**"This operation has been canceled due to restrictions in effect on this computer. Please contact your system administrator"**
It is most likely that your browser's association has become corrupt in some way.
I found the easiest way to cure this was to ensure the htmlfile registry key was correctly set up:
You will need to open regedit.exe and go to HKEY\_Local\_Machine\Software\Classes\htmlfile\shell\open\command
There should be a string value inside there called (Default) - in most cases it seems the following should work:
"C:\Program Files\Internet Explorer\iexplore.exe" -nohome
Make sure this is correct, close everything down and restart Outlook.
NB. make sure Outlook is completely closed - ie. OUTLOOK.EXE is no longer in task manager.
[Microsoft support issue on the matter.](http://support.microsoft.com/kb/310049)
*Usual disclaimer applies. Do this at your own risk. No warranty, etc. etc.*
