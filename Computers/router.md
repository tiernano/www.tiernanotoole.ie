---
layout: computers
title: Router
sitemap:
    priority: 0.7
    changefreq: 'weekly'
    lastmod: 2015-07-16T13:37:00
---
HP Proliant ML110G5 running [PFSense][1] 2.2.3. This machine has a [Core2Quad Q6600][3], 8Gb RAM and some storage... 
It also has 12 Gigabit network ports:

* 2 Quad port Intel Gigabit NICs (PCI Express)
* 1 Dual Port Intel Gigabit NIC (PCI-X in a PCI slot)
* 1 Single Port Intel Gigabit NIC (PCI Express)
* 1 Single onboard NIC (dont know who make it)

Internet wise, there are 3 WAN links on connected to the machine:

* 2 [UPC][4] Unlimited 240Mb/s Cable modems each with 24Mb/s upload speed. The modems are Cisco EPC-3925s and have been put into bridge mode.
* 1 [Vodafone][5] Fiber (VDSL) "Broadband only" connection. This is listed as 100mb/s down, 20mb/s up, but closer to 70/20. Connected to PFSense using PPPoE.

All 3 connections are setup in Load Balanced mode. PFSense gives more weight (3:3:1 ratio), meaning that the 2 cables get 6 times the traffic as the VDSL link... The Multi WAN stuff is detailed on [the PFSense wiki][2]. 
An older screen shot of a speed test is below:

<a href="/post_images/tumblr_nkoi26HcMZ1s6snd0o1_500.jpg"><img src="/post_images/tumblr_nkoi26HcMZ1s6snd0o1_500.jpg" alt="Speed Test"></a>

[1]: http://www.pfsesne.org
[2]: https://doc.pfsense.org/index.php/Multi-WAN
[3]: http://ark.intel.com/products/29765/Intel-Core2-Quad-Processor-Q6600-8M-Cache-2_40-GHz-1066-MHz-FSB?q=Q6600
[4]: http://www.upc.ie
[5]: http://www.vodafone.ie
