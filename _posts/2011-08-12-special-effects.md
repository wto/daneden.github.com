---
layout: post
title: Special Effects
tags:
- Code
- Design
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  yourls_shorturl: http://drwys.so/1d
  views: '586'
  yourls_tweeted: '1'
  art_direction_single: ! "<style type=\"text/css\" media=\"screen\">\r\nhtml, body
    { background: #E2D0B4 url(http://cdn.daneden.me/wp-content/uploads/2011/08/specialeffectsbg.png)
    repeat; color: #333; }\r\n.row, #main, .container { background: transparent; }\r\n.post_header
    { -webkit-mask-image: url(http://cdn.daneden.me/wp-content/uploads/2011/08/mask.png);
    }\r\nh1.post_title {\r\n    min-height: 100px;\r\n    font-family: futura-pt,
    Futura, Helvetica Neue, Helvetica, Arial, sans-serif;\r\n    font-weight: 700;\r\n
    \   color: #333;\r\n    color: rgba(255,255,255,1);\r\n    text-shadow:\r\n    0
    1px 0px #378ab4,\r\n    1px 0 0px #5dabcd,\r\n    1px 2px 1px #378ab4,\r\n    2px
    1px 1px #5dabcd,\r\n    2px 3px 2px #378ab4,\r\n    3px 2px 2px #5dabcd,\r\n    3px
    4px 2px #378ab4,\r\n    4px 3px 3px #5dabcd,\r\n    4px 5px 3px #378ab4,\r\n    5px
    4px 2px #5dabcd,\r\n    5px 6px 2px #378ab4,\r\n    6px 5px 2px #5dabcd,\r\n    6px
    7px 1px #378ab4,\r\n    7px 6px 1px #5dabcd,\r\n    7px 8px 0px #378ab4,\r\n    8px
    7px 0px #5dabcd;\r\n    text-transform: uppercase;\r\n    font-size: 4em;\r\n
    \   line-height: 1;\r\n}\r\n\r\na, h3 { color: #d86b22; }\r\n\r\na:hover { color:
    #5D83C0; }\r\n\r\n.post_title .date {\r\n    margin: .75em auto;\r\n}\r\n\r\n.post_header
    \ time {\r\n    text-shadow: none;\r\n    background: #E2D0B4;\r\n    color: #d86b22;\r\n}\r\n</style>"
  dsq_thread_id: '457550225'
---
With more and more CSS3 properties, web designers are getting a lot more control over their work. Things that may have previously been achieved only through Flash or Photoshop are becoming reality, or are undergoing some serious experimentation.

I'd love to say I know all about a lot of these experimental properties and their potential, but just spending a few minutes browsing around the web has proved me wrong. So instead, I present to you a round-up of my current favorites from the vast collection of CSS experiments going on around the web.

<!--more-->
<h3>Gravatar tucked corners</h3>
<a title="Gravatar tucked corners" href="http://playground.genelocklin.com/tucked-corners/">This</a> wonderful demo is a collaboration of efforts from <a title="Gene Locklin on twitter" href="http://twitter.com/genelocklin">Gene Locklin</a> and <a title="Josh Hibbert on twitter" href="http://twitter.com/joshuanhibbert">Josh Hibbert</a> in an attempt to recreate the 'tucked' corner effect on <a title="Gravatar - globally recognised avatars" href="http://gravatar.com">Gravatar's home page</a> - and I have to say, they did a bloody good job of it. It's probably the most effective use of <code>box-shadow</code> and pseudo elements I've seen to date, and I still struggle to get my head round how they did it. Bravo, lads.

[caption id="attachment_629" align="aligncenter" width="800" caption="What is this, I don&#39;t even... Impressive CSS."]<a href="http://playground.genelocklin.com/tucked-corners/"><img class="size-full wp-image-629" title="Gravatar's homepage recreated in CSS3" src="http://daneden.me/wp-content/uploads/2011/08/howdidthey.png" alt="" width="800" height="300" /></a>[/caption]
<h3>Mask-image</h3>
There are actually a few great examples I wanted to show off for this particular property, but I'll try to keep it short. The most impressive comes from a design by Matthew Smith of <a title="SquaredEye" href="http://squaredeye.com/">SquaredEye</a> which was built by <a title="Michael Meyer" href="http://mikemeyer.tumblr.com/">Michael Meyer</a>. It's an event page that features a whole host of CSS3 effects, but the most striking is in the headline - where a bright sunbeam is shining through. This is achieved through the use of <code>mask-image</code>, a property that works much in the same way that Photoshop's masks do.

[caption id="attachment_630" align="aligncenter" width="660" caption="That&#39;s selectable text. Wicked cool!"]<a href="http://tintype.mikemeyer.im/adoption/home.html"><img class="size-full wp-image-630" title="A Night for Adoption" src="http://daneden.me/wp-content/uploads/2011/08/smith_adoption.jpg" alt="" width="660" height="389" /></a>[/caption]

Credit for this example however, goes to <a title="Trent Walton" href="http://trentwalton.com/">Trent Walton</a> - he wrote a great <a title="Mask-image text by Trent Walton" href="http://trentwalton.com/2011/05/19/mask-image-text/">post</a> with a few examples of<code>mask-image</code>, and he uses it particularly well in his designs.
<h3>Text shadow</h3>
The <code>text-shadow</code> property is probably one of the most accessible and fun in the CSS3 spec. It's easy to make great looking designs with a simple drop shadow on text, but hard to make <em>great</em> looking designs. Typekit have gone all out and provided a <a title="Shading with CSS text-shadow - Typekit" href="http://blog.typekit.com/2011/07/19/shading-with-css-text-shadows/">fantastic post</a> of examples of beautiful uses of the <code>text-shadow</code> property. I even used one technique for the title of this post.

[caption id="attachment_632" align="aligncenter" width="800" caption="Amazing text-shadow usage from Typekit"]<a href="http://blog.typekit.com/2011/07/19/shading-with-css-text-shadows/"><img class="size-full wp-image-632" title="Print-style text-shadow techniques" src="http://daneden.me/wp-content/uploads/2011/08/textshadow.png" alt="" width="800" height="447" /></a>[/caption]
<h3> Simurai</h3>
There isn't really one example of Simurai's work that stands out - it's all astonishingly good. He makes incredible interfaces &amp; experiments using only HTML and CSS, and does a bloody good job of it too. Just go and browse through the <a title="Simurai Labs" href="http://lab.simurai.com/">labs</a> to see what I'm talking about.

[caption id="attachment_634" align="aligncenter" width="509" caption="My favorite experiment by Simurai - all in HTML &amp; CSS. Amazing!"]<a href="http://lab.simurai.com/css/umbrui/"><img class="size-full wp-image-634" title="UmbrUI by Simurai" src="http://daneden.me/wp-content/uploads/2011/08/umbrui.png" alt="" width="509" height="377" /></a>[/caption]
<h3>CSS-Tricks</h3>
Again, I don't have a particular example from <a title="CSS Tricks" href="http://css-tricks.com">Chris Coyier</a> - he is just another CSS master. I can almost guarantee, if there's a CSS property, Chris has done an example of it that's easy to grasp and presented in a fun and great way. If you have the time, watch his screencasts - they're well worth it.

[caption id="attachment_635" align="aligncenter" width="814" caption="Just a few of the hundreds of available snippets on CSS-tricks.com"]<a href="http://css-tricks.com"><img class="size-full wp-image-635" title="Hundreds of snippets on CSS-tricks.com" src="http://daneden.me/wp-content/uploads/2011/08/woah.png" alt="" width="814" height="449" /></a>[/caption]

<hr />

For now, those are the ones I'd say are worthy. I have no doubt that I'll come across something soon after and wish I'd included it, but I usually share any cool stuff I find over on <a href="http://twitter.com/dan_eden">twitter</a> if you're interested.
