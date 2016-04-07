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

![speed test result](/post_images/2016/03/29/20160329-speedtest.png)

As you can see, I can manage to get all my upload speed using speed test, but not all my download speed... tweaks need to be made...

[1]: http://www.ubnt.com
[2]: https://www.ubnt.com/edgemax/edgerouter-poe/
[3]: http://www.virginmedia.ie
[4]: /Computers/macmini.html
