---
date: 2017-09-25T07:00:00Z
publishdate: 2017-09-25 07:00:00 +0100
published: true
tags:
- Backup
- Tutorials
- Crashplan
- BackBlaze
title: New Backup Plans
slug: new-backup-plans
aliases: 
    - "2017/09/25/new-backup-plans.html"
---

So, a few weeks back, [CrashPlan](http://www.crashplan.com), one of my chosen backup services, decided to [kill their consumer backup plans](https://www.crashplan.com/en-us/consumer/nextsteps/). Which made me have to rethink my backup plan for the house...

**Note**: This is how I am backing up files, and may or may not work for you. Some of this is already in "production" as of today, but others are planned... Any questions, comments, etc, leave them in the comments.

So, first, as mentioned above, CrashPlan's consumer backup options are now dead. They are giving you the option of either upgrading to their Small Business Plan for free till the end of your current contract + 2 months, or moving to [Carbonite](https://www.carbonite.com/). For me, i just moved to their Small Business option, since its free, and meant that most of my backups just migrated over... i did not, how ever, look too much into Carbonite.

Just checking their site now, i would have to go for a minimum of the Plus plan, and that only allows me to backup 1 machine... I have 2 (currently) that get backed up... and probably more at a later date... and, given their yearly price for Plus is $75 per year, thats $150 for 2 current machines, and an extra $75 per machine after... Granted, they are saying its unlimited storage. but the extra fee per machine puts it out of contention...

For CrashPlans Small Business Plan, their plan is $10 per machine per month... So, my 2 machines would cost $240 per year to backup. They are giving me the next few months for free, and then for the first year, they are offering a discount of 75%, but we will see what happens when renewal comes along...

So, where does that leave me? Well, its looking like i will be using a mix of [BackBlaze](https://secure.backblaze.com/r/01px2w) and [Hubic](http://www.hubic.com). The current idea is as follows:

* GodBoxV2 and the Mac Mini both have [Drobos](http://www.drobo.com) plugged into them: the GodBoxV2 has a Drobo 5D, and the mini has a Drobo mini. There is also a Drobo FS on the network. I know they are not backup solutions, but its better than having stuff on single drives...

* For Windows boxes, I am backing up files to the cloud using [Duplicati](https://www.duplicati.com/). These are backed up to both Hubic and BackBlaze B2. Photos and importing files are backed up to both, and stuff i want backed up, but not in 2 places, is just backed up on Hubic.

* For my Mac mini, i use a a mix of Duplicati and [Arq Backup](https://www.arqbackup.com/). Arq got B2 support recently, so its very handy for that.

* For some of my Linux Boxes, i use [Duplicity](http://duplicity.nongnu.org/). You may need to walk though the steps i have [here](https://www.tiernanotoole.ie/2015/04/01/Duplicity_Hubic.html) to get it working with Hubic, and it also works with B2.

Some further notes:

* Hubic are charging about EUR5 a month for 10Tb of storage. If you refer people, that can go up. I have maxed mine out at 12.5Tb.

* Hubic is limited to 10mb/s for uploads and downloads. I never got anywhere close to that speed with CrashPlan (I'm based in Europe, they are in the US, so speed of light and what have you... maxed most of the time at 4ish). That being said, even those its "limited" to 10mb/s, i have seen higher.,.. might be 10 per thread...

* I did, for a while, use the BackBlaze app and service. I just didn't renew because of the move to B2. If you don't want to mess with stuff, their App works great.And if you use [this referal link](https://secure.backblaze.com/r/01px2w) you get a free month... Also, its FAST AF! it actually manged to max out my upload connection to their server! wont complain about that!

* B2 is cheap. 0.5c per gig stored... So, it works out at about $5 per TB per month, minus your usual bandwidth fees...

* Duplicati and Duplicity both have options to send emails on success or failure, or the like. I recommend having the emails on failure turned on at a minimum... also, on headless boxes, like my Linux box, i recommend checking the backup every week...

So, there we have it. Any questions?
