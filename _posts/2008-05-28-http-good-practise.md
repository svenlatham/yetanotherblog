---
layout: post
title: "HTTP Good Practise"
date: 2008-05-28 14:45:12 +0000
permalink: /2008/05/28/http-good-practise/
author: "sven"
categories: ["Uncategorized"]
tags: ["web", "post", "html", "http", "verbs", "get"]
---

Here's one for the web perfectionists out there. The usual line with HTTP and web browsing is that requests are achieved through the GET verb, and data modifications are through POST.  
All well and good, but how do you handle text links that trigger a data modification? For instance, a page might have a list of items in a table, with "Edit - Delete" as associated actions. Edit is simple, it might go to edit?id=..., but Delete is more tricky. Assuming that no interstital "Are you sure" page is necessary, how can you trigger a POST from that Delete link?  
My current way of tackling this is to include a form at the base of the page, and use some Javascript to submit that form. For instance

```
<a href="javascript:deleteItem(123)">Delete</a>
```

```
<form action="" method="post" name="jsPost">
<input type="hidden" name="action" value="">
<input type="hidden" name="item" value="">
</form>
```

```
<script type="text/javascript">
function deleteItem(id) {
document.forms['jsPost'].action.value="delete";
document.forms['jsPost'].item.value=id;
document.forms['jsPost'].submit();
}
</script>
```

This works fine and while the HTTP behaviour is roughly correct (okay, so in a perfect world I'd use the DELETE verb....) the code does not work for people not using Javascript.  
Any ideas for a better, but clean solution?
