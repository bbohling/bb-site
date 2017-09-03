---
categories:
    - technology
date: 2011-03-06T00:00:00Z
tags:
    - technology
    - journal
title: Text File Revolution
aliases: 
    - /2011/03/Text-File-Revolution/
    - /technology/Text-File-Revolution/
---

I am like any other technologist (ok, geek) out there...I love tinkering with new stuff[^fn-1]. For the most part I wouldn't change this about me; it generates intense passion in my daily life as well as serving me well in my career. However, there are certainly pitfalls I inevitably fall into time and time again. The most prevalent is my constant tinkering with my online presence.

## A Brief History of My Online Life

Since 1995 I have had some sort of website. In those 16 years there were easily 40+ different websites I either hand-coded or used some sort of publishing/blogging software or framework. To name a few: [WordPress][wpress], [Blogger][blogger], [TypePad][tpad], [Movable Type][mt], [Drupal][], [ExpressionEngine][ee], [Joomla][], [CodeIgniter][ignite], and [CakePHP][cake]. Just [look at the complexity of my online life][online-life] a year ago[^fn-2].

## And the Point Is...

Today we are consuming **and generating** huge amounts of digital information. Some[^fn-3] have made careers from this fairly recent phenomenon. Yet when I went to look for ways to *optimize* my online presence there still was no easy answer. 

`<StartRant>`
I am tired of losing HUGE amounts of my digital content due to the information being in data stores I either had little or no control over. Patrick Rhone discusses this very topic on an episode of [Enough: Beware of Information Silos][silo]. I admit I am to blame for exponentially making it worse for myself by changing software every 6-12 months. Those that stick with just WordPress or any other publishing software are not as bad off, but how boring is that!?
`</StartRant>`

So I started looking at alternatives to Wordpress, [Posterous][], [Tumblr][] and the likes. Don't get me wrong, those solutions are fantastic for many uses cases, but they will not work for me on my main content: thoughtful writing and thoughtful photography. What does that exactly mean? Any content that I feel has a longer shelf life than a tweet or snapshot. This meaningful (at least to me) content I need to [ensure I own][b2cy]. For all the other *stuff* I will continue to use Posterous ([bbohling.com][]) and [Twitter][] ([ebohling][twit-ebohling]). Thus, my number one requirement:

>Full control over my content: a) capture content in a timeless format and b) display content in a lightweight and elegant fashion.

## Text File Revolution

Enter my *Text File Revolution*. I decided to go old school: text files. What format is easier to track, backup, and view than text files? One of the best data stores in my opinion. Obviously I am not the only one with this opinion with the huge increase of text editors, especially on iOS devices. Looking at my iPad and iPhone I have the following text editors:

* [PlainText][]
* [WriteRoom][wr]
* [Elements][]
* [iA Writer][writer]
* [Nebulous Notes][nebnotes]
* [DraftPad][]
* [MarkDownNote][]

And with [Dropbox][] and [Notational Velocity][nv] (specifically Brett Terpstra's fork, [nvALT][]) I can sync all the text files between my iOS devices and all my Macs. **Capture content in a timeless format: check.**

Now the harder part, taking those text files and turning them into a lightweight and elegant web site. Honestly, I started with WordPress and after a full weekend of futzing with themes and plugins I had a (fragile) solution. Fortunately, I quickly learned how fragile when just a few days later WordPress 3.1 came out and I upgraded. Everything broke. True, the theme designer quickly released a fix, but it made me realize how little control I had with my solution. My tech friend, Josh Bancroft, realizes this as well if you one of his recent posts on his [simplified WordPress installation][josh]. In my opinion WordPress is still overkill for a want. 

## HTML for Men

What is more lightweight than pure HTML? There is certainly a reason that myself and other webheads stopped creating HTML web sites back in 1999...they are a complete pain to maintain. The largest site of pure HTML files I maintained was 400+ pages back in 2000 for a computer reseller...not fun. I remember in 1998 working with a buddy to create an engine that took content from text files and it generated a static, HTML web site. That's what I want now! After some research sure enough there are a handful of static site generators:

* [Jekyll][]
* [nanoc][]
* [StaticMatic][]
* [webgen][]
* [static][]
* [Webby][]
* [hyde][]

Not wanting to spend a ton of time researching all the possibilities I looked to the web authors I read (and who they read) and noticed a few used Jekyll:

* [Tom Preston-Werner][tom] (co-founder GitHub, creator Gravatar, creator Jekyll)
* [Alex Payne][apayne] (Twitter engineer, BankSimple co-founder)
* [Henrik Nyh][nyh] (The Pug Automatic)

Whoa, awesome...now we're getting somewhere! **Display content in a lightweight and elegant fashion: check.**

## Jekyll: Where the grass is green (mostly)

I have only been working with Jekyll for about 16 hours so far and while I am extremely excited about this new direction I am taking, I can't recommend many people following me. I'll have a future post on the extreme technical nature of Jekyll. It is definitely not for those that don't like to get their hands dirty...extremely dirty. I haven't spent this much time in [Terminal][] for a long time. However, once I got everything setup and automated it is a snap. 

## Conclusion

Below is a snippet of the text file that I used to create this blog post. The text file consists of a very simple syntax called [Markdown][] created by John Gruber. It is a wonderful syntax that is hugely supported, but even if Markdown disappeared tomorrow my content is in basic text files that I own and manage.

![Text File Revolution](/uploads/2011/03/TextFiles.jpg "Sample Blog Post (Text File) using Markdown Syntax")

It may seem silly to most, but I feel like a huge weight has been lifted from my shoulders. I finally feel on the right path to not only simplifying my online presence but also controlling it. But I'm a tinkerer, so I'm sure I will have much more to say on the topic soon.

[^fn-1]: Stuff = gadgets, programming languages, software, operating systems, and any other *butterfly* that catches my eye.
[^fn-2]: Need I point out the irony that the link is to another one of my websites?
[^fn-3]: To name a few: [Becoming Minimalist][bmini], [Zen Habits][zen], and [Minimal Mac][minimac]. 

[wpress]: http://wordpress.org "Wordpress - both free and priceless at the same time"
[bbohling.com]: http://bbohling.com "Brandon Bohling on Posterous"
[blogger]: http://www.blogger.com "Blogger"
[tpad]: http://www.typepad.com/ "TypePad - great blogs start here"
[mt]: http://www.movabletype.org/ "Movable Type - a professional publishing platform"
[drupal]: http://drupal.org/ "Drupal"
[ee]: http://expressionengine.com "ExpressionEngine - the choice of top designers and web professionals"
[joomla]: http://www.joomla.org/ "Joomla"
[ignite]: http://codeigniter.com/ "CodeIgniter - Open source PHP web application framework"
[cake]: http://cakephp.org/ "CakePHP - the rapid development PHP framework"
[online-life]: http://bbohling.com/my-online-presence-revisited "My Online Presence Revisited"
[bmini]: http://www.becomingminimalist.com/ "Becoming Minimalist"
[zen]: http://zenhabits.net/ "Zen Habits"
[minimac]: http://minimalmac.com/ "Minimal Mac"
[silo]: http://minimalmac.com/post/2925165892/enough-beware-of-information-silos "Enough - Beware of Information Silos"
[posterous]: http://posterous.com "Posterous"
[tumblr]: http://tumblr.com "Tumblr"
[twitter]: http://twitter.com "Twitter"
[b2cy]: http://www.b2cy.com/social-media/who-needs-website-when-have-facebook "Who Needs A Website When You Have Facebook?"
[draftpad]: http://modelessdesign.com/draftpad/ "DraftPad - simple notepad which is like a single sheet of paper"
[elements]: http://www.secondgearsoftware.com/elements/ "Elements"
[writer]: http://www.informationarchitects.jp/en/writer-for-ipad/ "iA Writer"
[markdownnote]: http://www.codingrobots.com/markdownnote/ "MarkDownNote - Markdown editor for the iPad"
[nebnotes]: http://nebulousapps.net/notes.html "Nebulous Notes"
[plaintext]: http://www.hogbaysoftware.com/products/plaintext "PlainText - Dropbox text editing"
[wr]: http://www.hogbaysoftware.com/products/writeroom "WriteRoom - distraction free writing"
[dropbox]: http://dropbox.com "Dropbox"
[nv]: http://notational.net/ "Notational Velocity"
[nvALT]: http://brettterpstra.com/project/nvalt/ "nvALT - Brett Terpstra's Notational Velocity fork"
[josh]: http://www.tinyscreenfuls.com/2011/02/plugins-i-used-in-the-feb-2011-tinyscreenfuls-com-redesign/ "Plugins I Used in the Feb. 2011 TinyScreenfuls.com Redesign"
[nanoc]: http://nanoc.stoneship.org/ "nanoc"
[staticmatic]: http://staticmatic.rubyforge.org/ "StaticMatic - static websites, the modern way"
[webgen]: http://webgen.rubyforge.org/ "webgen"
[static]: http://static.newqdev.com/ "static"
[webby]: http://webby.rubyforge.org/ "Webby"
[hyde]: http://ringce.com/hyde "hyde"
[jekyll]: http://jekyllrb.com/ "Jekyll - transform your text into a monster"
[tom]: http://tom.preston-werner.com/ "Tom Preston-Werner"
[apayne]: http://al3x.net/ "Alex Payne"
[nyh]: http://henrik.nyh.se/ "Henrik Nyh"
[twit-ebohling]: http://twitter.com/ebohling "Brandon Bohling on Twitter"
[terminal]: http://en.wikipedia.org/wiki/Apple_Terminal "Terminal an OSX command line interface"
[markdown]: http://daringfireball.net/projects/markdown/ "John Gruber - markdown"


