---
layout: post
title: A non-scientific box-shadow experiment
tags:
- Code
- Design
- Development
- Geeky
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
  yourls_shorturl: http://drwys.so/24
  dsq_thread_id: '476133528'
---
I've been doing a fair bit of mobile work at the moment, which has led to a lot of deep thought into how I write my CSS and how best to optimize it all for mobile devices. Recently, I came across <a href="http://nerds.airbnb.com/box-shadows-are-expensive-to-paint">an article</a> demonstrating that CSS box-shadow can seriously impede page rendering performance. I dismissed it almost immediately, because I'd had experience of this first-hand. I found out the hard way a few months back, when applying a pretty large box shadow to a pretty large element lead to a pretty dramatic drop in performance when doing things like scrolling down the page. Eventually, I used a trust old image instead.

But browsers have come a long way since then; we've got things like hardware acceleration and whatnot. So, unlike the article mentioned above, I'm going to do a series of <em>non-scientific</em>&nbsp;experiments with box-shadow. I'm not measuring numbers, I'm measuring the performance of the page by how a user will - how it <em>feels</em>.

<!--more-->Let's take a look at our test page. It basically consists of 3 200px tall divs, each with a box shadow applied to them. Here's our first test:

<iframe style="width: 100%; height: 300px;" src="http://jsfiddle.net/CWgCK/1/embedded/result,html,css/" frameborder="0" width="320" height="240"></iframe>

Go ahead and give it a scroll. Not bad huh? I found that this first test performs just fine on all the supported browsers - IE9, Safari, Chrome, Firefox and Opera. Nothing to report.

For test number two, let's swap the <code>#000</code> color declaration for an <code>rgba(0,0,0,.6)</code>. Why? I read somewhere that browsers have a little more trouble rendering <code>rgba</code> than HEX colors. Don't hold me to that though. This isn't science.

<iframe style="width: 100%; height: 300px;" src="http://jsfiddle.net/CWgCK/2/embedded/result,html,css/" frameborder="0" width="320" height="240"></iframe>

Once again, performance is just fine. It's a little bit choppier in Opera, but nothing to worry about. For test number three, we'll increase the box-shadow blur radius to a whopping 1000px. It's unlikely that your <code>box-shadow</code> will ever need to have a 1000px blur radius, but by some kind of logic I'm making up on the spot, it's about the same as a 100px blur radius on a div that's 20000px long. That's another insane number of pixels, but what if you had an insanely long article, with an insanely long thread of comments? Or <code>box-shadow</code>s applied to a bunch of divs loaded via infinite scrolling, like seen on Tumblr? Extreme times call for extreme measures, people.

<iframe style="width: 100%; height: 300px;" src="http://jsfiddle.net/CWgCK/3/embedded/result,html,css/" frameborder="0" width="320" height="240"></iframe>

Now it's getting interesting. Performance wise, all the browsers suffer. IE9 is actually the most impressive, with considerably less lag when scrolling than the others. Firefox is by far the worst in this test, and Safari and Chrome are starting to suffer. But the most bizarre find in this test is in Opera - performance is surprisingly good, but we now have scrollbars. It seems that Opera will render large box shadows in a way that affects the layout of the page. Hopefully, the Opera team already knows about this, but I'll be submitting a report nonetheless.

We'll call this next test number 3.5, because it's exactly the same as number three, with the addition of one thing - a 3D transformation for Webkit browsers. Why's that? Well, by default, hardware acceleration is turned <em>off</em> in Safari and Chrome. By adding a 3D property, we'll be turning it on.

<iframe style="width: 100%; height: 300px;" src="http://jsfiddle.net/CWgCK/4/embedded/result,html,css/" frameborder="0" width="320" height="240"></iframe>

As expected, Safari and Chrome got a performance boost, both now scrolling significantly better. However, using this 3D transform results in pretty weird looking text in Safari. As a workaround, simply add the <code>-webkit-font-smoothing: antialiased;</code> rule to the CSS.

Now on to test number four. For this test, we'll use the same box-shadow as number three, but we'll apply it three more times. Again, it's unlikely in a real world situation, but multiple box shadows are commonplace these days, so we ought to account for the possibility.

<iframe style="width: 100%; height: 300px;" src="http://jsfiddle.net/CWgCK/5/embedded/result,html,css/" frameborder="0" width="320" height="240"></iframe>

Chrome gets a huge drop in performance, and Firefox becomes completely useless. Opera scrolls smoothly, but still has that strange layout issue. The victor in this test is Internet Explorer, which still scrolls very well. Safari is choppy, but much better than Chrome.
<h2>So, what does this all boil down to?</h2>
Well, for one thing, browsers are a lot better at this stuff than they were a few months ago. We also know that Opera will render large box shadows in a way that affects the page overflow, Internet Explorer still has a few tricks up it's sleeve, Safari's slow Javascript performance is rectified by it's excellent CSS3 support, and finally, hardware acceleration really does make a big difference. But don't forget that these tests were performed on a desktop computer, not a mobile device. The performance would probably drop to about 10% on mobile devices, which you should bear in mind.

Avoid large box shadows, enable hardware acceleration, and try to avoid transparency by opting for a solid color where possible.
