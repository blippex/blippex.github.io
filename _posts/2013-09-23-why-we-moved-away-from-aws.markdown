---
layout: post
title:  "Why we moved away from AWS"
date:   2013-09-23 16:00:00
categories: updates
---

Since years we have used [Amazon Web Service](http://aws.amazon.com/) for our hosting. It is a great idea and works wonderful for a startup. But since a few days [Blippex](https://www.blippex.org) is running on our own servers at [OVH](http://www.ovh.com/), here is why:
<!-- more -->
###Costs
AWS is great for a startup, you think you need to put the cache-server on a extra machine? Test it with a few mouse clicks! Need storage? great, use S3 for unlimited storage!

And at the first glance it looks quite cheap. A Web Server for $40 something? Nice! And you can backup it very easy with a mouse click while running, great!

But after some time you realize that you have to pay for everything extra: traffic, bigger disks, etc. And the basic servers are not really fast for databases because Amazon wants you to use their databases! Which is completely ok and their databases are great too, but for a small startup this gets quite fast quite expensive (for example, when you have a lot of updates per day).

Just to give you an example: For running Blippex on AWS we needed machines with at least 16 GB of memory for the databases (Mongo & Elasticsearch), so we used M1 extra large, the cheapest server with that amount of memory. This machine costs you around $340-$380 per month (depending if in the US or for example in Europe). 
Now you can say: use reserved instances! Ok, for a one year contract this machine would then cost around $284/month and three years is way too long for a startup where even one year can be too long.  
We need two of this, so make it around $700/month just for the two database servers. Then you need of course for example EBS volumes to store and to backup the stuff (sending 40+ GB every day to S3 takes quite long and is not that cheap either). Then of course Web Server, crawler, etc. so we payed around $1000/month for running Blippex on AWS. 

Now we moved Blippex to OVH (there are a lot of other providers for nearly the same price out there, for example [Hetzner](http://www.hetzner.de/en/)). We could scale it down to three servers (why? see next point) and pay for them 170 Euros (around $226) per month with unlimited traffic and backup space, thats 4,4 times less! For the saved money you get a office in Berlin :) And adding machines makes it even cheaper.

###Speed
Now you think: ok, but AWS gives you good speed for the money. Well, the new servers have 32GB of memory, 2TB of (RAID 0) storage or 240 GB of SSD storage! We did some not scientific speedtest (we tested importing the Mongo DB and searching in Blippex, the stuff that is important for us) and this machines are at least 4-5 times faster than the AWS machines. And you don’t have the AWS problem with EBS volumes having different speeds so you must build a raid to get an predictable performance).

So this allowed us to reduce the servers we need from 10+ machines to three by combining services on one machine (they are fast enough and have enough memory, for comparison: a standard, basic AWS machine has 1.6 GB of memory, this one has 32 GB). which comes of course with some more maintenance problems but on the other hand it is now faster than before because the connections between the services are faster.

###Privacy
This is a point that is not important for everyone but in a post Snowden world it is maybe a small advantage to have your service running at a place that is not (or not yet) owned by a US company and that the european data rights are in place. Not a decision maker but could be important in the future.

###Conclusion
AWS is really great and i can tell everyone use it when you start! But when you know what you are doing think about alternatives. This could be moving it to other cloud providers like [Rackspace](http://www.rackspace.com), [Linode](https://www.linode.com/) or [Digital Ocean](https://www.digitalocean.com/) or move it to your own server as we did.
Of course, there are also downsides when moving it to your server, more system administration, you have to build your own firewall, take care of security & backup, etc. But quite often, once you have set this up, you get better performance for a lower price.   
The biggest downside is not to be able to start new servers just with a mouse click :) With providers like ours you wait up to three weeks until you have your ordered machine, so plan ahead!

This does not mean that we will never ever move back to AWS, but right now this is the best fit for us. Maybe when we need world wide co-locations to make the search that 50 or whatever ms faster we will think about it again, but until then we are happy with the setup right now!

What is your experience with moving to AWS or away from AWS?

