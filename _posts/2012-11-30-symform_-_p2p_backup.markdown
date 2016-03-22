---
layout: post
tags:
- Backup
- Storage
- Networking
- P2P
title: Symform - P2P Backup
date: 2012-11-30  9:13:27
---
I have previously [posted about CrashPlan][1] as my Backup System. I also, a long time ago, talked about [Backing up SQL, MySQL and other stuff][2] on my other blog. Well, CrashPlan is all good, but there are 2 "niggly" bits with it...

* Its not FREE (well, this year i got it Free on Black Friday...) but it is cheap ($120 a year to backup 10 machines to the cloud aint bad.)
* Its NOT FAST! The CrashPlan Datacenters all live in the US, and my servers live in Europe (either Dublin or Germany). So, bandwidth is limited... Getting less than 1Mbit/s most times, but have seen it reach 3... I have 20Mbits/s upload... even half that would be nice...

So, thats where [Symform][3] comes in. Symform is a P2P Backup Service, which runs on Windows, Linux and MacOSX. In theory, it should run anywhere that has a [Mono][4] runtime since its written in .NET. Anyway, you start with 10Gb of free storage, and you can increese that by one of 2 ways:

* Pay money: for $0.15 per month, you get 1Gb of storage in the cloud
* Pay Bytes: For every 2Gb "Contributed" (which is actually more like a pledge than a contribution... more on that later) you get 1Gb storage in the cloud.

It works very well, and is nice a fast too. I have a few machines in house which are contribting stoage, a total of about 2Tb, and I have been given 1Tb storage in "The Cloud". There is a lot more on how this works on their "[How Symform Works][5]" section of their site.

I mentioned the "Contribution" VS "Pledge" up above... I have a machine in the house where i have Pledged 1Tb of storage. In reality, Symform can use the full 1Tb of storage, if it needs to, but is currently only using 168Gb. Now, that could just be that the machine is still getting files, and it will end up using the full 1Tb eventually, but either way, its all good. 

Also, as a couple of notes on Contribution and Backups: 

* The machine needs to be online and accessable on the internet at least 80% of the time, but 24/7 is ideal. If you drop below the 80%, your account can be suspended.
* your machine needs to be publically accessable, meaning port forwarded. I have a couple contribution machines in house, so they each have seperate ports forwarded to them.
* Given the P2P nature of the software, lots of connections to different machines are made... if you are behind a firewall, you may need to allow all or most outgoing connections. If you are on a really restrictive firewall, you may want to stick a contribution box in your [DMZ][6] and probably use the [Turbo Seeding][7] feature.
* Turbo Seeding is a handy feature, especially for Laptops... only problem is its Windows Only... So, importing and exporting does not work on Linux or OSX.
* The software can managed Work and Non Work hours, and will limit the upload and download speed during this time. Also a nice feature...

So far, so good. Very happy with the software, but would like a nicer interface to see whats going on. At the moment, you are either limited to using the web interface, which aint bad, but not great, or watching the log files... I would also like the ability to prioritize certain files or folders, so, for example, upload my documents folder before anything else, and if anything changes in there, even if its uploading from somewhere else, pause and upload the documents folder... Just a thought... 

[1]:http://tiernanotoole.ie/2012/08/30/CrashPlan-Backups.html
[2]:http://blog.lotas-smartman.net/new-backup-plan-out-with-jungle-disk-and-zmanda-cloud-backup-in-with-crashplan-mysqlbf-and-sqlbf/
[3]:https://control.symform.com/Organization/Referral?referralId=96E53D9DC4501633F2294EF202734DB08C00F044
[4]:http://www.mono-project.com/Main_Page
[5]:http://www.symform.com/join-the-revolution/how-symform-works/
[6]:http://en.wikipedia.org/wiki/DMZ_(computing)
[7]:http://www.symform.com/our-solutions/key-features/turbo-seeding/