---
layout: post
tags:
  - DNS
  - Networking
  - Development
  - Git
title: Git Push DNS
date: 2015-05-07T15:30:00.000Z
---

There are now a lot of services that have "git push" options available... you can build websites with
[Azure][1] and [Github][2], books using [ShareLaTeX][3] and now, DNS using [LuaDNS][4]. I have one zone
running at the moment ([tiernanotoole.net][5]) and you can see the DNS records on [github here][6]. I am
tempted at moving other records over soon... but i am currently on [Amazon Route53][7] and 1: its works, so
dont break it, and 2, not sure how to bulk export records from Route53 to Bind or [Lua][8] format.

[update] 2 quick updates: 1) their free account, which is what i am using, allows 3 domains and 30 host
records. they also charge less than [Route53][7]:

* route 53 for 10 domains per year cost 50c per domain (first 25) per month, then query charges. total,
about $60 + queries (@40c per million).
* luadns cost $29 a year for 10 domains, 5 million (ish) querys a month and 500 host records...

I think i have nearly 30 domain on AWS... so, their $59 a year package, which include 30 domains, would
probably save me money...

and 2) i forgot about one of those git push services... [DeveloperMail][9] is a service, for developers,
for managing email servers. IMAP, SMTP, Git... all supported! just signed up... $2 a month per user. Lets
see how this works...


[1]:http://www.azure.com
[2]:http://www.github.com
[3]:https://www.sharelatex.com/
[4]:http://luadns.com
[5]:http://www.tiernanotoole.net
[6]:https://github.com/tiernano/dns
[7]:http://aws.amazon.com/route53
[8]:http://www.luadns.com/help.html#lua-zone-file-format
[9]:https://developermail.io/
