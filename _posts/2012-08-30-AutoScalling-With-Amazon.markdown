---
layout: post
title: AutoScaling with Amazon
tags:
  - Amazon AWS
  - Cloud
---

I have a few [Amazon EC2][1] instances running on a project, and one of these instances was known as the Zombie Instance! Every time i killed it, it came back to life a few min later... I found out that i, at some point, set that instance to be in an [AutoScaling][2] group. Any time the instance died, Amazon would check and restart the instance. So, how did I kill this undead instance? Check out "[Auto Scaling with Amazon EC2 II][3]" on LLOVIZNA's blog. They had the same issue i had (trying to kill the Auto Scaling group gives an error) and figured out how to do it. Handy stuff. Now the instance is dead, and hopefully it wont come back any time soon... Mind you, When AutoScaling works correctly, it can be very cool indeed!


[1]: http://aws.amazon.com/ec2/
[2]: http://aws.amazon.com/autoscaling/
[3]: http://kkpradeeban.blogspot.ie/2011/02/auto-scaling-with-amazon-ec2-ii.html
