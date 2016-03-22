---
layout: post
tags:
- Programming
- Code
- HowTo
title: Compressing and UnCompressing Protobuf items in C#
date: 2012-12-12 11:29:32
---
Part of a project i am working on required sending large amounts of data between different instances. To get this to work efficially, we started using the [ProtoBuf][1] using [ProtoBuf-net][2] in .NET. but the files where still quite large (17mb, give or take). So, we looked into compression...

here is some examples of how we managed to compress the protobuf files. We got some decient compression: 3mb files, down from 17mb. very happy.

to compress an object (obj) and write to a temp file (tmpfile):

<script src="https://gist.github.com/4267147.js"></script>

to decompress the object back to a known type:

<script src="https://gist.github.com/4267157.js"></script>

[1]:http://code.google.com/p/protobuf/
[2]:http://code.google.com/p/protobuf-net/