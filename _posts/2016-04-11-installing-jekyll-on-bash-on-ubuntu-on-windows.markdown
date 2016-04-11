---
layout: post
title: Installing Jekyll on Bash On Ubuntu on Windows
date: '2016-04-11 10:09'
tags:
  - Jekyll
  - HowTo
  - Code
  - Blogging
---
At the 2016 Build conference, Microsoft announced that [Bash on Ubuntu on Windows][1] was coming. Well, it [came out last week][2], and I installed it as soon as I could! My next challenge was to get [Jekyll][3] to run and install on it, so I can build and preview this site on my [Surface Book][4].

So, first, I needed to install version 2.0 of Ruby. There is a bit of messing involved for this, but first

    apt-get update
    apt-get install ruby2.0

Now, when you run

    ruby -v

you will still see ruby 1.9.x installed... and the github-pages gem, which includes Jekyll 3, requires ruby 2.0... ugh. after reading [this very long bug report][5] I got this:

    # Rename original out of the way, so updates / reinstalls don't squash our hack fix
    dpkg-divert --add --rename --divert /usr/bin/ruby.divert /usr/bin/ruby
    dpkg-divert --add --rename --divert /usr/bin/gem.divert /usr/bin/gem
    # Create an alternatives entry pointing ruby -> ruby2.0
    update-alternatives --install /usr/bin/ruby ruby /usr/bin/ruby2.0 1
    update-alternatives --install /usr/bin/gem gem /usr/bin/gem2.0 1

Now, when I run ruby -v, I am told I am on version 2.0! Happy days! Next, i installed bundler using

    gem install bundler

which uses a [Gemfile][6] to install the required gems, so running

    bundle install

*should* install all required gems but no luck... I tried adding ruby2.0 dev to the mix

    apt-get install ruby2.0-dev

but running jekyll from bash said it did not exist, and running

    bundle exec jekyll build

failed with a memory issue... ugh...

Anyway, next, I tried

    gem install github-pages -V

-v makes it verbose, so you can see what's going on... after a bit of time, and lots of output to the screen...

    jekyll build
    bash: /usr/bin/jekyll: No such file or directory

FECK! So, after a bit more digging, i find that jekyll is actually in /usr/local/bin/jekyll

    ln /usr/local/bin/jekyll /usr/bin/jekyll

solves that problem!

now running

    jekyll build

works perfectly, as does

    jekyll serve

HAPPY DAYS! Mind you, I am only using this as a testing and writing system. I have not tried [s3_website][7] just yet, but that is being sorted elsewhere anyway. Maybe my next post will explain that...


[1]:https://www.tiernanotoole.ie/2016/03/31/bash-on-ubuntu-on-windows.html
[2]:https://blogs.msdn.microsoft.com/commandline/2016/04/06/bash-on-ubuntu-on-windows-download-now-3/
[3]:https://jekyllrb.com/
[4]:https://www.microsoft.com/surface/en-us/devices/surface-book
[5]:https://bugs.launchpad.net/ubuntu/+source/ruby2.0/+bug/1310292
[6]:https://github.com/tiernano/www.tiernanotoole.ie/blob/master/Gemfile
[7]:https://github.com/laurilehmijoki/s3_website
