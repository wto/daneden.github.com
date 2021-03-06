---
layout: post
title: A half-built grid is a dead grid
tags:
- Code
- Design
- Geeky
- Personal
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
  yourls_shorturl: http://drwys.so/1r
  dsq_thread_id: '457550312'
---
I recently remembered a relatively new redesign of my <a href="http://ntu.ac.uk">University's</a> website. Memories of a well structured grid were conjured in my mind, and I got all dizzy thinking that I'd been looking at this site without noticing it's excellent design. To my dismay, when I checked the site, it featured nothing but the carcass of a half-built grid.

Throughout a few elements on the home page, there appeared to be some sort of order and consistency - but it was just that. A faint echo between the odd element, and nothing more. The widths of elements were pulled out of thin air until they summed up to something close to the full width of the container.

Worse still, upon closer inspection I discovered some disturbing source code. The 'header' (as it appears on the site) is actually written <strong>after</strong> the content in the markup. Whether this is justified by an argument in accessibility is hard to believe. I can certainly see the logic of it, but it just doesn't make sense.

The main navigation uses a single <code>&lt;ul></code> for each item. That's right. Not an <code>&lt;li></code>, a <code>&lt;ul></code>. The links themselves were anchors, nested in list items, listed in an unordered list, for each item. Class names are non-semantic. Things like 'leftColumn' and 'whiteLink' are everywhere. In short, it's a little bit of a mess.

Now I understand that a website as large as this, with as much content as it has, (and most likely a CMS that's generating a lot of the code) it's going to be hard to keep everything trim. But someone designed this thing, and didn't do a great job. It's a shame. What I think it a bigger shame is that the redesign wasn't documented. I'd love nothing more than to listen to the design decisions made behind the scenes, what was going on in the designer's head throughout the process - but until that happens, I can only assume that the designer was at as much of a loss as I am now.

When I redesign a website, I think long and hard about everything that goes into it. I can spend hours working out pixel-precise measurements to acheive exactly what I want. I could justify the most minute of design decisions on sites such as my own and <a href="http://brills.me">Brills</a>, and if I couldn't I'd be outright about it. I expect the same from other web designers. No decision should be made without justification.

I'm not here to make an attempt at redesigning it myself. It would take a long time, and I've more important things to do. I also realise that the topic has taken something of a tangent from it's title - but the core argument remains the same. The grid on <a href="http://ntu.ac.uk">ntu.ac.uk</a> is broken for no reason. It was poorly executed, and that's a great shame.
