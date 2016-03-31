---
layout: post
title: Announcing B2 Uploader and Hubic Testing 2.0
date: 2016-01-15 23:55:00
tags:
- Announcement
- Code
- Hubic
- B2
---

I have 2 new side projects to announce on the site today. First has been running for a while (first check-in was December 28th) and it’s called [B2Uploader][1]. Its a fairly simple Windows application to upload files to [BackBlaze B2][5]. If you are not familiar with [BackBlaze][6], they provide unlimited backup storage for the low price of a fiver a month. They are the guys who design the [BackBlaze storage pods][7] (I want one, by the way!) that allow them to provide unlimited storage for the fiver a month (I currently backup over 4Tb to them!), and late last year, they started offing [B2][5] which is a storage platform on their pods, and it has a (somewhat) easy to use API. AND ITS CHEAP! half a cent, up 0.5c, per gig stored per month! That’s crazy cheap! 

[B2Uploader][1] uses the B2 API to upload files (it could do more, but currently, as the name suggests, its upload only). Its quite simple, and all the code is available. More stuff coming over the next few weeks. some of the usual badges for open source applications are below. if you want to shout at me, shout in the [Gitter chatroom][8] and I will reply. You can see the latest builds over on [travis-ci][9], and the [latest releases][10] are available on GitHub.

[![Join the chat at https://Gitter.im/tiernano/b2uploader](https://badges.Gitter.im/tiernano/b2uploader.svg)](https://Gitter.im/tiernano/b2uploader?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[![Build Status](https://travis-ci.org/tiernano/b2uploader.svg?branch=master)](https://travis-ci.org/tiernano/b2uploader)

The second project is still in the planning phase, and it’s an update to an older project I was working on called [HubicTesting][3]. The name is very cleverly called, wait for it... [HubicTesting 2.0][2]! I have mentioned [Hubic][11] before [here][13]. Cheap (about a tenner a month) for lots of storage (10TB!) but an odd API.. It uses [Swift][12] for storage, but has a weird(ish) API for authentication. Anyway, more details will be on the site once I write it up. 

So, anyone needing to upload files to B2, check out [B2Uploader][1]. Want to work with stuff on Hubic, check out [HubicTesting 2.0][2]. Any questions, drop me a mail or find me on the Gitter channel. Have a good one!

[1]: https://github.com/tiernano/b2uploader
[2]: https://github.com/tiernano/HubicTesting2.0
[3]: https://github.com/tiernano/HubicTesting
[4]: https://www.reddit.com/r/DataHoarder/comments/3xbx6y/b2_uploader_upload_directories_to_b2/
[5]: https://www.backblaze.com/b2/cloud-storage.html
[6]: https://secure.backblaze.com/r/01px2w
[7]: https://www.backblaze.com/blog/cloud-storage-hardware/
[8]: https://Gitter.im/tiernano/b2uploader
[9]: https://travis-ci.org/tiernano/b2uploader
[10]: https://github.com/tiernano/b2uploader/releases
[11]: http://www.hubic.com
[12]: http://docs.openstack.org/developer/swift/
[13]: https://www.tiernanotoole.ie/2015/03/31/HubiC_SWIFT_CURL.html
