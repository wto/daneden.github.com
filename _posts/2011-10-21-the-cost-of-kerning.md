---
layout: post
title: The Cost of Kerning
tags:
- Code
- Design
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_focuskw: ''
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  yourls_tweeted: '1'
  yourls_shorturl: http://drwys.so/1q
  dsq_thread_id: '457550309'
---
CSS3 brought with it a whole variety of typographic properties, to give web designers some of the type control we've long been dreaming of. One such property was the <code>text-rendering</code> property. This essentially gave web designers the option to add kerning and ligatures to their sites using OpenType fonts. I was so pleased with the addition of this property, I wrote <a href="http://adamwhitcroft.com/baseline/posts/better-typography-with-css3-experimental-features/">a post for the Baseline Project</a> praising it.

However, this exciting new feature has lost it's fluffy appeal since I first discovered it, and I'm banishing it from my designs. Here's the low-down.

[caption id="attachment_529" align="aligncenter" width="286" caption="Sexy sexy ligatures and kerning. But at what cost?"]<img class="size-full wp-image-529 " title="textrendering" src="http://daneden.me/wp-content/uploads/2011/08/textrendering.png" alt="" width="286" height="150" />[/caption]

The first thing I noticed was a problem with highlighting text. When you drag the cursor over a kerned pair of letters (in this case, "T" and "e"), the kerning is deactivated. This causes the surrounding letters to shift out of place and looks pretty weird.

[caption id="attachment_901" align="aligncenter" width="223" caption="Selecting kerned pairs causing weird behaviour"]<img class="size-full wp-image-901" title="Side Effect" src="http://daneden.me/wp-content/uploads/2011/10/sideeffect.gif" alt="" width="223" height="94" />[/caption]

The next no-no the property got was in Chrome on Windows XP. For some reason, when using web fonts in conjunction with <code>text-rendering: optimizeLegibility</code>, Chrome on XP screwed up all the characters. I talked to Typekit about the issue, and they told me it was down to the CSS property. Upon removing it, it was as good as new.

[caption id="attachment_903" align="aligncenter" width="406" caption="The herp derp in question, seen here on Owlr"]<a href="http://owlr.me"><img class="size-full wp-image-903" title="text-rendering on Chrome XP" src="http://daneden.me/wp-content/uploads/2011/10/18_10_11_21_49_14.png" alt="" width="406" height="195" /></a>[/caption]

The final straw came on Chromium on Linux distributions. When using <code>text-rendering: optimizeLegibility</code> on this browser, inline elements are given a strange negative margin. This is most likely down to the way that the kerning is done, but either way, it looks just awful.

[caption id="attachment_904" align="aligncenter" width="436" caption="The final straw - Chromium struggles with optimizeLegibility"]<img class="size-full wp-image-904" title="failbuntu" src="http://daneden.me/wp-content/uploads/2011/10/failbuntu.png" alt="" width="436" height="149" />[/caption]

I think it's safe to say that <code>text-rendering</code> is still a very experimental property. Kerning and ligatures are great, but not at the expense of... well, this. Plus, Firefox takes a pretty good approach - it'll use kerning and ligatures where ever it can, unless you specify otherwise by using the optimizeSpeed value. Hopefully more browsers will take the same approach in the future.
