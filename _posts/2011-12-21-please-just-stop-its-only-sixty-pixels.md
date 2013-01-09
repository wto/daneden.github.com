---
layout: post
title: Mobile designers are setting their houses on fire to keep warm
tags:
- Code
- Design
- Development
- Geeky
- Rants
status: publish
type: post
published: true
meta:
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_focuskw: ''
  dsq_thread_id: '511550524'
  _edit_last: '1'
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
---
If you've ever designed a website for mobiles devices - specifically, iPhone, Android and other smartphones - no doubt you'll have heard about the old <code>scrollTo</code> trick. The idea behind this sprinkle of JavaScript is to get rid of the web address bar seen at the top of a lot of mobile browsers. In it's simplest form, it's something like this:
<pre class="prettyprint">&lt;body onload="window.scrollTo(0,0);"&gt;</pre>
With this, the window will scroll a little once the page has loaded, thus hiding the address bar. Neato! It makes it more like an app, which is something clients and users alike enjoy and benefit from. But it's a little bit like setting your house on fire to keep warm. Let's dig in, shall we?

<!--more-->
<ul>
	<li><strong>Users don't care</strong> about those 60 pixels. If anything, they like them. They know that's how they get to other websites, or reload the page. They also know that they're in a web browser, not an app. Trying to hide that fact is pointless.</li>
	<li><strong>Users don't wait</strong> for a page to fully load before they start scrolling. This is even more true on mobile devices with slow connections. The number of times I've started scrolling a long web page before it's finished loading, only to be flipped straight back to the top once it's finished. When it came to Owlr, we added a listener to make sure we only used <code>scrollTo</code> if the user hadn't begun scrolling.</li>
	<li><strong>You need more than one rule</strong> for the wide variety of browsers. This will work for iOS devices, but then there's Androids, BlackBerry's and a bunch of other capable devices, too. Scott Jehl <a href="http://24ways.org/2011/raising-the-bar-on-mobile">outlines</a> a few handy techniques on 24ways, but you end up with 27 lines of JavaScript to hide 60 pixels. And that's without detection for user scroll.</li>
	<li><strong>It's not an app</strong> that you're building. It's a website. If you want your website to feel more like an app, then why not make it native - or make it <code>web-app-capable</code>. With that rule in place, the user wouldn't have a scrollbar anyway.</li>
</ul>
This isn't a dig at that 24ways article, or the author, or anyone else who uses this technique or similar techniques. I'm just hoping to make people who have been using this technique think twice about it. It's a little bit of OS chrome, to which the user is accustomed to and that doesn't take away all that much from the page itself.
