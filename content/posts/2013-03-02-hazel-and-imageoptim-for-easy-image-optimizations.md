---
categories:
    - technology
tags:
    - macos
    - utility
comments: false
date: 2013-03-02T00:00:00Z
title: Hazel and ImageOptim for Easy Image Optimizations
aliases: /2013/03/hazel-and-imageoptim-for-easy-image-optimizations/
---

[ImageOptim][io] is a fantastic utility to reduce the size of your images without impacting image quality[^fn-1]. I use it both for my web and iOS work, but it was not until today that I made it even better.


## My Old Workflow

1.  Save whatever image I was working on to some folder
2.  Open ImageOptim
3.  Drag the image onto ImageOptim canvas
4.  ImageOptim does its work
5.  I move the optimized image to its final destination

## My New Workflow

1.  Save whatever image I was working on to an “optimize” folder
2.  Hazel automatically moves to an “optimized” folder
3.  Hazel automatically kicks off ImageOptim and it optimizes the image
4.  I move the optimized image to its final destination

![Hazel rule with ImageOptim][io-pic]


My responsibilities went from four steps to two; a 50% reduction. I will admit that it only saves me a minute or so each time, but I am all about reducing inefficiencies and friction in my life right now. In addition, because I was testing image quality vs. file size of various screenshot apps ([Pixa][4], [Little Snapper][5], and [Voila][6]) I already saved myself at least 30 minutes.


With a little bit more work I could simplify or even remove the final step. Example: step 4 could be easy and fast by leveraging [Dropzone][7]. Simply drag the optimized image to a *dropzone* and it will place it in the appropriate directory, upload to a site, attach to an email, etc.


[^fn-1]: The image used in this post was reduced 45% to 137KB.

[io]: http://imageoptim.com/ "ImageOptim — make websites and apps load faster (Mac app)"
[io-pic]: /uploads/2013/03/ImageOptimAndHazel.png "Hazel rule with ImageOptim"
[4]: http://www.pixa-app.com/ "Pixa - organizing your images, the easy way"
[5]: http://www.realmacsoftware.com/littlesnapper/ "Screenshot & Website Capture For Mac - LittleSnapper"
[6]: http://www.globaldelight.com/voila/ "Voila - A complete screen capture and image editing tool for Mac OS X"
 [7]: http://aptonic.com/ "Introducing Dropzone 2"