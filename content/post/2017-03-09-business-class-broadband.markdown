---
date: 2017-03-09T00:00:00Z
published: true
tags:
- Networking
- IPv6
- HomeLab
title: Business Class Broadband... finally here....
slug: business-class-broadband
aliases:
    - "2017/03/09/business-class-broadband.html"
---

So, after many (MANY) years messing with dual cable modems, struggling to get them working together, to get websites to even allow me in, having to use hacks and kluges to get it to work at all... I have given up. It has been a struggle getting two modems working properly. Load blanching *kind* of works... but it's messy at best. Some sites kick you out every now and again because your IP changes. Some sites wont let you login at all... Mind you, some sites work grand and don't ask questions...

And the whole idea of multiple modems, to allow you to download things faster, doesn't work for everything... Anything you download in the browser is single threaded, so its limited to one modem... you can use use download accelerators, and they do work, but its an extra step, and some sites don't work for that either (MSDN for example). 

So, i have given up, bit the bullet, and moved to business class broadband from [Virgin Media][3]. It's actually cheaper than the two residential lines i had, but it is also slower than the two combined: previously, it was two x 360/36mb/s. Now i am am on a single 400/40mb/s modem. That being said, there are definite advantages:

* Static IPs pretty much as standard, and option of either one or five (no unbeaten!) Guess which one i went with? Its *technically* a /29 range, but the first usable IP is given to the modem, which acts as a gateway, so i end up with five usable. 
* Proper business class SLA. Any issues, someone who knows what they are talking about can help
* Phone lines on a separate modem. So, i got phone lines with them, and they give a separate modem for those lines, so as not to interfere with the internet. that modem has no internet connection and is just for calls. They are also working on a VoIP/SIP offering, which is something i am interested in. 
* Guaranteed speed! They guarantee a minimum speed to the modem at all time. Business customers have a priority on the network, which is nice. And, during testing, so far, i am getting the advertised speed most of the time. I needed to download a Windows 10 ISO yesterday from the MSDN, and it came in at between 45 and 48MBytes/s! 

So, only had it installed a week, and so far, so good. I have one IP given to my [PFSesne][1] box, and the rest given to a [VyOS][2] VM. The plan is to use the VyOS box for all network traffic, but first i need to do some testing and learning... Expect some posts on this soon!

[1]:http://www.pfsense.org
[2]:http://www.vyos.io
[3]:https://www.virginmedia.ie/business/