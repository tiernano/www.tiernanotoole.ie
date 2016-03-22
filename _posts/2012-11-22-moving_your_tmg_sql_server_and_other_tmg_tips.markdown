---
layout: post
tags:
- TMG
- Networking
title: moving your TMG SQL server Logs DB and other TMG tips
date: 2012-11-22  8:27:55
---
In house, I have been using [Microsoft TMG 2010 Server][1] for a while now. I use it as a firewall for some of the machines on the network, and also as a proxy for most, if not all, machines. When acting as a Firewall, all traffic flows though the machine, be it HTTP/HTTPS, SMTP/POP3/IMAP, or anything for that matter. You can also lock down ports on the box, which is a feature of most firewalls, but i like TMG due to its relitive ease of use...

Anyway, one problem with routing all traffic from different machines though TMG is after a while, the logging starts getting big. Single TMG by default is set to use [SQL Server][2], it can start using lots of memory, hard drive space, etc. So, there are a couple of articles which should make moving your TMG's SQL DB to a different machine easier...

* [Configuring Forefront TMG Logs][3]
* [Configuring (TMG) logging to a remote server][4]
* [How to configure Forefront TMG logging into a central Microsoft SQL Server database][5]

Some other tips you may find useful

* If you have Malware Inspection turned on, but you know there are certain sites that wont serve Malware (for example, Ubutnu Archives or YouTube.com) you can add these to the "Destination Exceptions" list. Under "Web Access Policy", click "Malware Inspection" and click "Destination Exceptions". Double click on the "Sites Exempt from Malware Inspection" and add your URL. I put *.ubuntu.com and *.youtube.com in here (Microsoft Updates are already on the list). Now, when downloading files from these locations, they do not run though inspection and save CPU cycles. **WANRING** You need to trust these sites! 
* There is a nice little app to add into TMG called [Bandwidth Splitter][6] which allows you to not only monitor what traffic is going though your network, but also put limits on different machine sets, users, etc. There is a [Free editon][7] which works with only 10 clients, but does what i need it to do to start with. 

[1]:http://www.microsoft.com/tmg
[2]:http://www.microsoft.com/sql
[3]:http://technet.microsoft.com/en-us/library/bb794937.aspx
[4]:http://technet.microsoft.com/en-us/library/dd441079.aspx
[5]:http://www.isaserver.org/tutorials/How-configure-Forefront-TMG-logging-into-central-Microsoft-SQL-Server-database.html
[6]:http://www.bsplitter.com/
[7]:http://www.bsplitter.com/download.aspx#trial_restrictions