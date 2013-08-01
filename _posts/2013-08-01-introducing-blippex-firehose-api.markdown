---
layout: post
title:  "Introducing the Blippex Firehose API, a world first!"
date:   2013-08-01 16:00:00
categories: updates
---

Lat week, when we released the [first database dump of Blippex](http://blippex.github.io/updates/2013/07/23/First-database-dump.html), [mgamache on Hackernews](https://news.ycombinator.com/item?id=6090659) said it will be cool to have some kind of firehose API like Twitter has, a nearly realtime feed of the URLs indexed by Blippex.

**We thought that is a very cool idea and present today the Blippex Firehose API!**

The Blippex Firehose API is streaming the URL and the title of every page that is getting indexed by Blippex in near realtime. We have decided to use [SockJS](https://github.com/sockjs/sockjs-client) for streaming the data because it is right now the most used websocket library with clients for a lot of languages, direct websocket access and working fallbacks if you are, for example, behind a proxy-server.

**Accessing the Blippex Firehose API**

This is the code you need to access the Blippex Firehose API using Javascript:

{% highlight javascript %}
<script src="http://cdn.sockjs.org/sockjs-0.3.min.js"></script>
<script>
//Open a SockJS connection to the Blippex firehose
var sock = new SockJS('https://firehose.blippex.org');
   //listen to the connection for messages
   sock.onmessage = function(e) {
   //Data is JSON-object, so parse it
   var data=JSON.parse(e.data);
   //write to DIV element
	document.getElementById('fh').innerHTML=data.title;
	document.getElementById("fh").href=data.url; 
   };
</script>
<a id="fh" href="#" target="_blank">If you don't see links here please update your browser</a>

{% endhighlight %}

As you can see no registration is involved and again, the firehose does not use any cookies and we don't store any IPs.
The result of this script is shown here:

{% raw %}
<script>
//Open a SockJS connection to the Blibbex firehose
var sock = new SockJS('https://firehose.blippex.org');
   //listen to the connection for messages
   sock.onmessage = function(e) {
   //Data is JSON-object, so parse it
   var data=JSON.parse(e.data);
   //write to DIV element
	document.getElementById('firehose').innerHTML=data.title;
	document.getElementById("firehose").href=data.url; 
   };
</script>

<span style="width:100%; float:left;height:60px;background-color:#eeeeee; padding:10px;">
<a id="firehose" href="#" target="_blank">If you don't see links here please update your browser</a>
</span>
{% endraw %}


**We have a nicer, quite addictive demo accessable [here](https://www.blippex.org/firehose) for you!**

**Dataformat**

After opening a SockJS connection to https://firehose.blippex.org the API sends JSON objects like this to the client:

{% highlight json %}
{"url":"http://wbbc.co.uk","title":"BBC - Homepage"}
{% endhighlight %}


We can't wait to see what developers will do with this! 
And if you have any ideas for improvements please let us know!

**Future**

This is of course just a start, we want to implement filters so that you can get only the pages that have a specified keyword in it. Think of it like the Twitter firehose API but for web-pages that were seen by real people!

And finally: To help improve Blippex, please tell your friends! The more people who are a part of the community, the better it will get for everyone!

**Thank you &amp; keep on searching & discussing!**
