---
layout: post
tags:
- Programming
title: Custom MSDeploy OverWrite Rules
date: 2012-10-31  9:45:54
---
I have a project which we are trying to automate the deployment system. The plan is to automatically deploy the project to a staging server anytime the build succeeds from SVN. 

I have had a few problems with this, but here are some of the links which may come in handy for you.

* [MSDeploy skip rules when using MSBuild PublishProfile with Visual Studio 2012][1]
* [Web Deploy : Customizing a deployment package][2]
* [How to set MSDeploy settings in .csproj file][3]
* [MSBuild target VSMSdeploy doesn't seem to support skip with a skipAction][4]

Still some tweaks to get this to work... If i find any more links i will put them here... The problem we are haivng is when a deploy happens, the WebDeployment tool cannot overwrite the log files directory, since they are in use... one option would be to restart IIS, which would be ok in staging, but we want to keep the logs in test and production, so, we need to figure out how to tell Web Deploy not to over write the files. 

[1]:http://stackoverflow.com/questions/12576662/msdeploy-skip-rules-when-using-msbuild-publishprofile-with-visual-studio-2012
[2]:http://blog.alanta.nl/2011/02/web-deploy-customizing-deployment.html
[3]:http://stackoverflow.com/questions/7100751/how-to-set-msdeploy-settings-in-csproj-file
[4]:http://forums.iis.net/p/1170702/1953807.aspx#1953807