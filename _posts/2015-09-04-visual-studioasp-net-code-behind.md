---
layout: post
title: "Visual Studio/ASP.NET Code Behind"
date: 2015-09-04 11:32:01 +0000
permalink: /2015/09/04/visual-studioasp-net-code-behind/
author: "sven"
categories: ["Uncategorized"]
tags: ["development", "visual studio", "c#", "codebehind"]
---

I'm going to need to remember this, as it runs slightly counter-intuitive to what I was expecting (although makes sense).
Code compiled in App\_Code is available globally, so any other piece of code can reference it.
Code compiled in code-behind (i.e. the .cs files 'behind' ASPX pages) is only available to its corresponding ASPX pageÂ *unless* you explicitly reference it.
This can be done by adding the following to the ASPX page:

```
<%@ Reference Page="......link to .aspx" %>
```

One to remember.
