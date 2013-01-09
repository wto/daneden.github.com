---
layout: post
title: CSS font smoothing
tags:
- Code
- Development
- Geeky
status: publish
type: post
published: true
meta:
  yourls_shorturl: http://drwys.so/c
  _edit_last: '1'
  dsq_thread_id: '458574134'
  _wp_old_slug: ''
  views: '159'
  _yoast_wpseo_redirect: ''
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_focuskw: ''
---
One of the things I find really helps a web design or UI design really stand out is some simple font smoothing. All the fonts in Mac OSX are smoothed beautifully, as well as Ubuntu. As for Windows, well, at least they give the option.

There are many ways to achieve smoother fonts in web design, and I'll show you just a couple I've seen.
<!--more-->
 My personal favourite is using a simple text-shadow in CSS. Let's assume your page has a white background color, so a white text-shadow with 1 pixel blur will give us a nice invisible shadow, acting as a smoother.

<pre class="prettyprint lang-css">* {
     text-shadow: 0 1px 1px rgba(255,255,255,.3);
}
</pre>

This works fine, but won't work if the background changes color from white. You end up with a sort of pressed style, which is nice, but for just achieving smoothness it's maybe not the best way. Another way is using the webkit-only font-smoothing property. Unfortunately, this property is only supported in Webkit browsers (Safari &amp; Chrome) and only effects Mac OS X.

<pre class="prettyprint lang-css">body {
     -webkit-font-smoothing: antialiased;
     font-smoothing: antialiased;
}
</pre>

Both these options have their advantages and disadvantages, and at the end of the day its really down to the users computer. Like I said, I go for the text shadow for it's compatibility and the fact it's a single line of code.

As it stands, <code>font-smoothing</code> is only available in Webkit browsers and has no place in any web standards. But it's still pretty nice.
