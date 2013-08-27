---
layout: post
title:  "Second database dump"
date:   2013-08-27 16:00:00
categories: updates
---

Today we are releasing the second database dump of the Blippex database!   
This second dump is more than twice as big as the [first one](/updates/2013/07/23/First-database-dump.html), containing more than 4 millions URLs.

The format is the same, it is a BSON dump of our MongoDB database, you can find it on [github](https://github.com/blippex/blippex_search_database_dump) or [download it here direct](https://s3-eu-west-1.amazonaws.com/export.blippex.org/blippex_26_08_2013.tar.gz) (577MB, extracted over 1GB).
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