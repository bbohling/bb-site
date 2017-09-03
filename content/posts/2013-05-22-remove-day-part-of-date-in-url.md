---
categories:
    - technology
tags:
    - coding
comments: false
date: 2013-05-22T00:00:00Z
published: true
title: Remove Day Part of Date in URL
aliases: /technology/remove-day-part-of-date-in-url/
---

Since everyone is talking about *shipping* these days tonight I took the plunge and released my modified blog on a new server. I have been dreading this day because a) the redesign is incomplete and b) there are so many steps in cleanly moving a domain between providers. Of course, immediately after "flipping the switch" I realized that my old website used URLs like `/2011/09/25/Ellie/`, but my new configuration was setup to use `/2011/09/Ellie/` (notice I no longer have a day in the URL). Crap.

No sweat, right? I knew .htaccess could handle such an easy task. The problem was (being an .htaccess novice) I did not know the exact syntax to use. Worse, all the samples I could find simply showed how to strip out the entire date, not just the day. Thankfully, I finally came across [this post][whew] where Alan Levine describes exactly what I needed to do in this paragraph:

> The first part instructs the web server to return a permanent redirect (301) to find anything that has the three numbered structure (e.g. yyyy/mm/dd/) and find all the stuff that comes after that (.*) – every set of patters in (…) corresponds to variables we can use in the result– $1 $2 $3 are the year, month, day respectively, and $4 is the string of the url we want to preserve.

Simply adding the line below in the .htaccess fixed the issue:

    RedirectMatch 301 /([0-9]+)/([0-9]+)/([0-9]+)/(.*)$ http://brandonbohling.com/$1/$2/$4

Like I said, "No sweat".

[whew]: http://cogdogblog.com/2012/11/20/permalink-magic/