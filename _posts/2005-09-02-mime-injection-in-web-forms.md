---
layout: post
title: "MIME Injection in web forms"
date: 2005-09-02 10:50:03 +0000
permalink: /2005/09/02/mime-injection-in-web-forms/
author: "sven"
categories: ["Uncategorized"]
---

I'm now getting daily (or more frequent) attacks on various web forms I have around the Internet. The characteristics are always the same: an automated bot seeks out a form that looks vaguely like a contact form. It then tries to iterate through each field, injecting a newline character and some MIME headers. An AOL address is BCC'ed, so the attacker can see which exploits were successful.

Presumably, once the attacker hits a vulnerable form, the spam begins. Fortunately this has yet to happen here, but it's undoubtedly going on all over the place.

Rather interestingly, MIME headers are put in - this could have the action (if done the right way) of hiding the original webform from the spam recipient, getting straight to the spammer's message instead.

To date, I've had attacks with BCCs going back to jrubin3546@aol.com, bergkoch8@aol.com and mhkoch321@aol.com

To protect yourself against these attacks, make sure that any web forms you use remove newlines from user input - particularly those that might reappear in headers. In PHP, for example use something like $usermail=str\_replace("\n","",$usermail); (and similarly for \r).

Elsewhere on the Internet, this recent 'wave' has been discussed, and a quick Google finds a few articles of interest:

* [Article about email injection](http://securephp.damonkohler.com/index.php/Email_Injection)
* [Blog with plenty of comments from affected webmasters](http://www.anders.com/cms/75/Crack.Attempt/Spam.Relay)
