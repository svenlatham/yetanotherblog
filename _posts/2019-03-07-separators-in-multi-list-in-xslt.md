---
layout: post
title: "Separators in multi-list in XSLT"
date: 2019-03-07 16:39:47 +0000
permalink: /2019/03/07/separators-in-multi-list-in-xslt/
author: "sven"
categories: ["Uncategorized"]
---

Quick note: if inside an XSLT for-each loop and I need a separator, the following should be fine:

```
<xsl:if test="position() != 1">; </xsl:if> {...content...}
```

This will add the separator as a prefix before all but the first element.
