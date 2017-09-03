---
categories:
    - technology
tags:
    - macOS
    - coding
comments: false
date: 2013-03-07T00:00:00Z
title: Configuring Homebrew in a Multi-User Setup
aliases: /2013/03/configuring-homebrew-in-a-multi-user-setup/
---

My MacBook Pro is setup with two user accounts: one for personal and one for work. This is certainly not my setup of choice, but if I want to use my own MBP (which is retina) at work then I have to abide by this rule.

Anyway, this setup caused an issue when I went to do something that required Homebrew. After a little research and testing [Leif Hanack had the best answer][1]. All it requires is a group that both users are members and then change group permissions on `/usr/local`. While I have not done so myself, this methodology should work on other items (i.e., iTunes library) I wish both accounts to have access.

 [1]: http://blog.strug.de/2012/06/my-homebrew-multi-user-setup/ "My Homebrew Multi User Setup"