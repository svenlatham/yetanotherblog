---
layout: post
title: "Interesting Windows Problem"
date: 2006-08-06 23:09:31 +0000
permalink: /2006/08/06/interesting-windows-problem/
author: "sven"
categories: ["Uncategorized"]
---

Here's an interesting little problem I encountered the other day. Your keyboard starts behaving strangely - for example pressing the ' apostrophe key doesn't seem to work, but following it with a letter produces a strange foreign character. I was writing some code in a basic text editor, and it was driving me nuts when ['i'] was ending up as [í']

Turns out this is due to a special keyboard type in Windows called *International English*. There are five modifier keys ` ' " ~ ^ which modify the display of the following character.

Somehow this 'feature' kept activating itself (maybe a key combination?) You can remove it by switching your keyboard language to US/UK English (or your local equivalent).

I always find the Keyboard Language control tool in a slightly odd place in WIndows. It's not under *Control Panel > Keyboard* (Why on earth not?). It's under *Regional and Language Options*, in the *Languages* tab and press the *Details* button.

Once I'd found the cause of the irritation in Google, I ended up at <http://www.starr.net/is/type/kbh.html>

technorati tags:[windows](http://technorati.com/tag/windows), [language](http://technorati.com/tag/language), [keyboards](http://technorati.com/tag/keyboards), [problems](http://technorati.com/tag/problems)
