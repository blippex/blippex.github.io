---
layout: post
title:  "Third database dump released!"
date:   2013-10-15 15:00:00
categories: updates
---

We got in the last two weeks very good press coverage (for example at [qz.com](http://qz.com/129879/this-is-the-first-interesting-search-engine-since-google/)) for Blippex and served up to 980k searches/day, averaging now at over 500k/day, thats 8 times more than two weeks ago!  
So we delayed the export of the dump a little bit to make sure everything is working fine.

But today we are finally releasing the third database dump of the Blippex database!   
This third dump is nearly twice as big as the [second one](/updates/2013/08/27/second-database-dump.html), containing more than 7 millions URLs.

The format is the same, it is a BSON dump of our MongoDB database, you can find it on [github](https://github.com/blippex/blippex_search_database_dump) or [download it here direct](https://dump.blippex.org/blippex_15_10_13.tar.gz) (935MB, extracted over 2.3GB).
<!-- more -->

The database format looks like this (dummy data):

{% highlight json %}
{
	"_id": "b919f02c8f053c41e8ee86311ca9b0f6,
	"url": "https://www.example.com/",
	"host": "www.example.com",
	"root": "example.com",
	"title": "Example Title"
	"time_spent": [
		{
			"sec": 45,
			"seen_at": ISODate("2013-06-23T00: 41: 44.0Z")
		},
		{
			"sec": 5,
			"seen_at": ISODate("2013-07-01T14: 41: 44.0Z")
		}
	]
}
{% endhighlight %}

Compared to our "real" database there is one thing missing. Due to copyright issues we do not publish the text of a web page, because we are not eager to spend our money on lawyers instead of developing Blippex.   
We are once again curious to see what people will do with it!

Don't forget to check out our [Blippex Hearbeat](https://www.blippex.org/heartbeat) to see what is going on at Blippex!