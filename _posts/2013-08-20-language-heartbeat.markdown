---
layout: post
title:  "Language Detection and the Blippex Heartbeat"
date:   2013-08-20 16:00:00
categories: updates
---

Today we are introducing two new and very exiting features for Blippex, language detection and the Blippex Heartbeat!
<!-- more -->

###Language detection

We got a lot of feedback that Blippex is showing results in languages that are irrelevant for the person who is searching, so we worked hard on it and since last week Blippex detects the language of a crawled page using the great [CLD](https://github.com/dachev/cld) module for Node. 

And when you search, Blippex rank the results in the languages your browser want to have (via the ["Accept-Language"-header](http://en.wikipedia.org/wiki/Content_negotiation)) higher than results in other languages, this should give you a better search experience. This does not mean that you won't get results in other languages, but less often (we are still fine tuning the scoring).

Of course, via the search API you can request different languages and the results are containing the language-field, see the [documentation](https://archify.atlassian.net/wiki/pages/viewpage.action?pageId=18939913). Please tell us what you think about this new feature!


###Blippex Heartbeat

After releasing the [Blippex Firehose](/updates/2013/08/01/introducing-blippex-firehose-api.html) people said "Really cool, but what can i do with it?". Good question!
So today we launch the [Blippex Heartbeat](https://www.blippex.org/heartbeat)


[![Blippex Heartbeat](/css/img/posts/heartbeat.png)](https://www.blippex.org/heartbeat)

The Blippex Heartbeat shows you in real time statistics about what URLs are getting indexed, what are the top domains, what are the top languages, what are the top [Top Level Domains (TLD)](http://en.wikipedia.org/wiki/Top-level_domain) and if people are searching on Blippex. 

You can find the Blippex Heartbeat here: [https://www.blippex.org/heartbeat](https://www.blippex.org/heartbeat), works best in fullscreen mode (press F11 in Chrome)! If you think something is missing or you have a idea how we can improve the Blippex Heartbeat please tell us!

The Blippex Heartbeat is important for us because it shows us that Blippex is alive. And Boy, it is really alive! Last week was once again the best week ever! Thank you!
