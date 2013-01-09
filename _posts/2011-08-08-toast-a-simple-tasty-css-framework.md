---
layout: post
title: Toast - a simple & tasty CSS framework
tags:
- Code
- Design
- Development
- Downloads
- Updates
status: publish
type: post
published: true
meta:
  views: '624'
  yourls_tweeted: '1'
  yourls_shorturl: http://drwys.so/19
  _edit_last: '1'
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_focuskw: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  dsq_thread_id: '457550200'
---
<img class="aligncenter size-full wp-image-547" title="stop" src="http://daneden.me/wp-content/uploads/2011/08/large.png" alt="Stop mucking up your markup!" width="800" height="600" />

Not so long ago, I <a title="Improving the CSS framework" href="http://daneden.me/2011/08/improving-the-css-framework/">posted</a> about the problems of today's CSS frameworks - namely, the clearfix and declaring the last item in a row. Rather than just whine and moan and not actually do anything about it, I thought I'd tackle the problem head first - the result is <a title="Toast.css - a simple &amp; tasty CSS framework" href="http://daneden.me/toast/">Toast</a>, and I'll try to explain it all pretty thoroughly right here.
<!--more-->
<h2>Wait, another CSS framework?</h2>
Yup, another one. You must know that there are a whole <a title="The 960px Grid System" href="http://960.gs">bunch</a> of <a title="1140px Grid" href="http://cssgrid.net">frameworks</a> <a title="Cabin CSS" href="http://cabincss.com">available</a> to use <a title="Blueprint CSS" href="http://blueprintcss.org">all over</a> the <a title="Less CSS Framework" href="http://lessframework.com">web</a>, each with advantages, disadvantages, quirks &amp; perks. No doubt you've found one you love, and stuck with it. Unfortunately, I'm not so happy to settle - I've tried every framework under the sun, and while Andy Taylor's CSS Grid has been the best so far, I've never been truly happy with them. I always end up having to rewrite rules and modify code to let it fit to what I need.

Not to mention one particular time-consuming activity; setting type to a baseline grid. No matter how many great tutorials there are on doing this (thanks to <a title="The Baseline Project" href="http://adamwhitcroft.com/baseline/">this website</a> for the best so far) it's going to take you some time unless you do it right at the beginning of the project, which, if you're anything like me, you'll forget to do. The CSS framework is a perfect place to do this, and there haven't been many to take up that oppurtunity.
<h1>So what's in the box?</h1>
The files you download from github or direct from the site will include the following, which I'll explain one by one, in depth (note that these descriptions are as of v1.1):
<ul>
	<li><code>index.html</code></li>
	<li><code>style.css</code></li>
	<li><code>IE.css</code></li>
	<li><code>reset.css</code></li>
	<li><code>toast.css</code></li>
	<li><code>type.css</code></li>
</ul>
So, let's take a closer look at these files.
<h3>index.html</h3>
Nothing special here. It's a plain index file with links to the stylesheets, and some basic page structure. There <em>is</em> however a link to a script that will make Internet Explorer behave more modern, enabling us to use Toast to it's full potential.
<h3>style.css</h3>
Again, nothing to see. It's an empty stylesheet, ready for rules. In the root of the 'site' as opposed to in the 'CSS' folder, so that it's ready to be dropped into a WordPress theme.
<h3>IE.css</h3>
This sheet does some clever things - thanks to <a title="Dan Cederholm" href="http://simplebits.com">Dan Cederholm</a>, the clearfix in the framework will work properly with Internet Explorer 6 &amp; 7 with the help of this sheet.
<h3>reset.css</h3>
<a title="Eric Meyer" href="http://meyerweb.com/">Eric Meyer</a>'s reset stylesheet. A must have for any project.
<h3>toast.css</h3>
This is the good stuff. Toast's base CSS file is fairly full &amp; complex, so I'll try to take it easy. I won't post the code here, simply because there's far too much - so if you'd like to read along, download the framework and open it up.

The first rules import the other stylesheets that come with Toast - reset.css, IE.css and type.css (which we'll come to soon). It also hides these stylesheets from IE for Mac, just because it's outdated and deserves as little styling as possible.

Next we'll apply some padding to the side of the container, giving the page a little breathing room. After that, the styles for the rows are applied - maximum &amp; minimum width, and put it in the center of the page. Some people prefer to work in 960px as opposed to Toast's default 1140px - so a class called <code>smallscreen</code> is added to set a maximum page width of 980px.

The columns are given some styles now - we want them to be inline elements, floated to the left, with a right margin creating the gutters between columns and each with a minimum height of 1px.

Next comes the lengthy process of all the individual column widths. Note I didn't come up with these widths, they're adapted from Andy Taylor's CSS Grid. However, I did notice that once these widths were in place along with some other rules, the rows were too wide in Firefox. This is because the widths I used were optimised for WebKit, which renders subpixels slightly differently - a width of 1140px in CSS (and Firefox) is actually 1133px in WebKit.

Next come the box styles - these are for the people who like their modules to be all 'blocky' - with padding and backgrounds and whatnot. Funnily enough, a lack of support for this feature is one of the main reasons people avoid CSS frameworks. Toast can do it just fine!

Adding <code>box</code> to the module's classes will give it a padding of around 1% whilst maintaining the rest of the structure of the page. It's not quite spot on, and needs some work.

Next, all the most likely block-level elements are given a maximum width of 100%, to stop them leaking out of their container - aka images, videos, flash objects etc.

The next few rules are pretty cool. First, the CSS finds the last module of each row and removes the right hand margin - thus avoiding the need to add the <code>last</code> class to the module. Yippee! Straight after that is the clearfix discussed in the post I mentioned earlier. Two big problems with CSS frameworks, fixed in 2 rules.

Last but not least come the media queries. First, below a 'normal' resolution, the font sizes are decreased to 90% - about 14px. Next, as long as the page has a respond class somewhere, when the screen resolution is less that 775px, the modules shift so that they're on top of each other instead of next to one another.
<h3>type.css</h3>
The last file in our framework. This sets basic styles for type elements, as well as implementing a baseline grid for great vertical rhythm. You can read a more detailed overview of the techniques I used <a title="How to set up a baseline grid" href="http://adamwhitcroft.com/baseline/posts/how-to-set-up-a-baseline-grid/">here</a> but the overall effect of the stylesheet is something like this:
<ul>
	<li>Set fonts at 100% - usually 16px</li>
	<li>Set the line-height at 1.5em (24px)</li>
	<li>Give headings relative sizes and margins to maintain vertical rhythm</li>
	<li>Give other block-level elements margins (paragraphs, lists, block quotes)</li>
</ul>
And, well, you get the gist.
<h1>The future of Toast</h1>
Right now, the future and stability of Toast isn't fully clear. I'll certainly be using it in my own projects (I've already replaced the old frameworks with Toast in 2 of my current projects), and it seems to be causing some buzz amongst people. I need feedback, more than anything. Feedback, tests, and feature requests will help this framework grow into something that more and more people will enjoy.

So what are you waiting for? <a title="Toast framework" href="http://daneden.me/toast/">Go and get it</a>! Let me know what you think, or if you've used it on a website you're building.
