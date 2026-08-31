---
layout: post
title: "Bayesian Language Detection"
date: 2006-01-21 20:19:38 +0000
permalink: /2006/01/21/bayesian-language-detection/
author: "sven"
categories: ["Blogwise"]
---

Excellent - I managed to write a Bayesian filter today from scratch (well, something that vaguely resembled and works like one). The application is a fairly common one - you pass it a slab of text and it detects which language the content is written in.
This is going to be used in the background of Blogwise, for blogs where I can't autodetect the language from metadata, and will silently run on new blog submissions.
The application is relatively straightforward. I feed it a load of text content known to be in a specific language. It ranks the word by frequency, and links it to the language. When it's done it has a frequency chart for each language. So, for example, the top words in English are *the, of, and*; the top in French are *de, la, le*; in Spanish it's *de, la, que*; and so on.
You'll notice that Spanish and French share the same top words - it's an art to get the checking algorithm tweaked to produce accurate results. The algorithm takes into consideration many words, and particularly looks for words that exist or are popular in one language but are rare in another.
The sample data is rather thin, but already I'm seeing promising results. Of the six languages tested (French, Spanish, German, Italian and English (UK & US)), I provided five samples. I then tested them with two further samples.
The results were very promising (even with such a small test group) - not only was the system correct on all but one case, it was making enough of a distinction between languages for the confidence to be very high indeed.
The only error was an incorrect assessment of a UK English blog as US English, but there's hardly a massive difference. US English was a close second place in its assessment, and I'm probably going to drop regional differences anyway (UK or US can be confirmed from the country - and does the reader really *care*?)
So this is good news, and all in the name of progress for Blogwise! Not bad for a few hours' work.
