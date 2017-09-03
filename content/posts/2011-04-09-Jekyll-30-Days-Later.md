---
categories:
    - technology
date: 2011-04-09T00:00:00Z
tags:
    - technology
    - blogging
title: Jekyll 30 Days Later
aliases: 
    - /2011/04/Jekyll-30-Days-Later/
    - /technology/Jekyll-30-Days-Later/
---

It has now been over a month since I started my [Text File Revolution][tfr] using [Jekyll][] as my vehicle. This will be my seventh post using Jekyll and my still evolving workflow. So why not share my experience so far?

## Jekyll Out of the Box ##
Jekyll is not your normal blogging system where you can simply write your post in a browser or use a blogging tool like [MarsEdit][]. Jekyll does not store your posts in a database nor does it serve content dynamically. Jekyll simply generates static HTML files based on your posts (text files) using templates (similar to a theme) that you create. That's it. The author is responsible for moving those static HTML files to where the site is hosted.

## Current (Manual) Workflow ##
I still intend on writing a post on how to setup Jekyll from start to finish. I performed the required steps on three different systems taking notes along the way. For now though, I just want to share my current workflow and how I intend on improving it.

![JekyllManualWorkflow](/uploads/2011/04/JekyllManualWorkflow.jpg "Jekyll Workflow")

1. Create a new text file in my _posts_ directory (full path: `~/brandon/Dropbox/sites/brandonbohling.com/source/_posts`) using the naming convention: YYYY-MM-DD-Title.md. Example: `2011-04-09-Jekyll-30-Days-Later.md`
2. In the new document type _.blog_ which triggers [TextExpander][] to create the post shell.
3. Write the post using [Markdown][] (a text-to-HTML conversion tool for web writers). Save work.
4. Open Terminal, navigate to the `source` directory and execute the command `jekyll`.
5. Review and edit locally, `http://0.0.0.0:4000/` _Not pictured above._
6. Use Transmit to sync local changes to the brandonbohling.com web server.

## Ways to Improve My Workflow ##

I would have little issue sticking with the workflow above. However, I do understand that there are some inefficiencies and technical hurdles, so the geek inside is restless. The two main areas which I want to improve on:

1. blog post setup (steps 1 and 2 above)
2. publishing posts (steps 4 and 6; somewhat step 5)

### Improve: Blog Post Setup ###

There is not much to this. I will likely combine steps 1 and 2 above using a script of some sort that I either execute via Terminal or some other trigger like TextExpander. It is only a minor inconvenience at this point and is not a roadblock to writing using an iOS device. Thus, I will not spend much effort on optimizing this until I first work on...

### Improve: Publishing Posts

While there are several ways to implement the first improvement, there are many, many ways to implement the second one. And it is the second one where the most time can be saved as well as eliminate one of the primary downsides to using Jekyll...needing to manually run the Jekyll command to generate the site, which is not possible if I am using an iOS device.

Probably the easiest way to improve efficiency would be to write an [rsync][] command. However, I would rather automate the entire publishing process so even if I was on an iOS device I could publish a blog post. This likely means I will need some folder watcher program which will monitors for updates, which would trigger a Jekyll build and then push the files to my ISP. Given that I am already using Dropbox I would think I could reuse some of its powers. Currently I am envisioning a workflow something like this:

1. Execute command or double-click icon and blog post template is created with today's date and a placeholder title for the file name, prefixed with the word DRAFT. Prefixing with DRAFT will keep the post from being automatically published.
2. Write the post using Markdown as I do today.
3. Remove DRAFT from the filename
4. Previous step triggers a program to execute Jekyll command and then upload the files to my ISP.

Here are some sticking points:

This would require me to have a system that was always on to execute step 4. This is not a deal breaker as I do have a system on 95% of the time. The only time I purposely turn off our iMac is when we go on vacation, which would happen to coincide with when I would most likely write and want to post though.

Less of an issue would be the lack of truly reviewing my work in a web browser before publishing. This would only occur when using an iOS device to write and publish, so again not a deal breaker, but a consideration nonetheless.

## Summary

For those that absolutely love the ease of publishing with blogging software like WordPress (and similar) will likely be appalled at the Jekyll workflow. However, as I noted in [Text File Revolution][tfr] I wanted full control and ownership of my content, so I am willing to suffer slightly with its manual process. With a little extra work I think I can make it just as painless as WordPress though.

What I find interesting is the sudden flood of posts and discussions around static (or baked) blogs. Brent Simmons may have started it with his [A Plea for Baked Weblogs][baked] post, but other notable folks have discussed as well. Maybe most surprising is [Marco Arment][marco] cofounder of [Tumblr][] and founder of [Instapaper][] talks about it with [Dan Benjamin][dan] on Build & Analyze in [Episode 18][18] and [Episode 19][19]. Marco is writing his own static web site generator using PHP while Dan is trying at Jekyll. I am very curious to see if they talk about their experience more in Episode 20. For me, I am thrilled I have moved to Jekyll.

[tfr]: /2011/03/Text-File-Revolution/ "Text File Revolution by Brandon Bohling"
[Jekyll]: http://jekyllrb.com/ "Jekyll - static website generator"
[MarsEdit]: http://www.red-sweater.com/marsedit/ "MarsEdit 3 - desktop blog editing for the Mac"
[TextExpander]: http://smilesoftware.com/TextExpander/ "TextExpander - Mac Typing Shortcut Utility Saves You Time"
[Markdown]: http://daringfireball.net/projects/markdown/ "Markdown - text-to-HTML conversion tool for web writers"
[rsync]: http://en.wikipedia.org/wiki/Rsync "rsync - synchronizes files and directories from one location to another"
[baked]: http://inessential.com/2011/03/16/a_plea_for_baked_weblogs "A Plea for Baked Weblogs by Brent Simmons"
[instapaper]: http://instapaper.com/ "Instapaper"
[tumblr]: http://tumblr.com "Tumblr"
[marco]: http://www.marco.org/ "Marco Arment founder of Instapaper"
[dan]: http://5by5.tv/people/dan-benjamin "Dan Benjamin of 5by5 fame"
[18]: http://5by5.tv/buildanalyze/18 "Build and Analyze Episode 18"
[19]: http://5by5.tv/buildanalyze/19 "Build and Analyze Episode 19""