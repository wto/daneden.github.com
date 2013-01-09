---
layout: post
title: Improving the CSS framework
tags:
- Code
- Design
- Development
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  yourls_tweeted: '1'
  yourls_shorturl: http://drwys.so/17
  views: '656'
  _yoast_wpseo_focuskw: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  dsq_thread_id: '457550204'
---
A good CSS framework is one of the most useful tools a web designer can have on their computer. I certainly know that without Andy Taylor's CSS Grid, this website would have taken at least double the amount of time to set up as it has done. That's not to say they don't come with their own issues and problems. Each of the frameworks I've seen has drawbacks, but I think I know how to get over two of the main ones.<!--more-->
<h2>Removing the <code>.last</code> and <code>.omega</code></h2>
A fair number of these frameworks, namely <a title="Columnal CSS grid" href="http://www.columnal.com/#markupcode">Columnal</a> and <a title="CSS Grid System" href="http://cssgrid.net">CSS Grid</a> require that once you've put the last module of a row in, you add the class value of <code>last</code> to it. Now, I don't know about you, but I tend to forget things like this, and then spend about an hour yelling at the screen, wondering why everything looks off.

What this class does, in the case of Columnal and CSS Grid, is remove the right hand margin of the last module, so that it doesn't fall on the next line because it's run out of room. But frankly, it's not very semantic, and also not very designer-friendly, to have to remember to add this class.

This is where <code>:last-child</code> comes to the rescue! Let's get right in to the code.
<pre class="prettyprint">.row :last-child { // note the space between .row and :last-child - this makes sure that it selects the last child element in the row, regardless of what it is. For specificity, you could say .onecol:last-child, .twocol:last-child etc
    margin-right: 0;
    }</pre>
This says exactly the same thing - take away the right hand margin on the last element of the row - without the messy markup. Awesome! But what's that? IE7 doesn't support <code>:last-child</code>? I guess you're right.

But fear not, there is a fix for that too! Using <a title="IE7.js" href="http://code.google.com/p/ie7-js/">this</a> rather fantastic and far-too-clever script, you can tell old versions of IE to behave the same way as more modern browsers. It even includes a transparent .png fix! I chose the IE9 version of the script, so IE versions 5.5 through to 8 will behave like IE9 and recognise the <code>:last-child</code> selector.

It really is that simple!
<h2>The float clearing problem</h2>
Another problem with the CSS frameworks of today is that they make heavy use of floats. <a title="The 960 grid system" href="http://960.gs">960.gs</a> and a few other frameworks require that before ending each row, you should put an empty <code>div</code> in there with the class value of <code>clear</code>, or something to that effect. This is <em>even worse</em> than cluttered class names - you're littering the DOM with empty and non-semantic content! Yikes!

Luckily, <a title="SimpleBits" href="http://simplebits.com">Dan Cederholm</a> has just the fix - and it's a damn good one! Lets say you have a row containing your modules, with a clearing <code>div</code> afterwards. Take that shameful clearfix out, and add this rule to your row's CSS.
<pre class="prettyprint">.row:after {
    content: ".";
    display: block;
    height: 0;
    clear: both;
    visibility: hidden;
    }</pre>
This creates a pseudo element that clears all the floats before it, without littering your markup! It's this kind of stuff that makes me do a happy dance in my chair.

But wait, once again IE doesn't support this kind of CSS trickery! Luckily, Dan is one step ahead of IE and has a fix for that too.
<pre class="prettyprint">* html .row { // IE6
    height: 1%
    }

*:first-child+html .row { // IE7
    min-height: 1px;
    }</pre>
That's it. Once again, it really is that simple.

I'm not saying that the creators of the frameworks have done a bad job, far from it - their contributions to the web designing community are extraordinary and save many people a lot of time. But if you're a little bit obsessed with the semantics of your site, and hate using clearfixing <code>div</code>'s all over your markup, then this is a simple solution for you.
