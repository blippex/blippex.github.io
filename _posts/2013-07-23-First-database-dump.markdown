---
layout: post
title:  "First database dump"
date:   2013-07-23 14:13:14
categories: updates
tags: dump database
---

It has been an amazing last week for Blippex. Last friday we reached the milestone of 50k searches per day. Today we are releasing as promised the first dump of our database. We decided to release the database as a BSON dump of our MongoDB database on [github](https://github.com/blippex/blippex_search_database_dump)—you can also [download it](https://dump.blippex.org/blippex_18_07_2013.tar.gz).
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

Compared to our "real" database there is one thing missing. Due to copyright issues we do not publish the text of a webpage, because we are not eager to spend our money on lawyers instead of developing Blippex. We are really curious about what else is possible with the data, we would be happy to see competing applications as well as additions or something completly different.