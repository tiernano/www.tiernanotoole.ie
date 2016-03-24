---
layout: post
title: Continuous Integration and Blogging
date: 2016-03-24 08:00:00
tags:
- Blogging
- Announcements
- Jekyll
---
Back in August of 2012, I started this site using Git and Jekyll. I hosted most of it at home, pushing to a server in house. Then, a few years back, I moved to pushing the files to [Amazon S3][3] and had [Cloud Front][4] doing distribution. The last moved had me hosting the files in [NearlyFreeSpeech.NET][5] and [Cloud Flare][6] doing the content distribution... Well, that changed over the last few days... again...

Currently, you are still hitting Cloud Flare when you hit this site, but the backend is back to being hosted on Amazon S3. But the files getting to S3 is more interesting now. All the "code" for this site is up on a [GitHub repo][1] and any time something is checked in, [Travis CI][7] kicks off, builds the files using [Jekyll][8] and pushes to S3 using [s3_website][9]. All my "private" keys are hidden in Travis-CI, so no one can access them but me. This makes updating the site a lot easier. I can create a file in GitHub directly, preview it, make changes, etc., and then check in. Once checked in, Travis kicks off, builds and deploys. All Good! 

It also means that if "bugs" are found on the site (by you, my dear reader), or if you have queries for some things, a "bug report" can be opened on the [issues log][8]. I already have a bug for making the site faster... Anything else you want me to change? 



[1]:https://github.com/tiernano/www.tiernanotoole.ie
[2]:https://www.tiernanotoole.ie/2012/08/29/NewSite.html
[3]:https://aws.amazon.com/s3/
[4]:https://aws.amazon.com/cloudfront/
[5]:http://www.nearlyfreespeech.net
[6]:http://www.cloudflare.com
[7]:https://travis-ci.org/tiernano/www.tiernanotoole.ie
[8]:https://github.com/tiernano/www.tiernanotoole.ie/issues
[9]:https://github.com/laurilehmijoki/s3_website
