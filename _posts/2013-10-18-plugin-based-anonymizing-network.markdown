---
layout: post
title:  "Blippex now uses a plugin based peer to peer network to anonymize data!"
date:   2013-10-18 15:00:00
categories: updates
---

Today we are releasing the first version of a peer to peer based anonymizing network build in to the [Blippex Chrome extension](https://chrome.google.com/webstore/detail/blippex/fnmgddilgkocbbhcmjdbioapbjlnjlnp)!
<!-- more -->

###Why?
Using the [Blippex extension](https://www.blippex.org/extension) means that every URL you browse to is send to our servers. We always said that we don't record your [IP-address](http://en.wikipedia.org/wiki/IP_address) (and trust us, we are not doing it!). 
But some people said: "Hey, you are a startup, maybe you change your mind in the future, so how can i make sure i can trust you?"  
To trust us completely we have to develop something that makes it technically impossible for us to say which IP-address has seen that page we just indexed, and that is where this new peer to peer based anonymizing network steps in!

###How it works
It is not that easy to explain it, so here is our try:
When you use the Internet and browse to a web page, you are making a direct connection to the server where this web page is located, so this server is able to record your IP-address and could use this information for you or against you.

**With the new feature in the Blippex extension this works different!**  

Let's imagine you are in love with a person, but the person don't know it and you are too shy to go directly to the person (that would be the normal way, browsing to a web page). 
But you know that this person is every Friday at a very crowded bar. So you go there with a present for this person, but you are too shy to hand it over directly, so you ask some one in the bar to pass on this present to the person you are in love.  

Because the bar is so crowded this person then passes the present to the next person and so on. After a not predictable number of people that have passed the present to the next person it hopefully arrives at the destination. And now it is really impossible to track back who sent the package, because some people cannot remember anymore who gave them the present, some have left already, and so on.

That is how the system we have built now into the Chrome Blippex extension works!  

Every URL we receive is going through a not predictable number of peers until it comes to us. And because the data (URL & time spent) is encrypted in a way that only the Blippex servers can decrypt it, no one in this chain is able to decrypt it.

###How it works technically
The plugin gets a random, 32 character long id that is only valid for 10 minutes, from the Blippex servers and get 10 random ids from the latest 100 other plugins that got id's too. It then connects over [WebRTC](http://www.webrtc.org/) (using [peerjs](http://peerjs.com/), great piece of software!) to this ten other plugins.  

Now when you browse to a web page the plugin generates a random 256 bit key and encrypts the URL & time spent using [AES-256](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard). Then this key is encrypted with our 4096 bit public [RSA](http://en.wikipedia.org/wiki/RSA_(algorithm)) key. Now we have a dataset that can only be decrypt with the private RSA key from Blippex.  

Then the plugin generate a random number that is either 0 or 1. If it is 1 it sends the encrypted data directly to the Blippex API servers where the data is decrypted and the page is getting indexed. When the random number i 0 the plugin makes a random connection to one of the 10 peers it is connected to and sends the encrypted data to this peer. Only this two peers know now that the have exchanged data, no one else.  

Well, and when a plugin receives encrypted data form one of it connected peers it once again gets a random number that is either 0 or 1. When it is 1 it sends the data to the Blippex API servers, when it is 0 it forwards it again to one of the peers.

This means that none of the peers is able to say if the data it has received is a page seen by the previous peer and Blippex is never able to reproduce how many peers where in the chain until Blippex received the data, making it impossible for us to know which IP-address has seen this page!

**We think this is a major step to anonymize data and increase the privacy of the people using Blippex!**

Right now this only works in the Chrome extension, Firefox is next, but the WebRTC technology is so new that we don't even know yet if we have to build a separate network for Firefox or if the Firefox extension can communicate with the Chrome extension. For now Opera and Safari don't support WebRTC yet, but hopefully soon!

**[Download the extension for Chrome](https://chrome.google.com/webstore/detail/blippex/fnmgddilgkocbbhcmjdbioapbjlnjlnp)**

Of course, the plugin is open source, you can check how it works [here](https://github.com/blippex/blippex_plugin_chrome).  

If you want to disable the anonymizing network just click on the Blippex icon in Chrome and in the option you can disable it, then the data will be  uploaded the old fashion way. 

We would love to hear your feedback on this!
