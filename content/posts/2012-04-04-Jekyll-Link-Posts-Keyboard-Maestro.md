---
categories:
    - technology
date: 2012-04-04T00:00:00Z
published: true
tags:
    - blogging
    - workflow
title: Jekyll Link Posts with Keyboard Maestro
aliases: /technology/Jekyll-Link-Posts-Keyboard-Maestro/
---

This has been a big week of knocking down the [Jekyll][jekyll] publishing barriers. [Automating the Jekyll publishing process][auto] was the first big one. As I stated in [that post][auto], it still is not perfect, but much, much better than the default Jekyll _behavior_. Next, I tweaked Jekyll so I could publish [link posts][linkposts], but what good is that feature unless I can publish them lickety-split? Luckily I remembered that [Ben Brooks][ben] [posted on this topic][benhow] recently (turns out it was just over a year ago). 

This is the macro I came up with taking [Ben's lead][benhow]:

![Keyboard Maestro Macro for Link Posts](/uploads/2012/04/KeyboardMaestroLinkPost.jpg "Keyboard Maestro Macro for Link Posts")

## The Workflow

When I am viewing a web page in Safari that I want to link to I do the following:

1. Highlight any text I want to quote.
2. Hit my Keyboard Maestro hot key to launch the _Link Post_ macro

That is it. After using the above 2 steps I got the following link post _start_ for my first link post, [How to find the hidden files on Mac OS X][howto]:

![Sample Output from Keyboard Maestro Link Post Macro](/uploads/2012/04/KMLP-Sample.jpg "Sample Output from Keyboard Maestro Link Post Macro")

Again, this is not perfect. Currently the macro is for Safari only. I also use Google Chrome (though mostly for Flash-based sites) so I need to create a Chrome-specific macro. Or better yet (if possible), tweak the macro to copy the relevant info of whichever browser is in the foreground. Hopefully someone much smarter than me will post a solution. Let the online discussions begin!

[jekyll]: http://jekyllrb.com/ "Jekyll Blogging Platform"
[linkposts]: /2012/04/Link-Posts-With-Jekyll/ "Link Posts with Jekyll by Brandon Bohling"
[auto]: /2012/03/Automating-Jekyll/ "Automating Jekyll by Brandon Bohling"
[ben]: http://benbrooks.me/ "Ben Brooks"
[benhow]: http://brooksreview.net/2011/03/cmd-one/ "How I Blow with Keyboard Maestro and TextMate by Ben Brooks"
[howto]: /2012/03/How-to-find-hidden-files-OSX/ "How to find the hidden files on Mac OS X by Brandon Bohling"