---
categories:
    - technology
tags:
    - macOS
comments: false
date: 2013-05-22T00:00:00Z
title: OSX Disk Images
aliases: /technology/OSX-Disk-Images/
---

I wanted to create an encrypted disk image for my 2012 Tax Return documents, but unfortunately Disk Utility, which comes with OSX, does not allow image sizes (that are encrypted and journal HFS+) less than 10.5 MB. This seemed strange, so I looked for the command line equivalent. With the help of [this article][encrypt] I came up with this:

	hdiutil create -encryption -size 5m -volname 2012Taxes 2012Taxes.dmg -srcfolder ~/Desktop/foo/ -fs HFS+J

* 5M = disk image size (5 MB)
* 2012Taxes = disk image name when mounted
* 2012Taxes.dmg = disk image name
* -srcfolder is optional. It adds the files to any folder you provide
* HFS+J = format will be journaled HFS+ 

Note: you will be prompted for a password after you execute the command

For whatever reason I still could not create an encrypted disk image smaller than 5 MB, but the fact I could create one smaller than the Disk Utility seems odd.

[encrypt]: http://commandlinemac.blogspot.com/2008/12/using-hdiutil.html