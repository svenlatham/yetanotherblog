---
layout: post
title: "Email Forwarding & SPF"
date: 2014-09-22 20:03:25 +0000
permalink: /2014/09/22/email-forwarding-spf/
author: "sven"
categories: ["Uncategorized"]
tags: ["mail", "spf", "servers"]
---

![mail](https://www.yetanotherblog.com/wp-content/uploads/2014/09/mail-300x200.png)A friend emailed me the other day to ask why their hosting company have announced they will stop forwarding.  
Roughly speaking, they have an email address joe@customdomain.com which is hosted by said company. This forwards to their Gmail address joespersonalaccount@gmail.com [these are, if you hadn't guessed, not their real emails].  
The company has stated that they will no longer allow forwarding of emails from the custom domain to an external server. *Why?* my friend asked. It is, after all, a quite normal thing to do with domains.  
As far as I can tell - it looks like the reason is down to the way popular mail services filter spam. Google's GMail, for example, uses a thing called [SPF](http://en.wikipedia.org/wiki/Sender_Policy_Framework). This is a mechanism that checks whether emails came from a legitimate source.  
Let's say bob@bigcorp.com is sending my friend Joe an email, but they use his Gmail account directly - this is the simplest path:  
1. Bob writes the email and sends it. The mail server at bigcorp.com looks up the mail server handling Gmail.com accounts and connects to it.  
2. The mail server at Gmail.com receives the email and puts it in Joe's inbox.  
Now, the mail server at Gmail.com is applying SPF. This looks up the public record for bigcorp.com to see which mail servers have authority to send from that address. The mail server that sent the mail to Gmail is indeed legitimate, so it's allowed through.  
Now, Bob sends another email, this time to joe@customdomain.com  
1. Bob writes the email. The bigcorp mail server looks up customdomain.com, finds its mail server and connects to it.  
2. The customdomain.com mail server realises it's supposed to forward mail on, so once it has the email it finds the gmail.com mail server and resends the email there.  
3. The gmail.com mail server receives the email and puts it in Joe's inbox.  
So, same as last time, the gmail.com server applies SPF. However, this email didn't come directly from bigcorp.com, it came via customdomain.com. This isn't on bigcorp's list of authorised servers, so as far as Gmail is concerned this email could have been forged. It's quite possible the email will end up in the junk folder.  
Worse still, if lots of emails come via customdomain.com Gmail might start thinking the entire domain is spammy. This is partly why I suspect the hosting company want to avoid forwarding. Ending up on spam blacklists is a costly, damaging affair.  
This might appear like a weakness of SPF, but there is a fairly reasonable solution to this. I use Google Apps for Work (i.e. I pay for Gmail) and as part of my configuration I can tell Gmail which mail servers are trustworthy.  
If Joe did this, he would add his mail server for customdomain.com to the trusted list. Now, when Gmail checks where an email is coming from it will see that customdomain.com is a trusted server, so will look further up the history to the previous mail server. In this case it'll be bigcorp.com, which is valid, and the mail will be allowed through.  
Unfortunately I'm not sure this is available on the freebie Gmail server, nor whether other services support it.  
The hosting company didn't give their reasons for limiting the feature, but this seems like a pretty likely (and logical) reason.  
Sidenote: there's also a bit on Wikipedia about [rewriting the envelope sender](http://en.wikipedia.org/wiki/Sender_Rewriting_Scheme). Looks a little hacky, but might be a viable alternative for those without whitelisting.
