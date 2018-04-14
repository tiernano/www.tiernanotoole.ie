---
date: 2016-11-15T00:00:00Z
published: true
tags:
- Docker
- Development
title: Docker Jekyll and Mr ngrok
slug: docker-jekyll-and-mr-ngrock
---

See what i did with the title?! Anyway, in [my last post][1], i explained how i was building this site with Docker running on Windows 10 with the Anniversary update. Today, i am going to show you how to host it using [Nginx][2] and [ngrok][3].

So, first, you should know what Nginx is at this stage... If not, check out [their site][2]. Next [ngrok][3] is basically a way of tunneling your localhost to the web. So, how do we build the whole lot together and serve your site to the internet? Well, this is what i have so far:

First, build your site in jekyll. for me, the command is

    docker run --rm -v "$(pwd):/src" -w /src ruby sh -c 'bundle install --path vendor/bundle && exec jekyll build -s www.tiernanotoole.ie/ -d www.tiernanotoole.ie/_site/'

next, run an nginx server with that output folder:

    docker run --name tiernanotoolenginx -v "$(pwd)/www.tiernanotoole.ie/_site/:/usr/share/nginx/html:ro" -d -p 8881:80 nginx

the docker container is called tiernanotoolenginx, since i could have multiple ones, and port 8881 is being redirected to port 80 on that container, but technically, it might not be needed due to the next command:

    docker run --rm -it --link tiernanotoolenginx wernight/ngrok ngrok http tiernanotoolenginx:80

essentially, what we are doing here is running ngrok and pointing it at post 80 on the nginx container... you see i did not point at 8881, since we are using the continer directly... it might be different if you were not...

when that command runs, you get a screen telling you the URL of your site with some basic stats. your site is now hosted publically, via an ngrok tunnel! you could run that container as a daemon, and leave it running, but for me, i wanted to do some minor testing, so i can kill it when i want...

So, all is good with the world!

[1]:https://www.tiernanotoole.ie/2016/11/02/building-jekyll-sites-with-docker-on-windows.html
[2]:https://www.nginx.com/
[3]:https://ngrok.com/
