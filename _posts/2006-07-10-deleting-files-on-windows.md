---
layout: post
title: "Deleting Files on Windows"
date: 2006-07-10 10:28:14 +0000
permalink: /2006/07/10/deleting-files-on-windows/
author: "sven"
categories: ["Uncategorized"]
---

Over the past few days I've been writing a program to create static HTML pages from Wikipedia XML dumps (long story - actual program and more info to come in a few more days...)

The program creates a **lot** of subdirectories in the process, and a lot of these happen to be in Unicode.

99.9% of the time this is fine. Windows is happy. I'm happy. Everybody's happy. The 0.1% has been a particular folder 'Cuisine of Israel' which, for the past day, I've been unable to delete. I  get the following message:

Cannot delete Cuisine of Israel : Cannot find the specified file.  
  
Make sure you specify the correct path and file  name.

It took some searching on Google, and [this Groups page](http://groups.google.com/group/microsoft.public.windowsxp.general/browse_frm/thread/86f80e307e6725ab/4e515406e67a2b4e?lnk=st&q=Cannot+delete++Cannot+find+the+specified+file.&rnum=4&hl=en#4e515406e67a2b4e) for me to find the answer:

1. Open a command line (Start > Run > Type **cmd** and press Enter)  
2. Navigate to the folder above the one you want to delete  
3. Type **dir /x** to see the MS-DOS 8.3 filenames. In my case it was CUISIN~1  
4. Type (eg. for me:) **rmdir /s CUISIN~1** and confirm the delete.  
5. The folder should now be removed.

It should be a similar process for files (except, using **del** instead of **rmdir**).

Apparently Windows has a problem with certain characters. In this case I think there was a Unicode space character of some kind in the file. Windows wasn't capable of dealing with it, and gave the error message.

*Make sure you're deleting the right directory. This solution provided without warranty - please back up your files, etc. etc. Use at your own risk.*

technorati tags:[windows](http://technorati.com/tag/windows), [xp](http://technorati.com/tag/xp), [files](http://technorati.com/tag/files), [bug](http://technorati.com/tag/bug)
