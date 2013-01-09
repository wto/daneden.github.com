---
layout: post
title: The Swiss Theme
tags:
- Design
- Personal
- Updates
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
  yourls_tweeted: '1'
  yourls_shorturl: http://drwys.so/1t
  dsq_thread_id: '457626817'
---
It's not very often I design something I'm completely happy with. Blog themes start to fall apart, especially with the addition of extra challenges, browser compatibility problems and shifts in content requirements. The Bringhurst theme was no exception. It suffered from awkward behavior in Firefox and a broken appearance after the addition of the ad module. Luckily, work on the next theme was well under way.

And here it is - the Swiss theme. Let's run through the stuff that makes it tick.
<h2><!--more-->The Grid</h2>
A digital frontier. At the heart of the Swiss theme is a carefully considered grid. It's based on the 130px fixed width of the advertisement module. This is the first time I've ever had a predefined width with which to work from, and I can tell you, it was a <em>huge</em> help. Whenever I had to think up a width for an element, it was a simple case of using the grid based around this fixed module. The navigation labels echo the width most significantly.

With the Bringhurst theme, I was convinced that the vertical rhythm and horizontal alignment should be as close to each other as possible. Generous margins were based on the 24px baseline. This time, the horizontal and vertical spacing were considered separately. This, again, made things much easier.
<h2>Pixel Precision</h2>
I know what you're thinking when you check out the CSS for this theme - I know I told you all to <a href="http://forrst.com/posts/Stop_using_pixels-vy1">stop using pixels</a>. But this is a little different.

The argument in that post was based entirely on my experiences with pixel-precision when it came to typography. The differences in text rendering and the rounding of decimal em measurements were causing me stress in the typographic qualities of my designs. This theme is placing more emphasis on the layout than anything else. Readability is still a priority, but the effective layout of content is a much more important objective. That's why I'm contradicting myself.
<h2>Less CSS</h2>
I've long been avoiding LESS and SASS as design tools. For those who don't know what they are, they're sort of like an extended syntax for CSS, allowing variables, mixins and functions. You can learn all about LESS <a href="http://lesscss.org/">here</a>.

The reason I've been avoiding them is because, generally speaking, they rely on external scripts of software to process and get served up to the browser. I'm no fan of anything that relies on technology that might not be native or enabled on every browser. However, I took the plunge for this project and used LESS to write my CSS.

Instead of having it compiled on load, I compiled the LESS code locally and uploaded the CSS file to the server. The result of working this way has been pretty good - the color scheme of the site will change every now and then, and this is made super easy by the LESS variables. It also means that rather than having to manually enter variations of colors such as lighter and darker, I can just have LESS calculate those variations for me. Easy rollover states are easy.
<h2>The Future</h2>
As usual, I've pushed the theme live 'unfinished'. There are still a bunch of loose ends, things like 404 pages and archive pages that I haven't even touched. I get too excited and launch this stuff too early. But at the same time, it's continuing the "Design by committee" method that's worked so well up to now. If you run into anything that's bothering you on the site, let me know. It's always great to hear fresh ideas.
