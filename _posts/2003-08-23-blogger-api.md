---
layout: post
title: "Blogger API"
date: 2003-08-23 19:35:08 +0000
permalink: /2003/08/23/blogger-api/
author: "sven"
categories: ["Uncategorized"]
---

I spent quite a bit of today getting our [blog editor](http://www.theuniversityoftheinternet.com/weblog-centre) to support Blogger API. Once done it should let users post using a variety of tools (I, for one, am looking forward to blogging from my mobile :-) -- tools I've used/tried today:

[BlogBuddy](http://blogbuddy.sourceforge.net/) - nice and small. Very sensitive to API errors, so not a good program to test with. No WYSIWYG -- it's just pure HTML, which is a shame and it's been undeveloped for over a year, which is a great shame.

[w.bloggar](http://wbloggar.com/) - very powerful but the interface is quite confusing at first. It's counter to what I want (a simple interface).

[Mozblog](http://mozblog.mozdev.org/) - I use Mozilla all the time so this would've been ideal. Unfortunately it's incredibly buggy to the point that it's unuseable. Shame - I like the idea of this and look forward to future versions!

[PowerBlog](http://www.powerblog.net/) - this is nice and tidy. Simple to use, but introduces 'plops' which seem to refer to places you can blog - absolutely awful word if you ask me... has a brilliant debug feature, so I'm using it currently to debug the server.

Here are the [Blogger API](http://www.blogger.com/developers/api/1_docs/) implementations. Green means I've implemented it. Red means it needs to be done. Gray means that it's not going to be implemented:

**blogger.getRecentPosts  
blogger.getUsersBlogs  
blogger.newPost  
blogger.editPost  
blogger.deletePost  
blogger.getUserInfo  
blogger.getTemplate  
blogger.setTemplate**

If I get a chance I'll also implement the [metaWeblog and MT](http://www.movabletype.org/docs/mtmanual_programmatic.html) extensions. I'm also looking forward to implementing the [Echo API](http://bitworking.org/rfc/draft-gregorio-07.html) when it's finally done.
