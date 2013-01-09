---
layout: post
title: Faux borders & columns
tags:
- Code
- Design
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  _yoast_wpseo_focuskw: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  yourls_shorturl: http://drwys.so/1g
  views: '200'
  yourls_tweeted: '1'
  art_direction_single: ! "<style type=\"text/css\" media=\"screen\">\r\nbody { background:
    #215d8c url('http://daneden.me/wp-content/uploads/2011/09/grid.png') !important;
    color: #fff; }\r\n#main, .container, #footer { background: transparent; }\r\n#header
    {\r\n-webkit-box-shadow: 0 2px 2px rgba(0,0,0,.2);\r\n-moz-box-shadow: 0 2px 2px
    rgba(0,0,0,.2);\r\n-o-box-shadow: 0 2px 2px rgba(0,0,0,.2);\r\nbox-shadow: 0 2px
    2px rgba(0,0,0,.2);\r\n}\r\n.post p.wp-caption-text { color: #eee; color: rgba(255,255,255,.6);
    }\r\n#footer { background: rgba(0,0,0,.7); }\r\na { color: #fff; border-bottom:
    1px dotted #fff; }\r\n#footer a { border-bottom: 0; }\r\nh3 { color: #fff; border-bottom:
    1px solid #fff; }\r\n.post_header time:before, .post_header time:after { background:
    #fff !important; }\r\na:hover, .comment-meta a { color: #c93; text-decoration:
    none !important; }\r\n#sidebar, .commentsheader { color: #fff; }\r\n.postid-#postid
    h1.post_title {\r\ncontent: url('http://daneden.me/wp-content/uploads/2011/09/faux.png');\r\n}\r\n.post_header
    time {\r\n    color: #fff;\r\n}\r\ncode { color: #c93; }\r\n</style>"
  dsq_thread_id: '460754260'
---
Columns are an important tool in web design - almost every single website you've ever used probably has columns of some description. Usually, they're based upon a larger grid system, which the designer uses to calculate how wide elements should be across the site.

The trouble is, what if you want to divide these columns up visually? You could use CSS borders, but then you'd be at risk of breaking the grid. Single pixel values can result in huge and undesirable consequences - not to mention the fact that it wouldn't work on a flexible layout. So instead of going through our layouts &amp; frameworks and modeling for cases where we need to allow for padding and borders, let's see what fancy CSS stuff we can do to achieve column divisions, without breaking the grid.

<!--more-->For this demo, I'll be using my own framework, <a href="http://daneden.me/toast/">Toast</a>.  The syntax in use is especially for toast, but the rules should still work the same way for other grid systems and frameworks.
<h3>Dan Cederholm's "faux column" effect</h3>
This is an oldie, but a goodie. Dan suggests using a background image based on percentage values of your website. Let's say you have a layout with 2 columns. They meet at 75% of the page's width. So in this instance, you'd create a <strong>huge</strong> document which has a column division at the same 75% value. Then, position this image on the background of the container at 75%. You're probably starting to see a pattern here.

Huzzah! You've made a couple of faux columns that are fully flexible, and it'll play nicely with your fluid website. It's the same technique I currently use on this site.

[caption id="attachment_734" align="alignleft" width="406" caption="Broken column is broken"]<a href="http://daneden.me/wp-content/uploads/2011/09/borken.png"><img class="size-full wp-image-734" title="Broken faux column" src="http://daneden.me/wp-content/uploads/2011/09/borken.png" alt="" width="406" height="247" /></a>[/caption]

However, there are a few drawbacks with this technique - for instance, it behaves slightly weirdly at very narrow widths. Additionally, and quite annoyingly, if you want to change the colors at all, you have to create a new image.

Another annoying problem with this is that if the user chooses to apply the image to a generic container, if they wanted to have a single column (rather than two) on a page, then it'll still display the background image. No good!
<h3>The box-shadow technique</h3>
This is the first approach that came to mind when I was thinking about the common problems with Dan's faux column effect. By applying two negatively positioned box shadows to the sidebar, you could create a vertical rule that divides the two. For example:
<pre class="prettyprint">#sidebar {
	-webkit-box-shadow: -23px 0 0 #fff, -24px 0 0 #bbb;
	-moz-box-shadow: -23px 0 0 #fff, -24px 0 0 #bbb;
	-o-box-shadow: -23px 0 0 #fff, -24px 0 0 #bbb;
	box-shadow: -23px 0 0 #fff, -24px 0 0 #bbb;
}</pre>
This code is based on the assumption that there is a gutter of approximately 48px between each column. What this gives us is a single pixel line with no real width - so it doesn't break the grid.

But, as is with most things, this technique comes with a host of problems. The first and most blatantly obvious one is that the support for CSS box shadows isn't all that great. (ahem... Internet Explorer) It's also important to remember that this technique works under the assumption that there's a white background - it won't work for transparent backgrounds. It'll simply display a big, grey block.
<h3>The pseudo element solution</h3>
So, back to the drawing board. We know we want the solution to be flexible, easy to change and work with transparency. Lucky for us, there is a way for us to get all these things.

Using a <code>:before</code> pseudo element, we can give the sidebar a non-obtrusive division that won't break the grid, and it has fairly decent support across browsers.

Here's the code:
<pre class="prettyprint">#content {
	position: relative;
}

#content:before {
	content: ".";
	height: 100%;
	display: block;
	position: absolute;
	width: 1px;
	background: #bbb;
	text-indent: -9999px;
	left: 76.5%;
	top: 0;
	z-index: -1;
}</pre>
And there you have it. The element is actually applied to the sidebar's container - but that way, we can have the division span the entire height of the container, giving a faux column effect like the one demonstrated in example one! To give true faux columns, adjust the width of the element.

I've thrown together a <a title="Faux columns and borders - demo page" href="http://daneden.me/labs/columns">demo page</a> with some of the pros and cons of each of these techniques. Feel free to download, share or modify it to your will!
