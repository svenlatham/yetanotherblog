---
layout: post
title: "Deviation"
date: 2013-07-09 21:32:00 +0000
permalink: /2013/07/09/deviation/
author: "sven"
categories: ["Uncategorized"]
---

As I become older (!), wiser (?) and generally less interested in fiddling about with the innards of software, I've become acutely aware of aspects of software development which are more often than not the cause of issue.  
Software design is intrinsically an ass-covering occupation. With most budgets and with even the most skilled developers, bugs will be created. Our role is to minimise the frequency and impact of bugs; to work on a basis of zero bugs is (with current development environments) a largely futile exercise.  
Computer programming is largely about a series of transitional actions. Functions take an input and produce an output. Cause and effect. This is why unit tests feature in so many programmers' armouries - they offer a systematic, highly repeatable way of testing that a given function works as expected.  
The complexity of functions can be guessed from the number of external inputs they take. The ease of testing is reduced every time the number of inputs increases. This becomes far more complicated when global scope or environment variables come into play - something often overlooked when testing.  
So, when building up functions my first soon is to remove as many variable inputs as possible. I treat globals as positively evil, and avoid them unless necessary. Functions with many inputs are also treated with caution. What is a function doing with so many variable inputs? It usually suggests a chain of conditional statements - perhaps the function needs to be split.  
Optimisation is another poisonous part of programming. Generally if a cache or other optimisation mechanism is implemented it adds an aspect of unpredictability to the application - another input (or factor) we need to consider when writing and testing. Most developers will implement some form of optimisation without giving it a second thought - a global database connection for instance persists state between functions, which gives an unexpected input for testing purposes.  
I accept that optimisations in most cases are both necessary and quite tolerable, provided the developer is aware of them and takes necessary caution around them.  
I start with a perfect system - the kind we might hear about in compute science theory. All functions perform one action only, in isolation. There are no globals. Everything is real-time (no offline mode or synchronisation). Then I begin to unravel the optimisations applied. Caching. Globals. Offline mode. Each of these is treated as an unwelcome guest; an unfortunate consequence of our imperfect environments. They are necessary - we live in the real world - but every single one is a potential source of headaches.  
This might all sounds like a pursuit of the unachievable dream. I did after all start by saying that zero bug policies are futile, but I do believe we can make as much effort as is reasonably possible to head in that direction, and my personal goal is to avoid as many optimisations as absolutely possible.
