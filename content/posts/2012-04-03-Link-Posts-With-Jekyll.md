---
categories:
    - technology
date: 2012-04-03T00:00:00Z
link: http://tuananh.us/articles/posting-link-post-in-jekyll.html
published: true
tags:
    - blogging
title: Link Posts with Jekyll
aliases: /technology/link/Link-Posts-With-Jekyll/
---

Now that I have [Jekyll publishing automated][auto], why not do link posts? For one, Jekyll does not support link posts out of the box. However, Tuan Anh figured out how to tweak Jekyll to support link posts: [Posting Link Post in Jekyll by Tuan Anh Tran][link].

This is the code I used to modify my post.html file (in the _layouts directory):


```
{% if page.link %}
<h2><a href=”{{ page.link }}">{{ page.title }}</a></h2>
{% else %}
<h2> {{ page.title }} </h2>
{% endif %}
```


**NOTE**: I had to use `page.link` where Tuan Anh used: `page.post-link` (in [their code][gist]).

Unfortunately, clicking the title on the homepage still goes to a permalink on my site. It is not until one visits the actual, individual (link) post when the title is hyperlinked to the source. This is due to Jekyll not knowing the internals of any post when generating the homepage. Still, I thank Tuan Anh for the tip and will use it often!

[auto]: /2012/03/Automating-Jekyll/ "Automating Jekyll by Brandon Bohling"
[link]: http://tuananh.us/articles/posting-link-post-in-jekyll.html "Posting Link Post in Jekyll - Tuan Anh Tran"
[gist]: https://gist.github.com/1569797 "Code to enable link posting in Jekyll by Tuan Anh Tran"
