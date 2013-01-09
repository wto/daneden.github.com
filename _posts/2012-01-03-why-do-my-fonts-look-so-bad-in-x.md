---
layout: post
title: Why do my fonts look so bad in X?
tags:
- Design
- Development
- Geeky
- Q and A
status: publish
type: post
published: true
meta:
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_focuskw: ''
  _edit_last: '1'
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  dsq_thread_id: '525310722'
---
<mark>I've answered this question at least a dozen times in various web communities, but mostly on Forrst. This particular answer is pulled directly from the most extensive answer to this question, which is <a href="http://forrst.com/posts/Why_do_my_fonts_look_so_bad_in_X-rzI">over on Forrst.</a></mark>

There's a lot of this question shooting around. We web designers spend hours working on a design in Photoshop, perfecting down to the last pixel. But when we convert the whole thing to HTML and CSS, we're let down by the inconsistent and poor text rendering that web browsers have to offer.

At this point, <a href="http://www.memedepot.com/uploads/1000/1148_1253230725640.jpg">our designer might give up hope,</a> stomp over to Forrst and ragepost about how crap Firefox's font rendering is. It seems as though this common behavior is spawned from a universal lack of understanding when it comes to the variety of font rendering techniques employed by the various Operating Systems and web browsers. Here, I'll try to shed some light on the why's, how's and <em>calm the heck down</em>'s with font rendering. This information has been collected mainly from personal experience and the clever folk over at <a href="http://typekit.com">Typekit.</a><!--more-->
<h2>A brief history of type</h2>
Let's go back a few decades, to the start of Adobe. In its early years, Adobe created a font rendering technique known as Postscript. Around the same time, Apple Computers Inc were creating a file format for fonts called Truetype. Truetype quickly became very popular, and is the most widely used font format on both Mac and PC. However, the companies needed ways to display the fonts as well as package them. Apple opted for Adobe's relatively underdeveloped Postscript, whereas Microsoft went their own way. Years later, Microsoft created Cleartype, the antialiasing software used in Windows XP, Vista and 7 (though Windows 8 features the much better DirectWrite).

What's important to take away in this brief history lesson is that Adobe's Postscript is much better suited for rendering large, bold text and emphasises curves in letterforms - whereas Microsoft's Cleartype and previous rendering techniques are better suited for small text, and emphasises legibility at small sizes.
<h2>What this means today</h2>
Since Adobe and Apple both use the same font rendering technique, there tends to be little difference between your mockups in Photoshop and the actual rendering in browsers. As for Windows, you'll find an often startling difference between mockup and markup.

Unfortunately, short of buying a Macintosh, there's not much that can be done to prevent this. The closest you'll get to your mockup is installing <a href="http://apple.com/safari">Safari</a>, which employs the same font rendering and antialiasing techniques as Mac OS (and therefore the same rendering as Adobe Photoshop).

Using <a href="http://typekit.com">Typekit</a> will actually get you very close as well - they manually hint all the fonts they serve, and serve them to Windows computers in Postscript format. <strong>What does that mean?</strong> The Cleartype rendering engine will ignore Postscript's rules (which is a good thing in this case) and serve the font as it was intended. Smoother curves on Windows. <a href="http://blog.typekit.com/2011/09/15/improved-windows-rendering-for-more-typekit-fonts/">(read more about that here)</a> Hooray!
<h2>Why none of this matters</h2>
You might dismiss this next sentence as codswallop - <em>but it really is OK for your mockup to look different from the real thing.</em> Your website is going to look different on every browser, on every operating system, every mobile device, television, computer screen, Playstation 3 and printer it'll be viewed on. You're going to have no control over how your website is consumed in the hands of other users. Their resolution, color calibration, font size and browser settings will vary wildly, and that's an important (and perfectly acceptable!) fact to remember at all times. If you're really fussed about your mockup looking different from the browser, you should <a href="http://daneden.me/2011/09/design-in-the-browser/">design in the browser.</a>
<h2>This doesn't really help me with my problem</h2>
If you think this post is a load of toss, or it doesn't help you at all, let me know. Leave a comment, or <a href="http://twitter.com/_dte">tweet me.</a> Also, take all this knowledge with a pinch of salt. I have no doubt that a lot of the things I've said can't be backed up with hard fact, or I've gotten my sources wrong. If you have something to catch me up on, let me know!
