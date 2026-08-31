---
layout: post
title: "Apache and PHP"
date: 2004-06-04 16:12:33 +0000
permalink: /2004/06/04/apache-and-php/
author: "sven"
categories: ["Uncategorized"]
---

Ooh this is a tricky one. My self-made templating system which is otherwise coming along quite nicely has hit a slight problem. The system works by running all .html files through a PHP script (via the AddType and Handler config instructions).  One of the principles of the templating system is that it integrates quite well with the host server, thus templates are set by .htaccess files in Apache. It normally works great.  
  
When you set all .html files to use a particular handler, Apache doesn't check that the file exists before it invokes the handler script. If that file doesn't exist, the handler needs to return an error code to the server, and Apache will then kick off its ErrorDocument for a 404. The snag is, I can't figure out how to get a PHP module to return an error code to the host server. The best I can do at the moment is echo back a custom 404 page from within PHP, which is not very portable at all - it should be using the document defined in the .htaccess or Apache config.  
  
I'm fairly sure something like this is what I want:  
if (!$mydoc=@file($reqfile)) {  
    exit(404);  
} else { ....  
  
But exit(404) doesn't seem to work. The Apache API docs suggested that I should be returning a HTTP status code as the error, and I can't find any other information about it. Does anybody know what to do in this case?
