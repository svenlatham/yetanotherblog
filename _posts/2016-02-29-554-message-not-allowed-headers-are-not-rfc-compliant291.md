---
layout: post
title: "554 Message not allowed - Headers are not RFC compliant[291]"
date: 2016-02-29 10:53:53 +0000
permalink: /2016/02/29/554-message-not-allowed-headers-are-not-rfc-compliant291/
author: "sven"
categories: ["linux"]
---

If you get this message when sending emails to Yahoo addresses from PHP, it's quite possible the subject line is being duplicated and this is causing your email to be rejected.
PHP's mail() function takes a Subject as a parameter. It also accepts a custom list of headers.Â The mail() function seems to always append a subject header irrespective of the contents of the custom list.
So, if you have the Subject already defined in your custom headers, PHP will add another. This is not RFC compliant, andÂ Yahoo has a particularly strict checker for incoming emails (most other mail servers seem to ignore this, as far as I can see).
Take the Subject line out of your custom headers, make sure it's in the mail() call itself, and the mail should send (assuming no other issues....)
