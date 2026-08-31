---
layout: post
title: "Automating Press Clippings"
date: 2014-11-11 11:38:24 +0000
permalink: /2014/11/11/automating-press-clippings/
author: "sven"
categories: ["Uncategorized"]
---

One of my projects is running [a journal devoted to Business Improvement Districts](https://www.bidintel.co.uk/) (BIDs) in the UK. These are organisations formed around town & city centres to improve the local environment and trading conditions.  
We've just started recording mentions of BIDs in the press, which is a useful way to track industry updates. At first, I was running this manually, but it because apparent pretty quickly that this would be unsustainable, so I looked at how to automate as much as possible.  
I think I have a solution, dipping into various methods I've been meaning to use for a while.  
The system starts by receiving an update from Google Alerts on a particular topic. This email normally contains 20-30 links to various worldwide news articles.

## Email to script

This was something I've used before but the basic gist is that an email address is piped directly to a script. I created a new account on a domain I manage and set it to pipe to a script. In Postfix the virtuals file tells the server that *username@domain.tld* is mapped to a local alias, let's say *mailcatcher*. In aliases, this alias is mapped to a script. The line looks like this:

```
mailcatcher "|/var/mailscripts/script.php"
```

Run all the mappers, reload Postfix and the email address is set up. Now, provided that script is executable, the entirety of the email will be sent via STDIN to that script.

## Message Queueing

I've dabbled but never got too far into message queueing. The high-level idea is that pieces of information ('messages') are pushed around and progressively worked on by a number of scripts. These scripts are small - they usually do only one job, but they manipulate that message in some way or do something in response to it. Once a script's work is done, the result is usually passed on to another. Depending on the complexity of the system, multiple scripts might work on a single queue of items.  
The outcome is a chain of incremental processing, much like a factory line. For this task it works extremely well as I can break a fairly complex chain of actions into digestable pieces, so once an email is received the following chain is followed:  
Receive email via mail script (above). This adds the whole email contents as a message to a 'mail' queue.  
A script watches the 'mail' queue and takes any new messages. Its job is to find all the links in the email and create one new message for each link. These go into a 'link' queue.  
Another script on the 'link' queue checks the database for known links to see if the link is a duplicate. Any message that isn't a duplicate goes into the 'retrieve' queue.  
The 'retrieve' script follows the URL and grabs a copy of the page in full. This then goes into the 'parse' queue.  
The 'parse' script parses the HTML and looks for common elements (headline, publish date, source, etc.). Once it has enough information, these elements end up in a message in the 'publish' queue.  
The 'publish' script creates a new database entry for the article and publishes it to WordPress. The article clipping is now live.  
There are several good reasons for breaking up a procedural process into separate scripts and queues. For one, it's very easy to scale up. Parsing might be a great deal harder (require more processing power) than anything else, so could need more machines working on it. Grabbing the contents of a URL is notoriously unreliable, so if a script fails here the queue entry is merely postponed until later when it'll try again.  
Debugging is also trivial. I can simply watch a particularly (/troublesome) message work its way through the system and see exactly where any errors are coming up.  
This is also good for development. The parser only knows how to read a pre-defined selection of news pages, so if a new page arrives which can't be parsed I need to add new rules to the parser. By holding the message in a queue I simply postpone the message until the parser is upgraded and the message can continue through the system.  
There are a fair few messaging systems out there which handle this stuff well, but I needed something quick & dirty, so wrote something up to handle this myself. Down the line, I'm planning to move to a more robust, distributed system.

## Web Interface

Many of the news articles are rejected because they cover regions we don't care about (US, New Zealand, Canada, etc.) so I use domain blacklisting to disregard foreign news sources. This isn't fool-proof. Some news aggregators are international, and might carry articles we care about.  
Furthermore, once a UK-based article is picked up, I need to figure out which BID it relates to. Doing a simple search for town names is not enough ('Rugby' was pretty popular because of the sport-related mentions on pages), so I look for '{town name} business' and phrases like that. It gets about 75% of the results satisfactorily.  
For the rest, I need to manually intervene and provide a BID association myself.  
This is the bit I need to work on. Currently the parsers and labelling systems are all hardwired. No good. It's manageable for now, but in the near future I'm going to need a web interface to handle all the messages that don't get through.

## Overview

The whole system is running automatically and probably saving me at least an hour a day. It took around 8 hours to build so I'm happy with the returns. Having now put together a basic framework I expect to be able to use this for other tools as well.  
Automation was one of the key lessons I learnt a decade ago with Blogwise, a blog directory that was easily attracting 100+ new submissions per day. The labour involved in handling submissions was phenomenal and automation scaled up in ways labourers could not.  
It's now something I advise others to do as well, particularly with repetitive tasks. A relatively small development investment can replace many man-hours of activity, and the economies of scale are often much more impressive.
