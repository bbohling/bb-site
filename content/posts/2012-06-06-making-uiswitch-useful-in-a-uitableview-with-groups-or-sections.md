---
categories: technology
tags:
    - coding
    - iOS
date: 2012-06-06T00:00:00Z
title: Making UISwitch Useful in a UITableView with Groups or Sections
aliases: /technology/making-uiswitch-useful-in-a-uitableview-with-groups-or-sections/
---

I just had a [progasm][progasm][^fn-progasm]. I was creating a UITableView that had multiple groups with multiple rows in each group. Each row had a UISwitch. The intent was to update a price label every time a UISwitch value (on/off) changed. However, figuring out which row _and_ section, trigged the event was not straightforward. After doing some research it seemed like most people were using a hack where they would set the UISwitch tag property to the indexPath.row value. Fine-and-dandy for those with only one group or section, but what about poor me? After digging around some more I stumbled upon [this answer on stackoverflow][answer] (of course). So I created a UISwitch category that allowed me to create a property called optionIndexPath and with a few lines of code I have a very slick solution.

I am a newbie when it comes to iOS development so maybe this solution is obvious to most __or__ maybe this is an absolutely terrible solution, but until someone tells me otherwise...I think it rocks.

---

[^fn-progasm]: I can't believe I just used that word. I blame it on lack of sleep.

[progasm]: http://www.urbandictionary.com/define.php?term=Progasm "Definition of progasm"
[answer]: http://stackoverflow.com/a/5500525 "stackoverflow answer"
