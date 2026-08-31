---
layout: post
title: "Templating in HTML"
date: 2013-01-20 14:07:39 +0000
permalink: /2013/01/20/templating-in-html/
author: "sven"
categories: ["Uncategorized"]
---

Ongoing thoughts...
A fairly common scenario, particularly with dynamic page rendering, is the need for templates. Specifically, when loading data asynchronously we might want to define a template for each element in that data set.
For example, say I have three rows of data coming from JSON:

```
[{ 'name': 'John Doe', 'birthyear': 1981 }, { 'name': 'Jane Smith', 'birthyear': 1985 }, { 'name': 'Alice Bobbington', 'birthyear': 1987 }]
```

For interest, let's say that both fields will be editable in the table from the outset. We're aiming to produce something like this:

```
<table>
<thead>
<tr><th>Name</th><th>Birth Year</th></tr>
</thead>
<tbody>
<tr><td><input type="text" name="name_1" value="John Doe"></td><td><input type="text" name="birthyear_1" value="1981"></td></tr>
<tr><td><input type="text" name="name_2" value="Jane Smith"></td><td><input type="text" name="birthyear_2" value="1985"></td></tr>
<tr><td><input type="text" name="name_3" value="Alice Bobbington"></td><td><input type="text" name="birthyear_3" value="1987"></td></tr>
</tbody>
</table>
```

*Please assume validation, correct HTML5 input tags and proper IDs & row references would be settled for the real thing ... :-)*
There are several options to populate this in a HTML table.

1. Start with a blank table body. Use DOM manipulation to add rows and columns in Javascript.
2. Create a dummy row, hide it with CSS. Clone the row node in the table and populate each clone with each successive row of data.
3. Create the HTML for each row in the Javascript (as a string) and use that to set the innerHTML of the table.
4. Use something like [JsRender](https://github.com/BorisMoore/jsrender), where the source template is [defined in a script tag](http://weblogs.asp.net/stevewellens/archive/2011/12/01/goodby-jquery-templates-hello-jsrender.aspx) and we duplicate the template for each row.

There are pros and cons to each.
If we want to take the pure Javascript approach, (1) is the likely best option. No string manipulation, no messy fragments of HTML, but it's verbose. Start taking this approach in a data-heavy page and you might want to rethink it.
If you're using a decent editor with good syntax highlighting and completion tools, option (2) might be better. By revealing the rows through CSS, you can also preview how the row will look once complete (since it exists in the table). However, this places an extra row in the table which means you have to be careful when manipulating the table that you don't include the template row (or, that youÂ *do* where necessary).
Option (3) seems to be a fairly popular choice, but it leaves me with the awful aftertaste of string escaping and evals (to clarify - I treat innerHTML with the same caution I do with eval ... i.e. only ever use them if I've exhausted all other options).
Option (4) looks promising, although I am uncomfortable with the idea of HTML markup inside a script tag ... it's (AFAIK) legitimate, but most parsers and editors won't acknowledge this, and has the same bitter eval taste as Option 3.
Right now I favour the approach of (2), whereby a hidden row is defined in the source HTML, and is duplicated & modified according to each received row. The issues described above could be reduced by placing the template in its own TBODY.
