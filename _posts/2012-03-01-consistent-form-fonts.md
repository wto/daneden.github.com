---
layout: post
title: Consistent Form Fonts
tags:
- Code
- Design
- Development
status: publish
type: post
published: true
meta:
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_focuskw: ''
  _edit_last: '1'
  dsq_thread_id: '594643239'
  _yoast_wpseo_linkdex: '0'
---
It's not very often I write something code-oriented these days, but this is a gem from the archives of <a href="http://www.komodomedia.com/blog/2006/10/css-trickery-part-5-inheritance/">Rogie King's blog</a> I simply had to share.

If, like me, using a full-on reset or normalizing stylesheet makes you feel dirty and wrong, you probably stick with something really simple like this:

<pre class="prettyprint">* {
    margin: 0;
    padding: 0;
}

html, body {
    font: 100%/1.5 Helvetica Neue, Helvetica, Arial, sans-serif;
}</pre>

That's about as complex as my reset gets. But then you drop a form into your HTML document, and things start to go a little bit west. Inputs and textareas will get the browser's default style for form elements, and pick a new font family, size and line-height to go with it. Yikes. Chaos!

But fear not; Rogie has the solution.

<pre class="prettyprint">input, textarea, select {
    font-size: inherit;
    font-family: inherit;
    line-height: inherit;
}</pre>

It turns out that by default, form elements don't inherit the declared font values. Heck, even <a href="http://meyerweb.com/eric/tools/css/reset/">Eric Meyer's reset</a> doesn't provide consistent form fonts.

I think the strange thing about Rogie's article on this is that it's six years old - but this is the first time I've found an explanation and fix for the issue.
