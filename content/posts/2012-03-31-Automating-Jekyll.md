---
categories:
    - technology
date: 2012-03-31T00:00:00Z
tags:
    - blogging
    - workflow
title: Automating Jekyll
aliases: /technology/Automating-Jekyll/
---

March 06, 2012, marked the one year anniversary of this site being driven by [Jekyll][jekyll]. I will not rehash my reasonings here as I explained myself already in the [Text File Revolution][revolution] post, but I do want to reflect for a moment...

Since switching to [Jekyll][jekyll] I have written a mere 28 times; a personal worst in my 9 years of blogging[^fn1]. I would love to blame it on a busy life[^fn2], but that is a cop-out. Instead I will blame it on the small, publishing barrier associated with using [Jekyll][jekyll]. While it only took a couple of minutes to publish a post there, were _just enough_ steps to make the thought of writing less appealing. That is why I worked out a better (but not perfect) workflow.

## Automating Jekyll with Automator

Like any other technical issue, there are many solutions. Admittedly the solution below is far from perfect, but it is an incremental improvement over the default Jekyll _behavior_, but it does greatly reduce the barrier of publishing posts on the Jekyll platform.

I decided to use a built-in tool provided by Mac OS X, [Automator][automator]. I know true Mac geeks leverage Automator's power quite frequently. I, on the other hand, have only used it a handful of times. Here is how I used Automator.

### Automator Folder Action

1. Fire up Automator
2. Create a new "Folder Action"
3. Use rsync to download my current published content (always backup, right?)
4. Compress the published content
5. Use rsync to publish new content
6. Save the workflow

Below is a screenshot of the Automator workflow:

![Automator Workflow for Jekyll](/uploads/2012/03/AutomatorJekyllWorkflow.jpg)

### Implementing the Folder Action

Now you have to setup the folder to use the folder action:

1. Using Finder, navigator to the folder containing your post folder
2. Right-click on the post folder and select Services -> Folder Actions Setup...
3. Select the script you created with Automator

![Setting up Folder Action](/uploads/2012/03/FolderActionSetup.png)

What this does is set up a _folder watcher_ for the post folder. Anytime a file is __added__ it will execute the script that was created using Automator.

### New Workflow

What does my workflow look like now? Unfortunately this workflow requires me to have Jekyll running on one of my systems at all times. I am OK with this since I have chosen not to use [GitHub for my deployment][gdeploy]. Also, I am unable to install incron on my server to have a [fully automated publishing solution][tyler]. Lucky for me, my iMac is almost always running anyway.

1. Make sure the Jekyll server is running (do this initially and periodically)
2. Write my post (saving it anywhere but in my post folder with the Folder Action enabled)
3. When finished save to my post folder
4. Within a few seconds my post is published

This new, automated workflow allows me now to write posts on my iOS devices. No, it is far from perfect, but the barrier to write has just been lowered significantly.

### Areas for Improvement

So how do I want to improve my workflow? 

1. Have the Automator workflow (folder action) run Jekyll so I do not have to always have Jekyll running
2. OR setup my server hosting this site to watch the Dropbox folder (again, I do not believe my ISP allows for this)
3. Figure out a more efficient way to preview posts. Currently I have a separate Jekyll site for previewing. This means I have a second folder action watching the preview folder. This works just fine, but I have to imagine there is a better way.

In a few months I will provide an update on how things are going. Just in the last few days I have already increased my post count, but we all know how new-and-shiny-objects get a lot of attention at first. I do have another workflow improvement, but I will save that for another post.

Feel free to share your feedback. Like my photography workflow, I am always trying to improve my blogging efficiency.


[^fn1]: Another recent anniversary. March 03, 2003, was my first blog post using dasBlog written by [Clemens Vasters][vasters].
[^fn2]: Father of a 5 year old boy, changed jobs, new puppy, travel, ...

[jekyll]: http://jekyllrb.com/ "Jekyll"
[revolution]: /2011/03/Text-File-Revolution/ "Text File Revolution by Brandon Bohling"
[vasters]: http://vasters.com/clemensv/default.aspx "Clemens Vasters"
[automator]: http://en.wikipedia.org/wiki/Automator_(software) "Automator - Mac OS X"
[gdeploy]: https://github.com/mojombo/jekyll/wiki/Deployment "Jekyll Deployment Options"
[tyler]: http://clickontyler.com/blog/2011/11/publishing-your-blog-with-dropbox-and-jekyll/ "Publishing Your Blog with Dropbox and Jekyll"