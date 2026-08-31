---
layout: post
title: "Quick Thinking"
date: 2007-09-19 14:01:58 +0000
permalink: /2007/09/19/quick-thinking/
author: "sven"
categories: ["sysadmin", "hacking", "spam"]
---

I'm currently managing a friend's WordPress blog while they bugger off on a round-the-world trip. Goodness me they get a lot of spam.  
Within a minute or so of turning off Spam Karma (it causes problems with the comment count, apparently) I/he had 15 new comments, all spam. So, without FTP access I quickly put in a hack to the comments page thusly:

```
<textarea name="quack" id="comments"></textarea>

<script type="text/javascript">

document.getElementById('comments').name = 'comments';
</script>
```

Nice and simple - a bit of Javascript that renames the comments field so it can be submitted correctly (if you fail to run the script, the comment fails). I ***know*** there are accessibility issues and all the smartarses who turn off their Javascript are stopped from commenting, but desperate times call for desperate measures. It's quick & dirty, and for most people (this guy doesn't get a massive amount of traffic) it works OK.  
Anyway, I went to bed last night feeling smug that I'd robbed a load of spammers of their precious links. This morning I took a look: 38 new comments. They've already made their way around it.  
This suggests one of three things:

1. The spammers caught the error and changed their behaviour to suit. *Doubt it, it'd be easier for them to move onto other blogs.*  
2. They execute Javascript (maybe it's a full-on Firefox session with a plugin script?. *Likely, and rather smart!*  
3. My code is rubbish and never worked in the first place. *Never impossible.*

Anyway, kudos to those guys for not being thwarted by a simple script! Now, let's see what happens when I get Spam Karma re-enabled or I activate Akismet...  
**Update 22 Sept:** Ignore the above. My code *is* rubbish. If the spammers do a simple POST to the server they will succeed, since I'd never updated the server-side code to match the client. Best bet for this hack would've been to rename the field both on the form and in the server code to something unpredictable ('quack' is just fine...) and not bother with the Javascript, Spammers would ignorantly continue to assume the field is '*comments'* and their posts would fail. Thanks Brian and Neil T  
A while ago I wrote a blog host service which included a more sophisticated spam filter. It would scramble *all* the fields client-side, include a couple of hashes and would only accept the comment as-is if all the hashes matched the server's own records. It stopped blind POSTs and bots that did not use Javascript. It also cleverly spotted genuine users who might not have been able to run the Javascript (since there was a larger platform accessibility was a concern), and used timing information to identify real users (who take their time) versus bots (who tend to write/post immediately or in a regular pattern).  
It worked for nearly 2 years without a single automated spam comment getting through (many tens of thousands were stopped; no false positives either). Manual spam got in, but was minimal. Finally the spammers changed their ways and (I guess) began using full browser sessions to post their spam - once they do that you need to start looking at content analysis or other methods.
