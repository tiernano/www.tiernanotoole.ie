---
layout: post
title: "Business Class Broadband... finally here...."
tags:
  - Networking
  - IPv6
  - HomeLab
date: "2017-03-09 21:00"
published: true
---
So, after many (MANY) years messing with dual cable modems, striggling to get them working together, to get websites to even allow me in, having to use hacks and kluges to get it to work at all... I have given up. It has been a struggle getting 2 modems working properly. Load banacing *kind* of works... but its messy at best. Some sites kick you out every now and again because your ip changes. Some sites wont let you login at all... Mind you, some sites work grand and dont ask questions...

And the whole idea of multiple modems, to allow you to download things faster, doesent work for everything... Anything you download in the browser is single threaded, so its limited to one modem... you can use use download accelerators, and they do work, but its an extra step, and some sites dont work for that either (MSDN for example). 

So, i have given up, bit the bullet, and moved to business class broadband. Its actually cheaper than the 2 residential lines i had, but it is also slower than the 2 combined: previously, it was 2 x 360/36mb/s. Now i am am on a single 400/40mb/s modem. That being said, there are definate advantages:

* Static IPs pretty much as standard, and option of either 1 or 5 (no inbetween!) Guess which one i went with? Its *technically* a /29 range, but the first usable IP is given to the modem, which acts as a gateway, so i end up with 5 usable. 
* Proper business class SLA. Any issues, someone who knows what they are talking about can help
* Phone lines on a seperate modem. So, i got phone lines with them, and they give a seperate modem for those lines, so as not to interfear with the internet. that modem has no internet connection and is just for calls. They are also working on a VoIP/SIP offering, which is something i am interested in. 
* Guarinteed speed! They guarintee a minimum speed to the modem at all time. Business customers have a priority on the network, which is nice.

So, only had it installed a week, and so far, so good. I have 1 IP given to my [PFSesne][1] box, and the rest given to a [VyOS][2] VM. The plan is to use the VyOS box for all network traffic, but first i need to do some testing and learning... Expect some posts on this soon!

[1]:http://www.pfsense.org
[2]:http://www.vyos.io 