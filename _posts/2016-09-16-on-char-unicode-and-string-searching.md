---
layout: post
title: "On CHAR, Unicode and String searching"
date: 2016-09-16 06:16:42 +0000
permalink: /2016/09/16/on-char-unicode-and-string-searching/
author: "sven"
categories: ["Uncategorized"]
---

As part of my wifi project, I need to store the hashed MAC address of devices so we can run analysis and gather daily figures. We use MariaDB, based on MySQL, for this particular application.Â There are various tables used for this, and all JOINed by the common hash.
When I first put the system togetherÂ in haste, I used VARCHAR(20) as it wasn't obvious at the time which route we'd go down, or how things would be processed.Â You can be a little more wasteful with VARCHAR as the storage space is n+1 (where n is number of chars), so the field shrinks to suit. Fixed strings using CHAR always pre-allocate a fixed space, so are less flexible.
Roll forward a year. Things have grown very fast, and we're starting to see performance limits being hit, and storage space becoming an issue, so it's time to review the schema.
 
Now we know the maximum bytes for any hash will always be four. They can be smaller than this (depends on application) but eight is theÂ limit.
So, CHAR(8) would seem a reasonable way to store eight bytes in hex.Â *If you're screaming about INT/BLOB/VARBINARYÂ storage, I'll come back to that in a moment...*
**Issue one - UNICODE**
First problem is that, if you use a multi-byte charset like utf-8, CHAR is potentially much worse than VARCHAR. As a fixed field, CHAR must allocate the maximum space for all supported Unicode characters, so [three bytes are reserved](http://dev.mysql.com/doc/refman/5.7/en/charset-unicode-utf8.html) for each character (MySQL utf8 doesn't support supplemental unicode characters, so three is the limit).
Compare to VARCHAR, where the field size is dynamic and therefore grows according to the characters in use. For anybody using straightforward Latin characters, this needn't be more than one byte per character.
In the case of utf8, VARCHAR canÂ be far more efficient than CHAR.
If you're only using basic characters or storing hex values in CHAR, explicitly set the latin1 character set on this field:
`` ALTER TABLE `mytable` MODIFY `col` CHAR(8) CHARSET latin1 ``
**Issue two - Comparing CHAR and VARCHAR**
As I was testing this I converted some tables hoping that the comparison would be fairly straightforward, but it seems there's a big performance hit when comparing a VARCHAR field to a CHAR field (possibly not helped by charset differences). I was seeing queries slow by a factor of 50+ in some cases.
`SELECT a.id, b.category from a inner join b on b.fk=a.id`
(fk is a varchar; id is a char - both contain the same string)
This is easily solved by explicitly setting a cast on the VARCHAR field, thus:
`SELECT a.id, b.category from a inner join b on CAST(b.fk AS CHAR(8) CHARSET latin1)=a.id`
Performance will be drastically improved. I believe this is due to the order and type of string comparison going on, and this addition explicitly converts all the potential strings up-front and avoids doing it on an ad-hoc basis.
**Next steps**
Performance is now much better, but this is still a fairly wasteful way of storing four bytes. The advantage is that, for debugging, it's easy enough to test queries and investigate issues without having toÂ deal with binary fields.
In terms of efficiency, the nextÂ step might be to switch to an UNSIGNED INT, whichÂ is allocated four bytes. This is readable in query output, and can be passed in the browser without too much fuss.
I suspect INT and BINARY also have further performance gains.Â I haven't tested the overhead, but I suspect the collation (the system of testing equivalence in characters)Â isÂ adding some workÂ to string comparisons - none of which we need here.
I need to test further before using UNSIGNED INT, and the update process is marginally more involved as the field needs to be converted and modified.
Right now, the performance is back at decent levels, so this is probably something to park for a while!
