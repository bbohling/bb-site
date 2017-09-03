---
categories:
    - link
    - technology
tags:
    - coding
    - powershell
    - microsoft
date: 2013-02-11T00:00:00Z
external-url: http://stackoverflow.com/a/1244872
format: link
title: Count Lines of Code in a Visual Studio Solution
aliases: /2013/02/count-lines-of-code-in-a-visual-studio-solution/
---

At work I was wading through a very old code base and was curious how many lines of code it contained. Not wanting to open the seemingly endless list of files in the solution, I went looking for a quick-n-dirty way to count the lines of code in the solution. Preferring a command-line approach than installing a utility that I would likely rarely use, I [found this simple powershell snippet](http://stackoverflow.com/a/1244872):

    (dir -include *.cs,*.cpp,*.h,*.idl,*.asmx -recurse | select-string .).Count
    

Note: you will want to navigate to the solution’s directory first, then execute the command above.