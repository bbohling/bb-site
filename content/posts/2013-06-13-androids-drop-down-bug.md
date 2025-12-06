---
categories:
    - technology
tags:
    - coding
comments: false
date: 2013-06-13T00:00:00Z
title: Android's Drop Down Bug
aliases:
    - /technology/androids-drop-down-bug/
---

On and off for several days now I have been trying to fix an issue where a drop down list (`<select>` tag) seems to be disabled on old (version 2.x) Android devices. Apparently this is a [known bug][bug] with [plenty][selectBox] of [suggested][stack] [fixes][scott]. Not a single one (or combination) worked for me. I even came across [this suggestion][iscroll] since we are using [iScroll][iscrollCode], but it did not help either.

## What was my solution?

Wanting to rule out any jQuery or Knockout issues, I added a simple, hard-coded drop down above the one I was having issues with:

    <select>
        <option>One</option>
        <option>Two</option>
    </select> 

And to no surprise, it did not work...however, now my original drop box did work! Unfortunately I cannot explain it nor can I take the time right now to figure it out, but I thought I would share anyway.

Obviously I could not have a random drop down on the screen so I just hid it using the following:

    //CSS
    #oldAndroidSelectFix { left: -9999px; }

    // HTML
    <select id="oldAndroidSelectFix">
        <option>One</option>
        <option>Two</option>
    </select> 

If you run into this issue I encourage you to start with the official bug report: [Android Issue 10280: browser - inactive dropdowns][bug]. There are several steps to try before using a horrible hack like mine.

[iscroll]: https://groups.google.com/forum/?fromgroups#!topic/iscroll/NqRIASglcj4
[iscrollCode]: http://cubiq.org/iscroll-4
[selectBox]: https://github.com/01org/appframework/tree/master/plugins#jqselectbox
[stack]: http://stackoverflow.com/a/15777026/1895616
[scott]: https://github.com/scottjehl/Device-Bugs/issues/3
[bug]: http://code.google.com/p/android/issues/detail?id=10280