---
layout: post
title: Changing My Ways
tags:
- Code
- Development
- Geeky
- Personal
- Work
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  _yoast_wpseo_linkdex: '0'
  _thumbnail_id: '1534'
  _yoast_wpseo_focuskw: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  dsq_thread_id: '851619773'
---
<small><strong>Note:</strong> this post isn't supposed to serve as a tutorial. There are much smarter folks who'd do a better job at tutorials than me. Think of this as a log of my experiences.</small>

I've always developed websites in a very similar (and bush-league) workflow. Develop locally for a short time, then quite quickly stick the site on a remote server via FTP, and continue to edit live on the private remote server.

If you're still reading this, I know you're very, very mad at me. That's a silly, dangerous, and irresponsible way to work. But I'm here to tell you that I'm a changed man. And if you work like that right now, by the time you finish reading this post, maybe you will be as well. <!--more-->

<h2>Git with the times</h2>
Over the last couple of weeks, I've been fine-tuning my workflow to include the <a href="http://git-scm.com">Git SCM</a> system. I've been meaning to include Git in my workflow for some time. Having used it with great success for projects like <a href="http://daneden.me/animate">Animate.css</a>, <a href="http://daneden.me/toast">Toast</a>, <a href="http://basehold.it">Basehold.it</a>, and <a href="http://github.com/daneden">more</a>, I thought it would make sense to start version-controlling my own website as well as future client work.

Before I could get Git involved, I had to get a local environment set up for testing and developing my website on. Luckily, <a href="https://twitter.com/lukejones">Luke Jones</a> has a great <a href="http://www.lukejones.me/articles/set-up-a-local-server-on-os-x/">tutorial</a> on setting up a local server on Mac OS X <em>without</em> using MAMP or other third-party software. This is great for a ton of reasons:

<ul>
<li>I don't have to worry about starting up any apps when I want to do some local development</li>
<li>MAMP isn't cluttering my already too-full dock</li>
<li>I also don't have to troubleshoot things when MAMP goes wrong (which is a lot of the time)</li>
<li>It gives me an excuse to open Terminal and look like a genius</li>
</ul>

Without MAMP, however, we don't get PHPMyAdmin. That's not the end of the world though, and there's actually a fantastic MySQL app called <a href="http://www.sequelpro.com">Sequel Pro</a> that can be downloaded for free. It's much more powerful, pretty, and less confusing that PHPMyAdmin.

Once I'd finished setting up the server, it was just a case of dropping the current contents of my website onto my iMac for local development. Well, it's not quite that simple.

<h2>WordPress Woes</h2>
I'm a huge fan of WordPress. However, one thing that does drive me crazy is moving from a local environment to a remote server and vice versa. Usually, I end up settling for completely different installations on both local and remote, with only the theme being the same. It's a pain. Without content, it can be difficult to design efficiently. All this is mainly because there's only one <code>wp-config.php</code> file - only one place to define your database connection. Too many times have I uploaded my local <code>wp-config.php</code> to my remote server by accident, overriding my database connection to a non-existent one.

Luckily, there's a trick you can use to have one connection locally, and another on the remote server. On your local machine, create a copy of <code>wp-config.php</code> and give it the name <code>wp-config-local.php</code>. Put your local database connection credentials in there. Now, make the following changes to <code>wp-config.php</code>:

<pre class=prettyprint>&lt;?php
if ( file_exists( dirname( __FILE__ ) . '/wp-config-local.php' ) ) {
    require_once dirname(__FILE__) . '/wp-config-local.php';
} else {
    /* Put your remote/original wp-config here */
}</pre>

Then, when you upload your site back to the remote server, just be sure not to include <code>wp-config-local.php</code>. Neat, right?

One last thing to do on our local environment. We don't want to download all the uploaded media, so we should request it from the production server. To do that, we need a <code>.htaccess</code> file inside <code>/wp-content/uploads/</code> that looks like this:

<pre class=prettyprint># Attempt to load files from production if they're not in our local version
&lt;IfModule mod_rewrite.c>
  RewriteEngine on
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteRule (.*) http://daneden.me/wp-content/uploads/$1
&lt;/IfModule></pre>

<h2>Back to Git</h2>
Let's bring this back to the main topic: Git. Now, I'm a huge fan of GitHub, so many of the following steps are oriented around how GitHub works - however, the same basic principle applies to many other SCM hosts such as Beanstalk and Codebase.

The first thing I did was create a new private repository on GitHub. If you're a student, GitHub will give you a <a href="https://github.com/edu">free "micro" plan</a>. After I'd created the repo, I wrote up a <code>.gitignore</code> file with all the files I didn't want uploading. Mine looks like this:

<pre class=prettyprint># Exclude these files from the git repo
wp-content/cache/*
wp-content/plugins/wp-minify/cache/*
wp-content/upgrade/*
wp-content/uploads/*
sitemap.*
wp-config-local.php
 
# Hidden system files
*.DS_Store
*Thumbs.DB
 
# Include these files in previously blocked directories
!wp-content/uploads/.htaccess</pre>

Next, I added the GitHub repo as a remote origin on my local machine, added all my files, and pushed to the remote repo. My website is now on GitHub. Hooray! But how could I get anything I push to GitHub to then go to my remote server?

<h2>Remote control</h2>
This is where things start to get cool. On the remote server in the root of my site, I initialised a Git repository with <code>git init</code>. Then I added the GitHub repository as a remote origin. At this stage, the three copies of the website are identical, except for <code>wp-config-local.php</code> since it's in the <code>.gitignore</code> file.

I created a PHP file in the root of the site with the contents:

<pre class=prettyprint>&lt;?php `git pull`;</pre>

While those look like single quotes, they're actually backticks. This tells the server to execute the contents as if they were entered on a command line. The final step was to point to this PHP script as a WebHook URL in the repository settings on GitHub.

That URL is hit every time you push to the repository, meaning any updates I make on my local machine are pushed to GitHub, then immediately pulled onto my live server.

Pretty. Freakin'. Awesome.

<h2>Wrapping Up</h2>
I'm sure there are better tutorials on all this, and almost certainly smarter ways of doing it, but I'm just glad I'm no longer working with FTP. I'm working on implementing this workflow with many of my existing web projects, and with future projects too. Hopefully this was of some use to some people - I'd love to hear your thoughts.
