---
layout: post
title: "MySQL Versioning"
date: 2004-02-03 17:39:20 +0000
permalink: /2004/02/03/mysql-versioning/
author: "sven"
categories: ["Uncategorized"]
---

While considering how I'm going to manage the new version of [Blogwise](http://www.blogwise.com/), I decided it would be a good idea to keep revisions of details recorded, since automated processes will be updating blogs' details fairly regularly and I want to note changes and be able to revert.

I use [MySQL](http://www.mysql.com/) and I can't find a good existing solution. [This article](http://www.ciselant.de/projects/pg_ci_diff/doc.html) suggests an ideal way one might go about it, and I was planning to adopt a similar idea anyway (storing diffs in some kind of history table) so seeing this has given me more confidence to try it!
