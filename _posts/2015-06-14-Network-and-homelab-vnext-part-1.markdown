---
layout: post
tags:
- Networking
- PFSense
- Hardware
- HomeLab
title: Network and Homelab V.Next (Part 1)
date: 2015-06-14 16:05:00
---
So, its that time again... [HomeLab][2] upgrade time... Or at least the planning for it. I am in the process of rebuilding my home lab, which involves pull all old servers out of the rack and replacing them with new ones... It also means rewriting the network, possibly upgrading some existing gear and hopefully getting the whole lot done on a budget of some sort...

So, why? Well, biggest reason for all this is currently heat and power usage. We use about 4-6x more electricity than the average house here in Ireland, which means our electricity bill is fairly high. It also means that the lab, which is also my office/bedroom, gets quite warm and uncomfortable during the summer month. There is an Air-Con unit in the room, and, well, that's costing the most on electricity!   

So, what I got is a basic overview of what I want from the homelab and hopefully in the next post, I will have an idea of what it will look like..

* 3-4 machines running a Hyper Visor (HyperV, VMWare ESXi or other). Leaning more towards Hyper-V purely because its what I got currently and its what we use in our main office.
* each machine should be connected to at least 2 networks: one for storage and migration, one for "public" to the LAN. There may be more VLANs for other networks, but 2 is a start.
* ideally, 10Gb connections would be nice, but multiple 1Gb connections would also work.
* shared storage (iSCSI, SMB3, etc) would also be a nice to have, but may bump up the server count (not actually a problem) but would increase power and cooling costs. An off the shelf box, like a [Synology][1] could do the job... 
* Lower power usage and less heat produced is also a major requirement. Most of the boxes I am decommissioning are older Xeon hardware ([5000][3] series upto a [5200][4] series process and even an [older Xeon P4][5]!). The newer [Xeon E3][7] and the even newer [Xeon D][6] are a lot more efficient, use less power, produce less heat and are way faster than what I currently have. The E3 can use up to 32Gb of RAM and the Xeon D top out at 128Gb... Me being me would like more than 32Gb RAM... :)
* smaller machines would also be nice. I have been looking at both Xeon D and Xeon E3 Mini-ITX boards and cases for them. I do have a half height Dell Rack, which I host these machines, and ideally, these machines should be rack mountable, but micro ATX cases could work. 2 per shelf would work grand.
* Onboard IPMI and KVM support is something I want too... I do have a KVMoIP switch in the house, and it works, most of the time, but getting a box that has this embedded into the board would be ideal... A lot of the server boards had it as standard or allowed it to be speced, so that's all good.
* I am also thinking of upgrading the router to a similar spec board... Possibly a Xeon E3, or even an i5.... Ideally it should have IPMI and KVMoIP on board and should produce less heat. Biggest issues is getting enough network cards into the box...

These are my requirements at a  high level overview. Over time things may change, but lets see how we get on...

[1]:http://www.synology.com
[2]:http://tiernanotoole.ie/Computers
[3]:http://ark.intel.com/products/family/28144/Intel-Xeon-Processor-5000-Sequence#@All
[4]:http://ark.intel.com/products/series/33092/Intel-Xeon-Processor-5200-Series#@All
[5]:https://en.wikipedia.org/wiki/Xeon#Netburst-based_Xeon
[6]:http://www.intel.ie/content/www/ie/en/processors/xeon/xeon-processor-d-family.html
[7]:http://www.intel.ie/content/www/ie/en/processors/xeon/xeon-processor-e3-family.html
