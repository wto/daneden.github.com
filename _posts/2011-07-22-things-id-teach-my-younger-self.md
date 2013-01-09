---
layout: post
title: Things I'd teach my younger self
tags:
- Development
status: publish
type: post
published: true
meta:
  yourls_shorturl: http://drwys.so/15
  views: '188'
  yourls_tweeted: '1'
  _edit_last: '1'
  dsq_thread_id: '465674607'
---
Browsing around on <a href="http://forrst.com">Forrst</a> recently is like walking into a room filled with learner drivers - seems like all the latest members are just starting out learning HTML and CSS, and picking up some bad habits along the way.

There are a lot of things I'd like to teach my younger self as well as the people I'm watching learn HTML for the first time, but here are just a few of the basic rules that no one really tells you until it's too late:

<!--more-->
<ul>
	<li><strong>Inline styles are the devil</strong> - probably a little over the top, but generally speaking it's bad practice to use inline styles. This is things like <code>&lt;div style="margin: 0 auto;"&gt;</code>. The BBC even have a web style guide that tells you on almost every page never, ever, ever to use inline styles.</li>
	<li><strong>The <code>&lt;style&gt;</code> tag is the devil's friend too</strong> -  again, it's probably not as bad as I'm making out, but the style tags often found in the head tags of a HTML document should really be in an external CSS file, with a link to it like this:
<pre class="prettyprint">&lt;link rel="stylesheet" href="link/to/style.css" /&gt;</pre>
</li>
	<li><strong>Sometimes, images just don't make sense</strong> - now I've tried long and hard to recreate many, many image-like qualities in CSS - gradients, motion, text-shadow etc. I probably take things a little bit too far sometimes, but the main point I'm trying to make is that images are sometimes not the right thing to do. Colored blocks for example, and simple things like that, can be easily created in CSS, and are much more easily edited.</li>
	<li><strong>Indent, indent, indent</strong> - a particularly bad habit I had when I started learning HTML &amp; CSS was poor maintenance of my code - more specifically, indentation and hierarchy of code. Generally speaking, I start indenting my HTML code from the body tag, like so:
<pre class="prettyprint">&lt;html&gt;
&lt;head&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;div&gt;</pre>
</li>
	<li><strong>Always double check</strong> - something that I think I'll still be doing when I'm a real pro is checking my code with others - it's amazing to see what other people make of your code, pointing out all the gaping holes you've missed and bad habits or practices you've picked up along the way. Forrst is my particular tool for feedback.</li>
</ul>
For now, that's all I can think of. No doubt this list will get pretty long in the future, and I'll post any updates on twitter.
