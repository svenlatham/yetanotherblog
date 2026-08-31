---
layout: post
title: "Reporting Data with Daylight Savings Time"
date: 2016-09-15 10:18:16 +0000
permalink: /2016/09/15/reporting-data-with-daylight-savings-time/
author: "sven"
categories: ["Uncategorized"]
---

At the end of October it'll be [time to put the clocks back](https://www.gov.uk/when-do-the-clocks-change). We'll get an extra hour in bed to compensate for the hour lost at the end of March, and the bi-annual tradition of media articles asking whether we should [ditch the whole thing](http://www.bbc.co.uk/news/uk-11659848) will run again.  
For anybody dealing with dates and times, daylight savings can be a pain. If your job involves managing computers, you might well keep everything in UTC (/GMT) to save headaches. This is also sensible advice if you deal with multiple time-zones. By sticking to UTC, you avoid the annoying issue of living out the same hour twice one morning somewhere in Autumn.  
In city centres, retail and business, our data is very much dictated by local time, not UTC. If the shops open at 8am, it will be based on local time. Work starts at 9 sharp, even if your previous night's sleep was rudely shortened by sixty minutes.  
For this reason, when we (meaning I - my [company](https://www.noggin.bi/)) report on city centre figures, we use local time. It keeps the peaks and troughs of the day in order. If we used UTC, it would be harder to compare a July day with a November day - they'd be off by an hour.  
We also store data in local time, mainly because of the complexities involved in constantly switching between UTC and local time. It's a minor issue, buts adds time to every query and makes the underlying system more complicated. Some might store in UTC, and convert. However you do this you'll still need to decide what to do at 2am at the end of October, when time steps backwards.  
**Springboard**  
For some useful observations, I needed to look for high-traffic places with a decent night-time economy. These are from Heart of London (West End):  
![heartlondon-springboard](https://www.yetanotherblog.com/wp-content/uploads/2016/09/heartlondon-springboard-300x98.png)  
First observation is that all the times appear to be based on local time. The general peaks/troughs appear to line up irrespective of daylight savings time. Sunday is shown in grey on these charts.  
There's not a lot to go on here, but March 2015 looks like a straight line between 1am and 3am. March 2014 has a data point in the non-existent time, but there's a noticeable drop. By comparison, October (where we live 1am-2am twice) seems to have a bump at 3am. This is also what I saw in the 2014 data - not shown here.  
Given that there's data in the March 2014 slot, I wonder if this is being accommodated in Springboard's stats - and if they're similarly compensating in the early hours of October's backwards step.  
**Highways England**  
Looking elsewhere, Highways England publishes traffic data across its network on a 15 minute basis. They also use local time - again, this makes sense as traffic demands are dictated by the clock.  
In March, they simply skip over the non-existent time. 1am to 2am is missing in the data, so for one day per year there are 23 hours' worth of records.  
In October, there is something weirder. The hour is repeated, but the data is inconsistent. This is the traffic data on a section of the M25 over October, with 1am-2am counted twice. Time Period shows the end of the 15 minute section as measured; the last column shows the number of vehicles of a given length over this period.  
![he-october](https://www.yetanotherblog.com/wp-content/uploads/2016/09/he-october-300x285.png)  
It looks like the sensor has managed to send something across throughout the affected time, but the data is largely missing. Interesting that the time period reports as :59 seconds only in this highlighted period, and for the two records where this *doesn't *happen (01:44:00 and 01:59:00) we seem to have data. I wonder if this is a bug of some kind.  
**Conclusions**  
These are the two main data suppliers I have an interest in, but it'd be useful to gauge feedback from elsewhere. This is a tricky issue. The ultimate goal is to show something which is meaningful to the reader, but we need to do this in a way that does not affect comparisons at the hourly level.  
In one way this is a fairly moot point. The volume of traffic at 2am on an out-of-season Sunday is likely inconsequential for many. However it does raise an interesting challenge for reports and figures, and is just one of many subtleties to consider in this sort of analysis.  
*Final thought: is it possible that the change in daylight savings time actually attracts people?*
