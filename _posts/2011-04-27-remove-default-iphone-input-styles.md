---
layout: post
title: Remove default iPhone input styles
tags:
- Development
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  yourls_tweeted: '1'
  yourls_shorturl: http://drwys.so/s
  views: '188'
  dsq_thread_id: '457896200'
---
I recently did an overhaul of the comments section for my site, making it much more pretty - particularly for the iPhone. I was pretty happy with the overhaul - except for one thing.

Mobile safari (and perhaps the Android browser, too) has some default styles for buttons and inputs - it takes the font, color, background color and everything into account, then applies these default styles on top of them. The result is somewhere in between the desired effect and the real default appearance - it's not very pretty.

I asked the people of twitter for assitance with this, but no one knew the answer. Luckily, after some research, I found the solution - it looks like this:
<pre class="prettyprint">-webkit-appearance: none;</pre>
This magical little phrase tells webkit browsers not apply any default styles to elements (only the ones you declare it on, mind - I declared it on everything using <code>* { -webkit-appearance: none; }</code>) and is pretty useful if you've got some custom styles on buttons and the like - particularly for web applications.

<!--more-->

For those of you who like to see this kind of thing in action, here's a picture of how it looks in real life:

<a href="http://daneden.me/wp-content/uploads/2011/04/comparison.png"><img class="aligncenter size-full wp-image-416" title="comparison" src="http://daneden.me/wp-content/uploads/2011/04/comparison.png" alt="Comparison of default webkit styles vs no defaults on the iPhone" width="792" height="818" /></a>
