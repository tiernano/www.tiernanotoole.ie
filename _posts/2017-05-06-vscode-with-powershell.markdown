---
layout: post
title: "VSCode and Markdown Monster with Powershell"
tags:
  - Powershell
  - Blogging
date: "2017-05-06 13:00"
published: true
---
A few years back, i created a post showing you how to add an Alias to PowerShell [to easily start Sublime Text][1] from a command line. This worked well, but this is 2017 (that post is from 2012!) and my daily text editor has changed. I have moved to [Visual Studio Code][2] for most of my daily work. It works well for 95% of my daily work. I still use [Visual Studio Pro][5] for Development, but for quick fixes, Code is great. For blogging, on the other hand, I am moving more and more towards [MarkDown Monster][3].  

Anyway, to upgrade the post, and to be able to use VS Code and MarkDown Monster from your PowerShell command line, i added the following:

    Set-Alias code "C:\Program Files (x86)\Microsoft VS Code\Code.exe"
    Set-Alias mm "C:\Program Files (x86)\Markdown Monster\MarkdownMonster.exe"
    
You can either run this each time you open PowerShell (pain) or you can add it to your `Microsoft.PowerShell_profile.ps1` which lives in your `Document\WindowsPowerShell` folder. If you dont have one, just create the file, add that piece of text, and next time you open PowerShell, you are good to go. 

in my case, i am actually in the [Visual Studio Code Insiders][4] group, do my alias is:

    Set-Alias code "C:\Program Files (x86)\Microsoft VS Code Insiders\Code - Insiders.exe"
    
When these are set, you can now run the following commands:

    code filename.txt 
    code folder
    mm filename.txt
    
VSCode will open either files or folders, but it seems Markdown Monster only opens files. 

[1]:https://www.tiernanotoole.ie/2012/08/30/SublimeText-With-Powershell.html
[2]:https://code.visualstudio.com/
[3]:https://markdownmonster.west-wind.com/
[4]:https://code.visualstudio.com/insiders
[5]:https://www.visualstudio.com/vs/