---
layout: post
title: How I write CSS
tags:
- Code
- Design
- Development
- Geeky
- Personal
status: publish
type: post
published: true
meta:
  _yoast_wpseo_linkdex: '0'
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
  recommended-listening: <a href="http://rd.io/x/QUTcaDcgq6w" title="Fairlight by
    Com Truise on Rdio">Com Truise - &ldquo;Fairlight&rdquo;</a>
  dsq_thread_id: '718242582'
---
I find it quite difficult to fully document my particular style of writing code. I point the blame for this problem on a constant state of learning that infects me daily. Something I wrote yesterday would make me raise an eyebrow today, and something I wrote months ago would make me feel a little sick. "How foolish of me!" I'd mutter from my seat, before remembering I'm in a public place and noticing the judging eyes of the public gaze upon me. I'm rambling.

Here I'll try to  explain the way I write my code (CSS, really. Since it's all I'm good at.) and why I choose to write it that way.

<!--more-->

<h2>Organisation of selectors/sections</h2>
This is usually the first thing that I consider when I sit down to write my CSS. The structure of the overall file. The table of contents, if you will. Nothing particularly out of the ordinary about the typical structure I choose for <em>single page sites</em>:

<ol>
<li>Contents, copyright, meta, etc in a commented block</li>
<li>Reset (more often than not, a simple <code>* { margin: 0; padding: 0; }</code>)</li>
<li>Base styles (<code>html</code>, <code>body</code>, <code>p</code>, etc)</li>
<li>Significant elements in order of appearance</li>
<li>Media queries</li>
<li>Animations</li>
</ol>

Of course, this structure wouldn't work for sites with a large number of pages and components, for which the structure is closer to this:

<ol>
<li>Contents, copyright, meta, etc in a commented block</li>
<li>Reset (more often than not, a simple <code>* { margin: 0; padding: 0; }</code>)</li>
<li>Simple abstractions for navigation, boxed off content</li>
<li>Base styles and shared styles/colors (<code>html</code>, <code>body</code>, <code>p</code>, etc)</li>
<li>Other components ordered by whatever the heck I feel like, grouped with their own corresponding media queries and animations</li>
</ol>

I'm also starting to write my CSS comments like my git commits - often and explicit. In some of my latest work, you'll find comments every 2 or three lines, often explaining even the simplest things. I'm sort of adopting a <a href="http://en.wikipedia.org/wiki/Rubber_duck_debugging">rubber duckie coding</a> approach. This habit has grown from the realisation that I open up code a few months after I originally authored it, and <a href="http://bukk.it/wtafnnn.gif">wonder what the heck I was thinking.</a>

<h2>Organisation of declarations</h2>
This is a tough one. A lot of people order their declarations by their relationship to one another. Grouping box model stuff together, fonts, colors etc. But there's a lot of overlap there - does <code>border</code> belong in colors, or box model? Does <code>color</code> belong in fonts? <code>line-height</code> can affect layout, so shouldn't that be with the box model? All of this is too much for my puny brain to handle, and I know if I tried to stick to a system, I'd end up with code riddled with inconsistencies.

So, what about alphabetical order? That makes sense, right? Right. But it's incredibly difficult to maintain. (Maybe difficult isn't the right word - it requires a lot of discipline.) So I order my declarations in the order that they occur to me in my head.

As I'm writing the CSS for a component, I'll talk to myself (or a rubber duckie, if there happens to be one within arm's reach) and go through the process. Let's imagine I'm making a button. So I'd start with a selector like <code>.butt</code> because it makes sense and it makes me chuckle. I'll want to give it padding. I'll play around with the padding for a while, then I'll settle and move on. What next? Background. A lovely blue color. Maybe stick a gradient on there. But yikes, now the text looks awful. Change the color. Remove <code>text-decoration</code>. Make it bolder. We're getting there. Add some rounded corners. This is pretty close to how our IE users will experience it. Looking good! Now for the polish. <code>box-shadow</code>, <code>text-shadow</code>, and maybe a <code>-webkit-mask-image</code> and <code>mask</code> since I'm pretty obsessed with them at the moment. And there we have our button.

Letting my mind flow between these steps and not worrying about the organisation of my CSS means I get things done a lot faster. And I tend not to fill my selectors with too many declarations, so if I need to make a change or add another property, it's not too much hassle.

<h2>Prefixes</h2>
The only other issue with organisation of CSS I can think of is how we include prefixed properties. Since we're all an impatient bunch, we want to try the latest bleeding edge CSS properties as soon as our browsers will allow us. I write mine by order of length, and add indents to line values up. Here's an example:

<pre class=prettyprint>.butt {
    background: -webkit-linear-gradient(#012,#234);
    background:    -moz-linear-gradient(#012,#234);
    background:     -ms-linear-gradient(#012,#234);
    background:      -o-linear-gradient(#012,#234);
    background:         linear-gradient(#012,#234);
}</pre>

While we're on the subject, will everyone <a href="http://daneden.me/2012/05/preprocessors/">stop faffing around</a> with preprocessors and realise it took me all of 10 seconds to write those prefixes? I don't mean that, actually. Do what you like. I'll just be grumbling in the corner.

<h2>Final thoughts</h2>
Some last things. Don't treat this as a guide. It's just my way of saying "this is what I do". It's the sort of thing that I find very useful, and I know that those who are learning CSS may find useful themselves. I don't write in a consistent enough style to create any kind of guide for my own writing style. It changes every day. But isn't that how it is with all of us?

I can't remember the last time I made an IE-only stylesheet. In fact, I can't remember the last time I declared any IE-only style of any kind except inline-block hacks. If you're writing extra CSS exclusively for fixing IE quirks, or any other browser quirks, you should probably consider how well formed your CSS is in the first place. IE doesn't support all the frills of the new crop, but it's still a (somewhat) standards-compliant browser. If you find a bug, it can almost definitely be fixed in a standards-friendly way, without the use of any magic numbers or IE hacks. Just bear that in mind. That's all I ask. Everything else in this post you can dismiss as codswallop.
