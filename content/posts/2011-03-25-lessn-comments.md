---
categories:
    - technology
date: 2011-03-25T00:00:00Z
tags:
    - technology
    - utility
title: Lessn and Comments
aliases: 
    - /2011/03/lessn-comments/
    - /technology/lessn-comments/
---

I really like how [Jon Hicks handles comments][hicksdesign] on Hicksdesign. Instead of allowing direct comments on his blog he provides a link that pre-populates a tweet. I'm not a fan of blog comments and many agree. [Alex Payne states why best][alex]:

> For most sites, though, comments are worse than useless. The anonymity of the Internet inspires hit-and-run attacks, unintelligible ramblings, and truckloads of spam.

So I wanted to implement a similar feature on this site. This lead me down a path of some additional work...

## Lessn (and Lessn More)

Since I didn't really want to force people to use a full URL like, [http://brandonbohling.com/2011/03/25/lessn-comments/][fullurl], I decided to use a URL shortener. Of course, I could use one of the many URL shortener services out there like [bit.ly][bitly] or [droplr][], which I have many times in the past...for my website though I wanted something more personal **and** in my control. Thus, I turned to Shaun Inman's URL shortener, [Lessn][]. It took only a few minutes to setup after I purchased a new domain, brndn.me. I soon realized though Shaun did not provide an easy way to track usage or even list out the URLs I had shortened. A quick Google search later I came across Alan Hogan's Lessn fork, [Lessn More][lessnmore]. A couple minutes later I had the perfect solution. Now I had a shorter URL that people could use to reference my web site. So now, [http://brandonbohling.com/2011/03/25/lessn-comments][fullurl] can be referenced using [http://brndn.me/5][shorturl]. If you own a domain and already have a hosting provider there's few reasons why you shouldn't setup Lessn More. Below are the 4 steps required directly from the README:

1. Open /-/config.php in a plaintext editor and create a Lessn username and password then enter your database connection details. You may also choose other settings such as authentication salts and a default home page.
2. For the shortest URLs possible, upload the contents of this directory to your domain's root public folder.
3. Visit http://doma.in/install.php to create the necessary database tables. (Watch for errors.)
4. Visit http://doma.in/-/ to log in & start using Lessn More! Be sure to grab the bookmarklets.

*Note: doma.in above should be replaced with your domain name.*

## Comments via Twitter

As I mentioned in [Text File Revolution][revolution] I am now using Jekyll to generate this web site. By default, it does not have a commenting solution. Some have chosen to integrate [disqus][], but I have chosen to go down another path and use Twitter. Honestly, the reason for this site is simply to provide me a writing outlet for myself so I don't want to clutter it with comments (or deal with the inevitable SPAM). However, I encourage others to comment via Twitter using a link at the bottom of each post[^fn-1], or better yet, create their own blog post providing their own point of view and referencing my post if appropriate. 


[^fn-1]: At this time I do not intend on adding a *Comment via Twitter* link on past posts.

[alex]: http://al3x.net/2009/02/24/why-no-comments-more-everything-buckets.html "Alex Payne"
[bitly]: http://bit.ly/ "URL shortener - bit.ly"
[disqus]: http://disqus.com/ "disqus - discover your community"
[droplr]: http://droplr.com "URL shortener - droplr"
[fullurl]: /2011/03/lessn-comments/ "Lessn and Comments - full URL"
[hicksdesign]: http://hicksdesign.co.uk/journal/truly-it-is-made-of-unicorns "Hicksdesign"
[lessn]: http://www.shauninman.com/archive/2009/08/17/less_n "Lessn by Shaun Inman"
[lessnmore]: https://github.com/alanhogan/lessnmore "Lessn More a Lessn fork by Alan Hogan"
[revolution]: http://brndn.me/4 "Text File Revolution by Brandon Bohling"
[shorturl]: http://brndn.me/5 "Lessn and Comments - short URL"
