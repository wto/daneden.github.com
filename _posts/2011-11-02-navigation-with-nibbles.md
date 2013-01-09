---
layout: post
title: Navigation with "nibbles"
tags:
- Code
- Design
- Development
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
  yourls_shorturl: http://drwys.so/1w
  dsq_thread_id: '459916485'
---
Something I've come across a few times on the web recently is a feature I like to call "Navigation with nibbles". Let me show you what I mean:

[caption id="attachment_943" align="aligncenter" width="1054" caption="Navigation nibbles, here seen on Themble and Simplebits"]<a href="http://daneden.me/wp-content/uploads/2011/11/banner.png"><img class="size-full wp-image-943" title="Navigation with nibbles" src="http://daneden.me/wp-content/uploads/2011/11/banner.png" alt="Navigation with nibbles" /></a>[/caption]

When I talk about nibbles, I'm in fact referring to those little snippets of information between each page title. I <em>love</em> this technique - it provides the user with a little piece of additional information about what to expect on the following page. It's simple and effective.

However, something I noticed about this little feature is that web designers are all doing it the same way - they're writing their nibbles in spans or other ambiguous markup in order to style it differently. And at the end of the day, it's not really a part of the link, and not really a part of the important content. So what can we do? Use pseudo elements, of course!

<!--more-->The theory is very simple. Keep your markup lean, with only the <em>actual</em> content between the anchor tags. Then use an attribute to insert the nibble of information about the page. While you could use the title attribute, for this example I'm going to use a data attribute.
<pre class="prettyprint">&lt;a href="/about" title="About" data-description="Learn a little more about me"&gt;About&lt;/a&gt;</pre>
Awesome. Lean, clean, and semantic. But how do we get that nibble to appear along with our link? Enter the pseudo element.
<pre class="prettyprint">a[href="/about"]:after {
    content: attr(data-description);
    display: block;
    font-size: .75em;
    line-height: 1.1;
    color: #999;
}</pre>
How easy was that? After this CSS (plus a little extra), you could end up with something like this:

<a href="http://daneden.me/wp-content/uploads/2011/11/mockup.png"><img class="aligncenter size-full wp-image-944" title="Pseudo elements are fun!" src="http://daneden.me/wp-content/uploads/2011/11/mockup.png" alt="" width="575" height="148" /></a>You might prefer to have your nibbles right in the markup, but if you ask me, this is a better solution.
