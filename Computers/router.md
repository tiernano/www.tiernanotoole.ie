---
layout: computers
title: Router
sitemap:
    priority: 0.7
    changefreq: 'weekly'
    lastmod: 2016-03-24T14:43:00
---
The main Internet Router in the lab is a [Ubiquiti Networks][1] [EdgeRouter POE][2]

Internet wise, there are 2 WAN links on connected to the machine:

* 2 [Virgin Media][3] Unlimited 360Mb/s Cable modems each with 36Mb/s upload speed. The modems are in bridge mode.


both connections are load balanced and some sites are sent over particular links (for example, all Apple traffic goes over WAN2, so Apple's caching server, running on the [mac mini][4] does its thing...

<a href="/post_images/tumblr_nkoi26HcMZ1s6snd0o1_500.jpg"><img src="/post_images/tumblr_nkoi26HcMZ1s6snd0o1_500.jpg" alt="Speed Test"></a>

[1]: http://www.ubnt.com
[2]: https://www.ubnt.com/edgemax/edgerouter-poe/
[3]: http://www.virginmedia.ie
[4]: /Computers/macmini.html
