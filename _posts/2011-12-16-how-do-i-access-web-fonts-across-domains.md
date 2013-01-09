---
layout: post
title: How do I access web fonts across domains?
tags:
- Code
- Development
- Q and A
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_focuskw: ''
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  dsq_thread_id: '506948611'
---
This little number was one that <a href="http://twitter.com/michaelw90">Michael</a> and I encountered while we were building <a href="http://owlr.me">Owlr.</a> We store Owlr's assets - that's the images, CSS and JS powering it - on a subdomain of Owlr (a.owlr.me). During testing, it was discovered that Firefox didn't manage to get the web fonts we were using to display icons. At first we dismissed it, since we were aiming Owlr at mobile devices rather than desktops. But, Michael was a stubborn sod about it, so we did some digging around.

<!--more-->It turns out that fonts served from an alternative domain won't be served for Firefox because of security issues. To get around it, you need to serve the fonts from their origin server with an <code>Access-Control-Allow-Origin</code>. This is as easy as adding it to the <code>.htaccess</code> for the same directory as the fonts. Here's the code:
<pre class="prettyprint">#This line will only allow access from http://foo.example
Access-Control-Allow-Origin: http://foo.example

#Whereas this line will allow access from any domain
Access-Control-Allow-Origin: *</pre>
There's a little bit more information about this over in <a href="https://developer.mozilla.org/En/HTTP_access_control">Mozilla's documentation.</a>
