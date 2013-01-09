---
layout: post
title: The problem with Microsoft
tags:
- Code
- Development
status: publish
type: post
published: true
meta:
  dsq_thread_id: '457550132'
  yourls_tweeted: '1'
  _edit_last: '1'
  yourls_shorturl: http://drwys.so/3
  views: '140'
---
I have an issue with Microsoft - it's no secret. It's often hard to pinpoint, but I recently encountered a problem with Microsoft's support for the CSS <code>opacity</code> property. It goes a little like this...

<!--more-->
<pre class="prettyprint">img {
    opacity: .9;
    -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity = 90)"; /* IE8 */
    filter: alpha(opacity = 90); /* IE5-7 */
}</pre>
<ul>
	<li>The <code>opacity</code> property is first - this is actually a CSS2 (yes, 2) property with support in every major browser - except IE (up to version 9)</li>
	<li>The <code>-ms-filter</code> property comes next - this is the worst one. It's a propriety property, only supported in IE8 and is ridiculously complicated</li>
	<li>The <code>filter</code> property is last - another propriety property, only supported in IE5-7</li>
</ul>

<hr />

While it's great news that IE9 will finally support the opacity property, it's sad that it's taken them this long to get there. The worst part is, Microsoft had a perfectly good (albeit propriety) CSS property for opacity, but replaced it with another one for only 1 browser version. Thanks to Microsofts persistence in the efforts for world domination, web designers now have to write 3 CSS rules instead of just one to emulate opacity and have it work cross-browser.

On a related note, Microsoft <em>won't</em> be supporting the <code>text-shadow</code> CSS property, even though it was in the CSS2 spec (it was later removed in CSS2.1, but support continued across most browsers and it was reintroduced in CSS3).
