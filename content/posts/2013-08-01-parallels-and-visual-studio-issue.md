---
categories:
    - technology
tags:
    - coding
comments: false
date: 2013-08-01T00:00:00Z
title: Parallels and Visual Studio Issue
aliases: 
    - /technology/parallels-and-visual-studio-issue/
---

After months of experiencing Visual Studio 2012 (running inside Parallels on my Mac) *hanging* when trying to exit out of the app I took a few minutes to look for a fix. Within a couple of minutes I came across [this thread][thread] which contained the solution to the issue. Based on the thread it seems like the root cause of this issue is that I am working on solutions that are stored on my Mac, `\\psf\Home\pathToSoltion` rather than working on solutions that are on the Windows (VM) C drive. Supposedly the Parallels team is aware of the issue and working on a fix, but you can fix it today within two minutes. Simply create a symbolic on the Windows VM.

1. In Windows, run a command prompt as administrator (Start, search for command prompt, right-click, run as administrator)
2. Type the command: `mklink /D "c:\mac" "\\psf\Home"`
3. Hit return
4. Now open solutions using `c:\mac\pathToSolution`

That's it. I only wish I would have looked for this solution months ago. 

[thread]: http://forum.parallels.com/showthread.php?262447-Visual-Studio-2012-Hangs-On-Close/page2