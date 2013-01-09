---
layout: post
title: Custom Safari "Top Sites" thumbnail
tags:
- Code
- Design
- Development
- Personal
status: publish
type: post
published: true
meta:
  _yoast_wpseo_focuskw: ''
  _edit_last: '1'
  _yoast_wpseo_title: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  dsq_thread_id: '510427309'
---
This-is-kinda-cool of the day. If you're a Safari and iCloud user, you may have noticed the custom "Top Sites" thumbnail it features. Take a look at the example:

[caption id="attachment_1125" align="aligncenter" width="463" caption="iCloud gets a fancy Top Sites preview thumbnail"]<img class="size-full wp-image-1125" title="iCloud Top Sites preview" src="http://daneden.me/wp-content/uploads/2011/12/topsites.png" alt="" width="463" height="276" />[/caption]

For a while, I was willing to accept that Apple hold the key to this level of customisation, and that's the way it could stay. But I really wanted to know what was going on here, so I popped open iCloud and took a look at the code.

<!--more-->After a bit of scanning, I saw something along the lines of:
<pre class="prettyprint">if(window.navigator &amp;&amp; window.navigator.loadPurpose === "preview"){
    window.location.href = "https://icloud.com/safari_preview"
}</pre>
Bingo. Seems like this Safari-only window property is our ticket to the top sites thumbnails. Just to be sure, I went to <code>http://icloud.com/safari_preview</code> to check it against the thumbnail, but got redirected. My guess is that they had something in effect of the reverse on the preview site, like this:
<pre class="prettyprint">if(window.navigator &amp;&amp; window.navigator.loadPurpose != "preview"){
    window.location.href = "https://icloud.com"
}</pre>
So there you have it. Custom "Top Sites" thumbnails and a redirection for non-preview access.

[caption id="attachment_1126" align="aligncenter" width="1600" caption="Custom Top Sites thumbnails for brills.me and the blog"]<a href="http://daneden.me/wp-content/uploads/2011/12/topsites1.png"><img class="size-full wp-image-1126" title="Top Sites previews for Brills and my blog" src="http://daneden.me/wp-content/uploads/2011/12/topsites1.png" alt="" width="1600" height="900" /></a>[/caption]
