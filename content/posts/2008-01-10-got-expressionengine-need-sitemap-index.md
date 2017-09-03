---
categories:
    - technology
date: 2008-01-10T00:00:00Z
tags:
    - technology
    - blogging
title: Got ExpressionEngine? Need a sitemap index?
aliases: 
    - /2008/01/got-expressionengine-need-sitemap-index/
    - /technology/got-expressionengine-need-sitemap-index/
---

If you have been developing web sites for a while you already
undoubtedly know [the importance of sitemaps][]. Most blog software,
such as [Wordpress][], provide plugins to [auto generate sitemaps][],
but I could not find one for [ExpressionEngine][] so I am here to
explain how to auto generate your own with ExpressionEngine.

To create a simple sitemap for a SINGLE blog in ExpressionEngine you can
follow the [instructions explained here][]. However, our site has
multiple blogs so I needed to use a [sitemap index][], which required a
bit more effort. First, I will summarize the steps.

1.  Create a sitemap for each blog.
2.  Create a sitemap-[blog-name].php (like sitemap-word.php) file for
    each blog in web root
3.  Create a sitemap.php file
4.  Update your .htaccess file if necessary
5.  Validate with Google webmaster tools

### Step 1: Create a sitemap template for each blog

In this step you need to create a template page for each blog. This page
generates a sitemap for a particular blog. The code I use is below.
Note: You will need to change the two variables to meet your
requirements. In addition, you need to change the loc tag to match the
URL to your blog.

```
{assign_variable:master_weblog_name="the_word"}{assign_variable:template_group_name="word"}
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9
	http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd"
	xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"> 
	<url> 
		<loc>http://ebohling.com/word/</loc> 
		<lastmod>{exp:stats}{last_entry_date format="%Y-%m-T;%H:%i:%s%Q"}{/exp:stats}</lastmod> 
		<changefreq>always</changefreq> 
		<priority>1.0</priority> 
	</url> 
	 {exp:weblog:entries weblog="{master_weblog_name}" limit="30" 
		disable="categories|custom_fields|member_data|pagination|trackbacks" rdf="off" dynamic="off" status="Open"} 
	 <url> 
		<loc>{title_permalink="{template_group_name}"}</loc> 
		<lastmod>{gmt_edit_date format='%Y-%m-T;%H:%i:%s%Q'}</lastmod> 
		<changefreq>weekly</changefreq> 
		<priority>0.8</priority> 
	 </url> 
	 {/exp:weblog:entries} 
	 {exp:weblog:entries weblog="{master_weblog_name}" offset="30" 
		limit="500" disable="categories|custom_fields|member_data|pagination|trackbacks" rdf="off" dynamic="off" status="Open"} 
	 <url> 
		<loc>{title_permalink="{template_group_name}"}</loc> 
		<lastmod>{gmt_edit_date format='%Y-%m-T;%H:%i:%s%Q'}</lastmod> 
		<changefreq>monthly</changefreq> 
		<priority>0.5</priority> 
	 </url> 
	 {/exp:weblog:entries} 
</urlset>
```

### Step 2: Create a PHP sitemap file for each blog

In this step you need to use an FTP client, web administration page, or
whatever you do to create files on your web server. In this case, you
will need to create some files in your site’s root directory (EE’s
installation directory). For me, that is public\_html.

You can use whatever naming convention you want, but I chose to use:
sitemap-[blog-name].php. So I created three files for my site:
sitemap-action.php, sitemap-word.php, sitemap-bryce.php. Each file will
contain code that looks like this:

    <?php 
    // Prevent content to be cached 
    header("Expires: Mon, 26 Jul 1997 05:00:00 GMT"); // Content was generated on past 
    header("Last-Modified: " . gmdate("D, d M Y H:i:s") . " GMT"); //Content is always modified 

    // Inform user agent that content is XML and is UTF-8 encoded 
    header('Content-type: text/xml; charset=UTF-8'); 

    // Read content from template and show it 
    @readfile ('http://ebohling.com/word/sitemap/'); 
    ?>

Note: you will need to change the readfile string to match the URL to
your sitemap in Step 1.

### Step 3: Create a sitemap.php file

Again, using the tool you used in Step 2, create a sitemap.php file and
use similar code as follows:

    <?php 
    // Prevent content to be cached 
    header("Expires: Mon, 26 Jul 1997 05:00:00 GMT"); // Content was generated on past 
    header("Last-Modified: " . gmdate("D, d M Y H:i:s") . " GMT"); //Content is always modified 

    // Inform user agent that content is XML and is UTF-8 encoded 
    header(&apos;Content-type: text/xml; charset=UTF-8&apos;); 

    echo "<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">";
    echo "<sitemap>";
    echo "<loc>http://ebohling.com/sitemap-action.php</loc>";
    echo "<lastmod>" . date(DATE_ATOM,mktime(0,0,0,10,3,1975)) . "</lastmod>";
    echo "</sitemap>";
    echo "<sitemap>";
    echo "<loc>http://ebohling.com/sitemap-word.php</loc>";
    echo "<lastmod>" . date(DATE_ATOM,mktime(0,0,0,10,3,1975)) . "</lastmod>";
    echo "</sitemap>";
    echo "</sitemapindex>";
    ?>

Make sure you the loc tags to match the URLs to your PHP sitemap files
that you created in Step 2.

### Step 4: Update your .htaccess file if necessary

If you are using an .htaccess file to remove index.php, then you will
need to update this file. There are many ways to implement this feature
as explained on [ExpressionEngine's wiki](http://expressionengine.com/wiki/Remove_index.php_From_URLs/ "ExpressionEngine wiki - Remove index.php from URL"),
so my sample code may not work for you. But with a little effort,
hopefully you will be able to apply the idea to your particular
implementation.

```
RewriteEngine On
RewriteCond $1 !^(galleries|css|images|corelib|themes|favicon.ico|robots.txt|index.php|phpinfo.php|sitemap.php|sitemap-word.php|sitemap-action.php) [NC]
RewriteRule ^(.*)$ /index.php?/$1 [L]
```

Note: corelib equates to ExpressionEngine's core library directory which you should have renamed on installation, so make sure you tweak accordingly. As well as your sitemap names.

### Step 5: Validate Sitemaps

First you will need to validate each of your sitemaps. I use the validation tool supplied by
[XML-Sitemaps](http://www.xml-sitemaps.com/validate-xml-sitemap.html "XML-Sitemap Validator").
The sitemaps you will need to validate are your sitemap-[blog-name].php (or whatever naming convention you used). So for me:
http://ebohling.com/sitemap-action.php, http://ebohling.com/sitemap-bryce.php, and http://ebohling.com/sitemap-word.php. This will not only validate that
your sitemap is well-formed, but also that your code in your PHP file and .htaccess file is up to snuff. If you simply want to validate the
sitemap you can first validate using your template URL. For me, http://ebohling.com/word/sitemap.

Unfortunately you CANNOT validate the sitemap index (http://ebohling.com/sitemap.php) using this tool. You will need to use
[Google's validtor](http://www.google.com/webmasters/tools/ "Google Webmaster Tools").

As you can see this wasn't exactly easy. Quite a few steps and a lot can go wrong at each step. Hopefully this will provide you a starting point
though and save you some time. Good luck!

[the importance of sitemaps]: http://www.google.com/support/webmasters/bin/answer.py?hl=en&answer=40318
    "Why should I have a sitemap"
[Wordpress]: http://wordpress.org/ "WordPress"
[auto generate sitemaps]: http://www.arnebrachhold.de/projects/wordpress-plugins/google-xml-sitemaps-generator/
    "Google (XML) Sitemaps Generator for WordPress"
[ExpressionEngine]: http://www.expressionengine.com
    "ExpressionEngine - the best CMS available"
[instructions explained here]: http://expressionengine.com/wiki/Google_Sitemaps/
    "Create a Google Sitemap for EE"
[sitemap index]: http://www.sitemaps.org/protocol.php#index
    "Sitemap Index format"