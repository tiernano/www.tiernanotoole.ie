---
date: 2017-01-19T00:00:00Z
published: true
tags:
- Storage
- Tutorial
- S3
title: Distributed S3 data storage using Minio (and Zerotier)
slug: distributed-s3-storage-minio-zerotier
---

So, something i have been looking into in recient times has been [Distributed Storage][1], and, more specifically, how to use the storage in my [many, many machines][2] to protect data, and also increese my usable space... There are a few projects on the market that do this ([Ceph](https://ceph.com/), [NooBaa](http://www.noobaa.com/) and [Gluster](https://www.gluster.org/) all spring to mind) but some are more painful to setup than others... which brings me nicely to [Minio][3]. Minio is a 20ish MB executable you download from their site, mark it as executable (on Linux or Mac Boxes) and run... and you have yourself a S3 compatable storage server... Simples!

"But Wait!" i here you screem! "thats not distributed!". Well, yes... but, it can be! Their [Distributed Quick Start Guide][4], which is where i started with this, allows you to run a distributed copy of your data. I will let their documentation explain more, but this is what i did:

* download the minio server (single executable file) on a minimum of 4 machines. 
* on each machine, run a command like the following:

<script src="https://gist.github.com/tiernano/a6617921976eef0c1c79b3175bd76bf7.js"></script>

replacing accesskey and secretkey with keys (check minio documentation to get these) and foldertoexport with, well, the folder you want to export!

For me, i have 4 servers currently clustered. 2 are in [online.net](http://www.online.net) (one in Paris, one in Amsterdam), 1 in [OVH.NET](http://www.ovh.net) (France, somewhere) and one in Dublin ([GodBoxV2](https://www.tiernanotoole.ie/Computers/GodBoxV2.html) currently). They are all interconnected using [ZeroTier][5] (I will explain that later) and so far, so good... only ran some basic tests, but with it, i could loose 2 machines and still have data... Not bad for free! I will run some speed tests soon. 


[1]:https://en.wikipedia.org/wiki/Distributed_data_store
[2]:https://www.tiernanotoole.ie/Computers/
[3]:https://minio.io/
[4]:http://docs.minio.io/docs/distributed-minio-quickstart-guide
[5]:https://www.zerotier.com/
