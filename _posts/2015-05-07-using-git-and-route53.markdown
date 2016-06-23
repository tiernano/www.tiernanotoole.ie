---
layout: post
tags:
- DNS
- Networking
- Git
- Development
title: Using git and Route53 together
date: 2015-05-07 20:00:00
---
so, earlier on today, i was talking about using [Git with a DNS service called LuaDNS][1] to update your DNS records. Well, thing is, i have 30+ domains registered, and of them about 25 are hosted on [Amazon's Route53][2]. So, moving ALL of them seems, well at the moment, excessive... So, i went digging...

there is a tool called [cli53][3] which will allow you to manage route53 objects from the command line. It can also export your zones to BIND format and then re-import them if you have made changes... This all came out of a blog post by the guys and gals at [netguru][4] who showed how they integrate their DNS records with their Continuous Integration... Now, i have not gotten to that stage, just yet, but its only 1 step more down the road... but I don't have my zones in bind format... So, how do i do that?

I tweaked their block of ruby code (first time playing with ruby, be gentle with me) and got the following:

{% gist f11fbec2075b8bf19d57 %}

essentially, it runs cli53 (you may need to change your path) and then creates .bind files for each zone.

then, using their code below, you can re-import them to Route53:

{% gist 7249547 %}

i have exported all mine, added them to git and done some testing... All seems to be in order... once i do some tweaks, i can get that CI piece working and it should be all magic...

[1]:http://tiernanotoole.ie/2015/05/07/git-push-dns.html
[3]:https://github.com/barnybug/cli53
[2]:http://aws.amazon.com/route53
[4]:https://netguru.co/blog/ci-your-dns-setup
