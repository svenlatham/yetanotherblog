---
layout: post
title: "The Perfect Website Doesn't Exist"
date: 2023-11-11 20:59:57 +0000
permalink: /2023/11/11/the-perfect-website-doesnt-exist/
author: "sven"
---

This blog has been going for about 20 years. Various iterations of WordPress, a custom CMS, back to WordPress again.



It's not my first blog. That was running all the way back in the 90s, before blogs were really a *thin*g. I've lost most of it but I remember it was based on hand-editing HTML files in Vim. Posts were still dated, sorted by latest and contained various updates. Just seemed like a natural way to track updates at the time.



I've probably been responsible for the creation of upwards of a hundred websites so far. From personal projects, commercial ones, customer sites, intranets and hobbies. Many of the commercial ones still exist, although my work has largely been overwritten.



I have also created websites that create other websites. Building content management systems and blog engines. If I count those, there's probably a few more hundred. Sadly all of those disappeared, along with the companies that I worked for that hosted them.



Along the way I've tried to adhere to principles based on well-established concepts. Good stable URLs, minimal overhead, decent semantics. It's helped me steer clear of some of the fads over time, like single-page content sites.



Many of those principles have come from managing the back-end. I've created websites attracting millions of users, sometimes in a very short time. This firmly focuses the mind on responsiveness: avoid dynamic pages, minimise bytes, cache smart.



More recently, static website generators have caught my mind. These aren't new. I build a couple of iterations back in the 90s - desktop apps that produced static HTML with a template. Nowadays this works well with source control and CI/CD, so a site can be edited in GitHub, prepared by Actions and deployed to a server.



Static websites are pretty much the fastest kind. No real processing on the client or the server, lots of cache opportunities, robust. For a blog - particularly one like this that isn't that fussed on user comments - they're almost a no-brainer. Why re-render the page for every user when they each receive the same content? There's quite a number of static site generators, and I've been using Jekyll for a while.



All good in principle, but it's not enough. It misses some of the interesting - and oft-forgotten - aspects of the web.



What about redirects? This is a server configuration challenge - Apache lets you use .htaccess files but that might be inefficient. Nginx needs to be configured. Others have in-between implementations.



What about content negotiation? I'm quite interested in this, because the transfer of knowledge shouldn't assume HTML. Want this in JSON? Fine. After text? Why not. PNG image? Well, that's a bit strange but yeah let's give it a go.



Language negotiation? Sure, why not. Apache kind-of supports this (as well as content) and you end up with various versions of the same file, so intro.en.html and intro.fr.json - the server handles the selection, so this kind of feels like a good outcome even if our generation gets a little more complex.



As the World Wide Web is well into its thirties as I write, some aspects keep coming round. Maybe that suggests they have a relevance that we shouldn't let go of; that original intentions and designs were good or - at least - grounded in reasonable premises.



Keen to explore, as always, so watch this space...
