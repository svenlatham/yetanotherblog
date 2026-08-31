---
layout: post
title: "MariaDB Indexes on DATETIME and DATE functions"
date: 2016-09-07 07:54:15 +0000
permalink: /2016/09/07/mariadb-indexes-on-datetime-and-date-functions/
author: "sven"
categories: ["Uncategorized"]
---

Quick note in haste, but important for me to remember.
`` SELECT * FROM table WHERE DATE(`period`)='2016-09-05' ``
is orders of magnitude slower than
`` SELECT * FROM table WHERE `period`>='2016-09-05 00:00:00' AND `period`<'2016-09-06 00:00:00' ``
where `period` is an indexed DATETIME field. The former uses an assortment of WHERE and INDEX clauses; the latter relies on the INDEX and uses a RANGE search, which is much faster.
