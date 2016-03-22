---
layout: post
tags:
- Storage
- Code
title: Hubic, OpenStack Swift and Curl
date: 2015-03-31 22:40:00
---
[HubiC][1] is an online storage site, built by the guys at [OVH][2]. They are currently offering 30Gb free (if you use the link above) or if you pay, you get 110Gb (insted of the usual 100Gb) for EUR1 a month, or 10.5TB (yup... TERABYTES!) for EUR5 a month... Thats a crazy amount of storage for a not crazy amount of money! 

So, while playing around with different things, I found they have an [API][3], so other than the usual apps to play with (like the Hubic Apps for iPhone, Android, Windows Phone, Windows Desktop and OSX, [Duplicity][4] for backing up *nix boxes, and a few others) you can build your own...

But first, i needed to figure out how... So, after a lot of arsing around in Linux shells with [curl][5] i finally got some stuff working!

First, i used the [Hubic sandbox][6] to get the keys... its quite simple to walk though... this gets you your Access Token (see step 3). next, we need to get the Endpoint from Hubic: [This GIST shows more][7]: 

<script src="https://gist.github.com/tiernano/9c061ae8d1312190f152.js"></script>

Quick walkthough:

the first CURL request is to the HubiC API to get the credentials... this gives you a JSON response with a token and a endpoint URL aswell with an expire time... 

The next request gets you a list of all files (or at least a load of files in my case) of whats in your folder. the <pre>default</pre> name here is my folder... I think its what everyone starts out with in HubiC... if you remove it, you will see all your top level folders.

next request i tried was to upload a file... the <pre>filename</pre> part is where you want it to be stored. this must exist on your local machine. 

finally, downloading of a file... pass in the location of the file on the server (listing files will give you the location) and then <pre>-o</pre> in curl shows the output location... 

Simples! now to get this working in c#... [Full OpenStack Swift API is available][8] to show how to do more... hopefully it will help in my C# coding...


[1]: https://hubic.com/home/new/?referral=GMSQVQ
[2]: http://www.ovh.com
[3]: https://api.hubic.com/
[4]: http://duplicity.nongnu.org/
[5]: http://curl.haxx.se/
[6]: https://api.hubic.com/sandbox/
[7]: https://gist.github.com/tiernano/9c061ae8d1312190f152#file-gistfile1-txt
[8]: http://developer.openstack.org/api-ref-objectstorage-v1.html