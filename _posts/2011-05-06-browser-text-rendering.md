---
layout: post
title: Browser text rendering
tags:
- Development
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  yourls_tweeted: '1'
  yourls_shorturl: http://drwys.so/x
  views: '356'
  dsq_thread_id: '457550183'
---
I'd say that when it comes to cross-browser compatibility, my site is as good as gold. The custom fonts work across every browser, including IE, media queries make it usable on mobile devices and small screens, and there are fallbacks for things that might not be supported in all browsers (here's looking at you, Microsoft). But there are some things that just can't be fixed.

I recently stumbled upon a <a title="Forrst post - &quot;Firefox 4 font-face typo too bold!&quot;" href="http://forr.st/~9xj" target="_blank">post</a> on Forrst by <a href="https://twitter.com/#!/juliuskoroll" target="_blank">@juliuskoroll</a>, saying something like this:
<blockquote>Hey guys, I implemented some fonts for blog.desiign.de and its way too bold in Firefox 4... The picture shows Firefox 4 compared to Chrome.</blockquote>
If you look at the picture, he's right. There is a significant difference in the font weight between browsers. I jumped the gun a little bit and replied:
<blockquote>This is usually just because of the way different browsers render text - safari renders text significantly bolder than chrome. Might be worth checking out the font-smoothing css property (with vendor prefixes) and setting the font-weight to 100 - some browsers, even when the font itself won't go down to that weight, will try to simulate it.</blockquote>
Theoretically, this is all true; but I'm not one to leave things up to theory. There's something similar going on with my website, too, so I decided to try and put an end to it.

<!--more-->

[caption id="attachment_424" align="aligncenter" width="1116" caption="The differences between text rendering across Chrome, Safari and Firefox can be seen here"]<a href="http://daneden.me/wp-content/uploads/2011/05/textrendering.png"><img class="size-full wp-image-424" title="Text Rendering Differences" src="http://daneden.me/wp-content/uploads/2011/05/textrendering.png" alt="The differences between text rendering across Chrome, Safari and Firefox" width="1116" height="554" /></a>[/caption]

As you can see, Webkit deals with it all very nicely (Chrome and Safari) and they're almost identical in their text rendering - a slight difference in the letter widths, but nothing worth panicing over (it should also be noted that Mobile Safari renders text significantly thicker than desktop browsers - no doubt this is Apple's way of 'helping' users read the text on such a small screen).

Firefox, however, throws a bit of a wobbly - it makes it significantly more bulky. While this might be more helpful to some users, it hinders cross-platform compatibility somewhat, and frankly I don't like the idea of Firefox messing with the font I chose because of it's weight and readability.

It could be down to the font files themselves - Firefox will use the .ttf font file, whilst the most recent versions of Chrome and Safari will opt for SVG fonts. But I can't imagine the font files being that significantly different from one another - font designers tend to be a bit fussy about these sorts of details. So I'm pretty sure it's the rendering engine thats doing this, which could be difficult to fix.

One of the things I suggested to @juliuskoroll was to set the font-weight to 100 - this explicitly tells the browser to render the text at it's thinnest weight. For fonts without a 'thin' style, the browser would simulate it where possible.
<pre class="prettyprint">* { font-weight: 100; }</pre>
This did make a difference, but unfortunately (and as I had expected), the change was made across all browsers - not just firefox. It turns out (and I think this should <em>maybe </em>be a standard feature in CSS) that you can't attach vendor prefixes to standard CSS rules, such as <code>-moz-font-weight</code>, so that wasn't an option either.

The only other way around this problem that I can see is to have the page detect what browser is being used with Javascript, then attach a class to the body (like "foxy"), and set styles in CSS like so:
<pre class="prettyprint">.foxy { font-weight: 100; }
.foxy h1, .foxy h2, .foxy h3, .foxy h4, .foxy h5, .foxy h6 { font-weight: 400; /* 400 is the 'normal' font weight - which is pretty bold in Firefox! */ }</pre>
It's not ideal, and it's certainly not necessary (I know I won't be going to this much effort), but it's nice to know that there is a way to fix this problem if we really have to.
