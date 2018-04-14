---
date: 2017-08-16T00:00:00Z
publishdate: 2017-08-16 06:00:00 +0000
published: true
tags:
- Jekyll
- Website
- Tools
title: Testing Forestry
slug: testing-forestry
aliases: 
    - "2017/08/16/testing-forestry.html"
---

So, as you probably know, this site is built with [Jekyll](https://jekyllrb.com/). Jekyll is a Static Site Generator, basically taking an input of a load of text files (see the source repo for this site on [Github here](https://github.com/tiernano/www.tiernanotoole.ie/)) and generating a load more HTML (the static HTML is hosted on [Github here](https://github.com/tiernano/www.tiernanotoole.ie-static), which auto publishes to [Azure App Service](https://azure.microsoft.com/en-us/services/app-service/web/)).

In previous posts, i have talked about using the likes of [Visual Studio Code and Mark Down Monster](https://www.tiernanotoole.ie/2017/05/06/vscode-with-powershell.html) to build the site. Well, a few days back, i found [Forestry.io](https://forestry.io). Its a web application which, in my case, is linked with my [GitHub](https://www.github.com/) repo (the Jekyll source one) and allows me to make changes to the code easily. Because the way i build my site is a little different, i manually build the site and push to the destination GitHub project, but they have features allowing you to push directly to SFTP or FTP servers, GitHub, or some other options.

The interface is nice and easy to use, and you can use drafts, etc. Mind you, even with drafts, because files are written into a public repo, they are not fully private... I suppose I could just make the source repo private... Anyway, they are free for single user sites (like this) or they have paid plans for teams (say, your business blog with more than 1 user updating it, for example).