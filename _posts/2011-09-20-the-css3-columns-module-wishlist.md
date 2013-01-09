---
layout: post
title: The CSS3 Columns Module Wishlist
tags:
- Code
- Design
- Development
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
  yourls_shorturl: http://drwys.so/1k
  views: '163'
  yourls_tweeted: '1'
  dsq_thread_id: '458567991'
---
During the recent redesign of the website, I've been working closely with the CSS3 columns module. I've grown something of a love-hate relationship with it. When it's given a huge amount of content, it can work great. If the sections are clearly and evenly divided up, images don't cut into the article too much &amp; attachments maintain <em>most</em> of the vertical rhythm, then the columns can be a lovely addition to help the flow and division of content.

However, things aren't quite as wishy-washy as that. When it drills down to it, the columns module is not all that well-implemented by the current crop of browsers. I'm not saying it's an easy task, but no one has got it quite right yet. I've created a tag for my site called 'span_all'. The purpose of this tag is to tell the browser "Don't turn this into columns - it's too short!". Short of creating a custom post type, which involved more PHP than I'd care to indulge in, this was my only option.

<!--more-->

Here goes a short list of things I'd quite like to see included in the CSS3 columns module, with names as technical as I could muster:
<ul>
	<li><strong>Column selectors</strong> - I think something like <code>nth-column()</code> would be great. Sometimes you end up with odd vertical alignment on the columns, and it'd be useful to make corrections such as <code>nth-column(2) { padding-top: .2em; }</code></li>
	<li><strong><code>column-height</code></strong> - I imagine this would work the same way <code>column-width</code> does, wherein the column is at least as tall as the column-height value. This would help prevent columns when the content is too short</li>
	<li><strong><code>column-break-after</code></strong> - it would be incredibly useful to be able to define rules about column breaks. For example, you might want columns <em>never</em> to break before an image, and always break after instead. I think it would work like this: <code>column-break-after: img, blockquote;</code></li>
</ul>
I think that even with just these three features, I'd be able to make a lot more use of the columns module, and it would unlock a lot more real-world potential for web design. What would you like to see added to the module?
