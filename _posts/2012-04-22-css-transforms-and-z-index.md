---
layout: post
title: CSS Transforms And z-index
tags:
- Code
- Development
- Geeky
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
  dsq_thread_id: '659696584'
  _yoast_wpseo_linkdex: '0'
---
Not too long ago, someone pointed out <a href="https://github.com/daneden/animate.css/issues/25">an issue</a> with Animate.css. In short, they were experiencing issues with animations causing the <code>z-index</code> of pseudo elements to get screwed up.

Now, we all know that CSS transformations mess up elements with <code>position: fixed;</code>, as it states in the CSS specification:
<blockquote>"Any value other than ‘none’ for the transform results in the creation of both a stacking context and a containing block. The object acts as a containing block for fixed positioned descendants." (<a href="http://www.w3.org/TR/css3-2d-transforms/">http://www.w3.org/TR/css3-2d-transforms/</a>)</blockquote>
But I'd always sort of overlooked that part about the stacking context, assuming from prior experience that it was talking more about affecting child elements than pseudo elements. This issue on Github made me stop in my tracks to get my head round it a little bit.

Like it says in the spec, any transformation value other than "none" creates a new stacking context. If, like me, the phrase "stacking context" confused the heck out of you, it basically means that z-index gets screwed up. To see what I'm talking about, here's a <a href="http://dabblet.com/gist/2463684">quick demo.</a>
<h2>What's it to you?</h2>
This is kind of a big deal. Pseudo elements are great for things like creating faux paper stacks and other neat effects - a lot of which rely on z-index. If you're animating those elements (with, for example, Animate.css) then you're gonna be pretty pissed to find it messing with the result of your neatly-written CSS. It sucks.

I might be overreacting, but it's put a big hole in my work on Animate.css. So I'll be working hard on a solution. As it stands, there's no known hack or fix for this issue (quite right, too - hacks are messy, and this isn't a bug so there shouldn't have to be a fix) but I can go ahead and swap out transformations for properties like left, top, right, etc. These properties don't affect the document flow, but do affect the overflow area - which is exactly how CSS transformations work anyway. Transformations like scale and rotate will still be the same, unfortunately. But these changes ought to fix the vast majority of entrance and exit animations in Animate.css.
