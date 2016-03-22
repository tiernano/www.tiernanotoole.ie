---
layout: post
tags:
- Announcements
- Git
- RSync
- Jekyll
title: Moving sites to NearlyFreeSpeech
date: 2013-01-15 19:23:02
---
I have been running a Dedicated Server from [Hetzner][1] for a while now, but have started to look at what i am running on the site, and reailized i under utilize the machine a lot... For example, this site is generated using [Jekyll][2], which takes up very little power, and becomes static HTML files. My other blogs ([Tiernan's Comms Closet][3] and [GeekPhotographer][4]) are both low traffic [Wordpress][5] sites, and I run a couple of other static sites also for friends... All in all, not a lot of power...

Its not a fortune to run the server, the box i have has a Quad Core, Hyper threaded Intel i7, 32Gb RAM, 2 3TB Hdds (not raid...) and runs a copy of [VMWare ESXi][6], and it costs about EUR60 a month, including a couple of IP addresses... But, i dont use it all that often... So, i am in the process of getting rid of it...

So, the 2 other blogs ([GeekPhotographer][4] and [Tiernan's Comms Closet][3]) have already moved. They where easy enough... Export the Wordpress DB, copy the file up, tweak the config, import the DB, DNS updates, etc... All done... but this site... that is more "Complicated"...

Since it is generated on a '[git push][7]', Jekyll and Ruby needs to be installed on the box... I am using static sites on [NearlyFreeSpeech][8] which only charge me per meg (about 0.1c, but that reduces as you transfer more) transfered and per 5 meg stored (1c). Thats for STATIC sites... if you are running a dynamic site, its about 1c per 1mb stored, plus 1c per day, plus another 2c for MySQL instances. Check out their [pricing calculator][9] to see the magic at work! 

Anyway, my GIT repo is on a machine in the house. It has Jekyll and all required bits installed. In the 'post-receive' hook (check [the original zerosum post][10]), i generate the site, and then do an rsync copy to NFSN servers. That is it! 

Any question, leave a comment.

[update] forgot to add the [gist][11] which shows how i do the rsync call...

{% gist 4545178 %}

[update2] you in my case, the folder that Jekyll is being built in needed to be chmoded and chowned... I chowned the the folder to the gitolite user and i chmodded the folder to 777... before i did this, some files where unreadable on NFSN... with this, all works grand...  

[1]: http://www.hetzner.de/en
[2]: http://www.vmware.com/products/vsphere-hypervisor/overview.html
[3]: http://blog.lotas-smartman.net
[4]: http://www.geekphotographer.com
[5]: http://www.wordpress.org
[6]: https://github.com/mojombo/jekyll
[7]: http://tiernanotoole.ie/2012/08/29/NewSite.html
[8]: http://www.nearlyfreespeech.net/
[9]: https://www.nearlyfreespeech.net/estimate
[10]: http://blog.zerosum.org/2010/11/01/pure-git-deploy-workflow.html
[11]: https://gist.github.com/4545178
