---
layout: post
title: "Compressing and Storing Time Correctly"
date: 2017-01-27 08:12:06 +0000
permalink: /2017/01/27/compressing-and-storing-time-correctly/
author: "sven"
categories: ["Uncategorized"]
---

After [earlier work with DATETIME and indexes](https://www.yetanotherblog.com/2016/09/07/mariadb-indexes-on-datetime-and-date-functions/), I am still seeing some performance issues with storing logs with a full timestamp. Since a lot of the reporting is based on day-on-day and week-on-week comparisons, it could be more efficient to store the date and time components separately.
For my purposes, I'm using time to a resolution of about 15 minutes so there's no real need to suffer the extra storage and performance overhead of working with a TIME field.
Instead, I've opted for a TINYINT with a value between 0-95 inclusive - one for every fifteen minutes of the day. Naturally, this is indexed.
The issue comes with how to convert time into these segments, and back again. Logically, 00:00 to 00:15 should beÂ the first segment, butÂ I have to be careful when reporting this back.
Technically if I'm quoting the range in a graph, there's no problem. It's between 00:00 and 00:15. If I'm forced to plot a point - say in a graph - the easiest solution would be to drop the dot at 00:00:00. The technicallyÂ *most accurateÂ*would be at 00:07:30.
That could be awfully messy, but it's the midpoint of each range and better thanÂ quoting a measurement (say, originally at 00:14:59.999999....) as 00:00:00 when it would clearly be better as 00:15:00.
In this case, I suspect simplicity prevails. Most normal people (i.e. not me) would be more comfortable seeing nice round numbers: 00:00, 00:15 and so on. Seeing 00:07:30, 00:22:30 and so on is likely to be unnecessarily confusing. Thankfully the incoming quality of data is not that precise, so nobody will scrutinise this.
Quoting the full range (00:00 - 00:15) would be more appropriate anyway, inÂ tables and text reports.
