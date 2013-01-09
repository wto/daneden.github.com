---
layout: post
title: Optimising animations and transitions
tags:
- Code
- Design
- Development
status: publish
type: post
published: true
meta:
  dsq_thread_id: '620485483'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_title: ''
  _edit_last: '1'
  _yoast_wpseo_focuskw: ''
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  _yoast_wpseo_linkdex: '0'
---
If you spend enough time with CSS transitions and animations, you start to notice some odd quirks. I've had a few emails from people using <a href="http://daneden.me/animate">Animate.css</a> in their websites and experiencing some of these issues - most frequently, odd changes in text rendering during animations. I'll go over just a few tips for optimising CSS transitions and animations to make them smoother and bug-free.

<!--more--><h2>Flash of aliased text</h2>
When transforming an element with a transition, you might notice the text on the page appearing thinner and smoother for the duration of the transition in Webkit browsers. You can check a demo of what I mean <a href="http://dabblet.com/gist/2157388">here.</a> What's happening here is that during the animation, 3D hardware acceleration is turned on, meaning that the browser applies antialiasing to the text. Once the transition is completed, this hardware acceleration is switched off again, returning the text to it's normal rendering weight. There are a couple of fixes available.

The first one is for Webkit browsers only, but since this problem only appears to affect Webkit browsers, that's OK. Simply apply <code>-webkit-font-smoothing: antialiased;</code> to the html or body element. This permanently switches on the hardware acceleration and antialiasing for the text. Check <a href="http://dabblet.com/gist/2157424">the demo</a> again, and you'll see that the bug is fixed. There are a couple of fairly minor problems with this fix; for one, it only works in Webkit. But as I already mentioned, this bug is only present in Webkit browsers as far as I know anyway. The other problem is that the antialiasing applied to the text may be undesirable in places. Personally, I think it looks great, but it's not everybody's cup of tea.

<h3>Cross-browser fix</h3>
There is a fix for the antialiasing bug that would work across all browsers, should the bug become apparent in non-webkit browsers. It involves applying a 3d transformation to the html or body element, turning on hardware acceleration. <a href="http://dabblet.com/gist/2157436">Check out this demo.</a>

<h2>Realistic movement</h2>
In the real world, when something moves, it doesn't travel in a linear way. It accelerates and decelerates smoothly, so it makes sense to try to attain this more natural movement in our web design. As a general rule, I avoid using a <code>linear</code> timing function for transitions and animations - it's very unrealistic, and feels quite forced. <code>ease</code> is a much nicer timing function, but still feels a little artificial. My personal favorite timing function isn't in the defined functions.

<pre class="prettyprint">-prefix-transition-timing-function: cubic-bezier(0.770, 0.000, 0.175, 1.000);</pre>

It might be a little speedy for most people, but I love it. Check out this handy tool for testing and writing your own timing functions, <a href="http://matthewlein.com/ceaser/">Ceaser.</a>

<h2>Some final notes</h2>
Just a couple more things to bear in mind when it comes to animations, transitions, and transformations.

<ul>
    <li>Applying <code>transform</code> to a fixed position element will reset its position to <code>static.</code> To get over this problem in animations, you could set the last keyframe to <code>-prefix-transform: none;</code></li>
    <li>Android devices (on versions below 4.0) won't animate or transition more than one CSS property. But <a href="http://daneden.me/2011/12/putting-up-with-androids-bullshit/" title="Dispelling the Android CSS animation myths">you knew that</a> already.</li>
    <li>Don't go <a href="http://daneden.me/labs/lolimate">overboard</a> on your transitions or animations.</li>
</ul>

If I've missed anything out, got anything wrong, or you have anything to add, I'd love to know. Comment below, <a href="http://twitter.com/_dte">tweet me</a>, or <a href="mailto:dan.eden@me.com">email me.</a>
