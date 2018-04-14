---
date: 2017-05-05T00:00:00Z
published: true
tags:
- Networking
- IPv6
- HomeLab
title: Zerotier and Minio Followup
slug: zerotier-minio-update
aliases:
    - "2017/05/05/zerotier-minio-update.html"
---

in a [previous post][1], I talked about setting up a distributed S3 like data storage system using [Minio][6] and [ZeroTier][7]. Well, this week, the ZeroTier guys tweeted about this.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Distributed S3 data storage using <a href="https://twitter.com/Minio">@minio</a> and <a href="https://twitter.com/hashtag/ZeroTier?src=hash">#ZeroTier</a> -- <a href="https://t.co/MAXTjo3muh">https://t.co/MAXTjo3muh</a></p>&mdash; ZeroTier, Inc. (@ZeroTier) <a href="https://twitter.com/ZeroTier/status/859557214997970944">May 2, 2017</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

A few people then started asking questions, and looking for a follow up, so here it is...

First, a quick recap. I had 4 machines, all running Linux. Three of them were in 1 time zone (GMT+1) and one was in another (GMT). Looking at the [Distributed Minio Quickstart Guide][4] again, there is a mention of times being in sync... which is probably why this did not work as planned... and by "not work as planed", I mean that Minio would crash, or not be responsive, or not write data in the place it should have... which was a pain. But looking at the documentation again, they do mention that Windows support is "experimental" which means, hopefully, some day it will be not so experimental, and might work... Given that most of my machines in house are Windows boxes, this would be a nice feature.

Now, what about ZeroTier? Given they posted it to their twitter? Well, it worked. it did the inter connect stuff well, and, given bandwidth limitations on a home broadband connection, it was still quite fast.

So, the question is, how fast? Well, on my [Surface Book][8] on a WiFi connection in the house, behind a [Meraki][2] [MX64][3] firewall, connecting to [the GodBoxV2][5] over FTP though ZeroTier, i get the following result:

[![FTP over ZeroTier](https://www.tiernanotoole.ie/post_images/2017/05/05/ftpdownload-zerotier-rs.png)](https://www.tiernanotoole.ie/post_images/2017/05/05/ftpdownload-zerotier.png)

the same download over FTP direct (no ZeroTier) does the following:

[![FTP direct](https://www.tiernanotoole.ie/post_images/2017/05/05/ftpdownload-direct-rs.png)](https://www.tiernanotoole.ie/post_images/2017/05/05/ftpdownload-direct.png)

So, direct over FTP is faster... in this instance by about 70%, but, over the download, it did get slower (seen it hit 12 at one stage) and because its over WiFi, those are a bit wonky... 

I did get one last screen shot:

[![network speed](https://www.tiernanotoole.ie/post_images/2017/05/05/networkseed-rs.png)](https://www.tiernanotoole.ie/post_images/2017/05/05/networkspeed.png)

as you can see, the Zerotier network adapter is showing 77.3Mbps, but the main network adapter is showing 80.8Mbps. There would be other traffic there, but if we assume there is nothing but ZeroTier traffic being sent, there is about 5% of an overhead. 

So, to wrap up: Minio and its distributed storage system over ZeroTier needs more testing. Ideally, all hosts need to be in the same time zone, or at least have the same time... Will try work on that soon. As for ZeroTier? I am extremely happy with them. Its fast, easy to setup, and easy to configure. What more could you ask for? Oh, and free, unless you need a pro account! 

[1]:https://www.tiernanotoole.ie/2017/01/19/distributed-s3-storage-minio-zerotier.html
[4]:https://docs.minio.io/docs/distributed-minio-quickstart-guide
[2]:http://www.meraki.com
[3]:https://meraki.cisco.com/products/appliances/mx64
[5]:https://www.tiernanotoole.ie/Computers/GodBoxV2.html
[6]:https://minio.io/
[7]:https://www.zerotier.com/
[8]:https://www.tiernanotoole.ie/Computers/surfacebook.html