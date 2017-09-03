---
categories:
    - technology
date: 2011-08-27T00:00:00Z
tags:
    - blogging
    - macos
title: Installing Jekyll on Mac OS X
aliases: 
    - /technology/Installing-Jekyll-on-Mac/
    - /2011/08/Installing-Jekyll-on-Mac
---

In March this year I once again changed blog engines I was using. I switched to [Jekyll][] after reviewing all the usual (and unusual) suspects. I describe most of my reasons[^fn-jekyll] in my post, [Text File Revolution][revolution] so I won't rehash again, however, I did want to write a little tutorial on how to get Jekyll up and running on your Mac[^fn-contact].

## Pre-Requisite: XCode

The easiest way to get a hold of XCode is to [download from the Mac App Store][xcode].

## Pre-Requisite: Git

Git is not absolutely necessary, as RVM (the next pre-req) is available as a tarball, but Git is so popular these days I thought I would provide the instructions.

1. [Download Git][git]. At the time that I wrote this I downloaded the package called, git-1.7.6-x86_64-snow-leopard.dmg, for my MacBook Air. 
2. Mount (double-click) the DMG file
3. Double-click the PKG file to install
4. After installation is complete open Terminal
5. You need to execute the file, setup git PATH for non-terminal programs.sh, in the DMG file. I find it easiest to do this in Terminal:
    1. `cd /Volumes`
    2. `cd G` (then hit the tab key to autocomplete the volume)
    3. hit enter
    3. `./s` (then hit the tab key to autocomplete the shell script file name)
    4. hit enter to run script
6. Restart terminal and you now have Git installed

## Pre-Requisite: Ruby Version Manager (RVM)

Again, RVM is not absolutely required but RVM does ensure that you do not jack up your system by overwriting the OS version of Ruby with a newer version. RVM allows multiple versions of Ruby to be installed on a system (in your home directory, .rvm) and makes it super simple to change the *active* version.

1. Open Terminal and run the command below
2. `bash < <( curl https://rvm.beginrescueend.com/releases/rvm-install-head )`
3. Note the message in the Terminal window after installation, it will be used below.
3. Next use your favorite text editor and create a new text file that will be saved to your home directory as .profile. Below is what I did:
    1. Open TextMate
    2. Copied the text from the message in terminal message into TextMate: `[[ -s "/Users/bbohling/.rvm/scripts/rvm" ]] && source "/Users/bbohling/.rvm/scripts/rvm"`
    3. Saved the doc in my home directory (/Users/bbohling/.profile)
4. Now restart Terminal
5. Type `rvm help`. If installation was successful you will see help instructions.

## Pre-Requisite: Ruby

Next we will install Ruby version 1.9.2. At this time Ruby version 1.8.7 comes with OS X (Lion). Since we installed RVM, this step is easy-peasy.

Lion users: You will need to open the .profile file and add the following line: `export CC=/usr/bin/gcc-4.2`. This sets the default compiler to gcc.

1. Open Terminal
2. `rvm install 1.9.2`
3. Now that Ruby is installed you can type the following command to use the newer version of Ruby: `rvm use 1.9.2`
4. To verify type: `ruby -v`
5. To make 1.9.2 the default: `rvm --default 1.9.2`

## Installing Jekyll

Finally the star attraction, Jekyll...which surprisingly is the easiest part. I also use the Jekyll plugin, [jekyll-tagging][tagging], that provides a better solution (in my opinion) than the built-in categories feature.

1. `gem install jekyll`
2. `gem install jekyll-tagging`

Jekyll is now installed and you are capable of creating your own static, text-based website. I will try to write a follow-up post that describes how I have set up my templates and configuration. In the meantime, [check out the docs][jekyll-docs].


[^fn-contact]: I performed all of these steps as I went through them myself so they should be accurate. If not, please let me know: brandon [at] bohling [dot] me.
[^fn-jekyll]: I just came across a post by Stephen Ramsay today on the topic, [Back to the Roots Web with Jekyll][roots-web].

[git]: http://code.google.com/p/git-osx-installer/ "Git Installer"
[jekyll]: http://jekyllrb.com/ "Jekyll - transform your text into a monster"
[jekyll-docs]: https://github.com/mojombo/jekyll "Jekyll - documentation on GitHub"
[revolution]: /2011/03/Text-File-Revolution/ "Text File Revolution by Brandon Bohling"
[roots-web]: http://lenz.unl.edu/2011/06/13/back-to-the-roots-web-with-jekyll.html "Back to the Roots Web with Jekyll by Stephen Ramsay"
[tagging]: https://github.com/pattex/jekyll-tagging "jekyll-tagging - Jekyll plugin to automatically generate a tag cloud and tag pages"
[xcode]: http://itunes.apple.com/us/app/xcode/id448457090?mt=12 "XCode"
