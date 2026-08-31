---
layout: post
title: "Dev switching for Nginx Reverse Proxy with cookies"
date: 2020-09-03 14:09:48 +0000
permalink: /2020/09/03/dev-switching-for-nginx-reverse-proxy-with-cookies/
author: "sven"
categories: ["Uncategorized"]
---

I'm a fan of using Nginx as a reverse proxy, and I've now used it for multiple projects.



Essentially Nginx sits in front of multiple other web servers (Apache or other Nginx instances) and redirects traffic according to a series of simple rules.



There are numerous benefits, but one particular use case is proving very useful. This is the ability to switch between a production and dev website using cookies.



Here's a broad example (note other proxy/server config instructions are omitted)...



```
server {
location / {
# By default, serve from the production server(s):
        proxy_pass https://production;
# If the special cookie appears in the request, redirect to the dev server:
        if ($http_cookie ~* "usedev31246") {
            proxy_pass https://development;
        }
}
# Special convenience URLs to enable/disable the cookies we need:
location /enable-dev {
    add_header Set-Cookie "usedev31246;Path=/;Max-Age=9999999";
    return 302 /;
}
location /disable-dev {
    add_header Set-Cookie "usedev31246;Path=/;Max-Age=0";
    return 302 /;
}
}
```



By default, a proxy connection will be made to the **production** server for all requests unless a cookie is provided in the request matching the string *usedev31246*, in which case it'll be sent via the **development** server.



For convenience, any user can set the cookie by visiting /enable-dev (which will redirect back to the home page). They can clear it by visiting /disable-dev.



This means you can quickly help somebody get to the dev site by directing them to https://example.org/enable-dev



Of course, you probably don't want anybody finding this so best to password protect and use a suitably secure cookie string, but I leave that as a challenge to the reader ;-)



This is quite nice for things like WordPress instances which tend to put the full URL in image and resource requests. By doing this, we don't need to rewrite those URLs and worry about permalinks changing.



If you're also using Nginx as a cache, beware as a user on the dev site might pollute/poison the cache with development code. Ensure the cache is disabled before dev requests are fulfilled (this is good practice anyway for a dev website).
