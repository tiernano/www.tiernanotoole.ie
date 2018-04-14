---
date: 2018-03-06T08:00:00Z
publishdate: 2018-03-06 08:00:00 +0100
published: true
tags:
- Blogging
- Hardware
- Tools
title: Blogging on an iPad Pro
slug: blogging-on-ipad
aliases: 
    - "2018/03/06/blogging-on-ipad.html"
---

So, a few months back I bought myself an [iPad Pro][1]. I got a 10.5" with 64GB Storage and the [Smart Keyboard][2]. Since then, i have been mostly using it for playing around: watching YouTube, Netflix, surfing on the couch, etc. but i started to wonder how "Pro" this was...so i went and did some testing, and in the end nearly all of this post is being written on it... 

first, the good stuff:

* [Microsoft's Remote Desktop Connection][4] works perfect on the iPad Pro. I have RDPed into machines (with the help of [ZeroTier][5])
* [Panic's Prompt][3] works well too... again, with ZeroTier, i can SSH into boxes and remote manage them. Handy for checking on docker instances...
* Panic also have [Coda for iOS][6]. its a very nice (if somewhat expensive at $25) editor for the iPad. This post is being written on there now.
* for Git stuff, i am using an app called [Working Copy][7]. Its free, to an extend, but if you need to do stuff like push changes, which is kind of important, then you need to pay a fee. 
* Coda and Working Copy work together with some magic built into Working Copy. It can act as a [WebDav server][8], which Coda can the connect to. you open, edit, change and create docs, and Working Copy keeps note. then you swap to them and checkin. You need to have both apps on the screen at the same time (the docking feature works well for that) since iOS seems to kill some background tasks.
* Unrelated to blogging, but i have also tried editing photos using [Lightroom][9], and so far so good. I have used the [Apple SD Card adapter][10] to download 50MP photos (upwards of 60MB) from my [Canon 5Ds][11] quick enough, add them to Lightroom, make some changes and send them to [Twitter](https://twitter.com/tiernano), Facebook (not Instagram just yet...) and it works well. I have managed to hook it to my [Gnarbox](http://www.gnarbox.com) too. 

Bad Stuff?

* keyboard takes a bit of getting used to. the Stupid "Global" button to swap keyboards (from 
English to Emoji) is in the place you would expect to find CTRL. and CTRL, Option and Cmd (remember, this is a "Mac" style keyboard) and all shifted one place... I would have preferred if they moved that somewhere else, or removed it altogether...
* a mouse would be very handy! I have tried pairing a bluetooth mouse to it, and no luck... it would be handy especially for editing documents and code, since touchscreen is "handy" some of the time, but not all the time...

So, there you have it. Blogging on an iPad. Would i give up my daily driver of my Surface Book and GodBoxV2 and just uses an iPad? Hell No... for basic stuff, it works well. Basic photo editing, blogging, surfing, etc, yes. But there is a reason my workstation has 16 processor cores and 160GB RAM: I need it. I have multiple copies of Visual Studio running, SQL Server, multiple VMs running different tasks, multiple web browsers, multiple monitors, etc. the iPad can do a good chunk of stuff, but not the major stuff... not yet. Don't get me wrong: Word, Excel, Power Point, Outlook. all the major office tools work grand. But Visual Studio? SQL Management Studio? just not there yet...

So, what did i not do on the iPad, and ended up doing on the PC? Well, so far, nothing... using Coda and Working Copy, i wrote the text, previewed it and checked it into GitHub. Then, Prompt is being used to build it on my docker box, check into the static site and push, which will then publish. unless you see an update below, all went as planned and all was done on an iPad...  


[1]:http://www.apple.com/ipad-pro
[2]:https://www.apple.com/shop/product/MPTL2LL/A/smart-keyboard-for-105‑inch-ipad-pro-us-english?fnode=37
[6]:https://itunes.apple.com/us/app/coda/id500906297?mt=8&at=11l4BV
[4]:https://itunes.apple.com/ai/app/microsoft-remote-desktop/id714464092?mt=8
[5]:http://www.zerotier.com
[3]:https://itunes.apple.com/us/app/prompt-2/id917437289?mt=8&uo=4&at=11l4BV
[7]:https://itunes.apple.com/us/app/working-copy/id896694807?mt=8&uo=6&at=1000lHq&ct=workingcopyapp
[8]:https://workingcopyapp.com/manual/webdav-server
[9]:https://itunes.apple.com/ai/app/adobe-lightroom-cc-for-ipad/id804177739?mt=8
[10]:https://www.apple.com/ie/shop/product/MJYT2ZM/A/lightning-to-sd-card-camera-reader
[11]:https://www.usa.canon.com/internet/portal/us/home/products/details/cameras/dslr/eos-5ds