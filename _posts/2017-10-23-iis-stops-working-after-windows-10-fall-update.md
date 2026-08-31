---
layout: post
title: "IIS stops working after Windows 10 Fall Update"
date: 2017-10-23 07:51:12 +0000
permalink: /2017/10/23/iis-stops-working-after-windows-10-fall-update/
author: "sven"
categories: ["Uncategorized"]
---

After installing the Fall Creators Update on Windows 10, IIS promptly stopped working.  
In the event viewer, the following vague message appeared on various app pools:  
`The worker process for application pool 'DefaultAppPool' encountered an error 'Cannot read configuration file  
' trying to read configuration data from file '\\?\', line number '0'. The data field contains the error code.`  
[Ajeet Yelandur had a solution](https://www.ajeetyelandur.com/2017/10/Windows-10-Fall-Creators-update-crashes-App-Pool/), and it works well:  
> Stop “Windows Process Activation Service” and “W3SVC” service and clean out (delete) all the files under C:\Inetpub\temp\AppPools\*. Start your services and the sites should be back to work.

Thank you Ajeet!  
(Posted here to help other searchers. It took me a while to find the solution amongst increasingly noisy Google results.)
