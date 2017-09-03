---
categories:
    - technology
tags:
    - coding
comments: false
date: 2013-08-16T00:00:00Z
published: true
title: Forgotten Step
aliases:
    - /technology/forgotten-step/
---

Even though I have probably set up a new Mac at least a dozen times in the last few years I keep forgetting the most basic step in the world of Terminal...creating a **.bash_profile** and adding an export path. This is key because it tells Terminal where to look for executable binaries. Hopefully writing the steps down will make sure I never forget this again.

1. Open TextEdit (or your favorite text editor)
2. Add `export PATH="$HOME/bin:$PATH"` on the first line
3. Save in your home directory (~/) as **.bash_profile**
4. If Terminal is open, restart it

If you really want to become a command line junky [check out these dotfiles](https://github.com/mathiasbynens/dotfiles).
