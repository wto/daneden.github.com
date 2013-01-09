---
layout: post
title: The story behind the new design
tags:
- Code
- Design
- Personal
- Updates
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  yourls_tweeted: '1'
  yourls_shorturl: http://drwys.so/14
  views: '264'
  dsq_thread_id: '457550194'
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_focuskw: ''
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
---
<mark>This post is referring to an old blog design that is no longer in use. However, the principles and techniques are still relevant.</mark>

Regular visitors, twitter listeners and Dribbble players might have noticed a change around here - I updated my website theme. And it's a biggy.

I've always thought of myself as someone with a good eye for design - a natural. But relatively recently, my eyes have been opened - and I'm just a tiny tadpole in a sea of sharks. <a title="Sebaastian de With" href="http://dribbble.com/Cocoia">There</a> <a title="Tim Boelaars" href="http://dribbble.com/timboelaars">are</a> <a title="Luke Beard" href="http://dribbble.com/lukesbeard">some</a> <a title="Pasquale D'Silva" href="http://dribbble.com/pasquale">seriously</a> <a title="Tim Van Damm" href="http://dribbble.com/maxvoltar">talented</a> <a title="Meagan Fisher" href="http://dribbble.com/owltastic">people</a> <a title="Morgan Allan Knutson" href="http://dribbble.com/morgan">out</a> <a title="Trent Walton" href="http://dribbble.com/TrentWalton">there</a>, people who drool creativity and make everything look so much easier. It soon came to light that these people had spent a long time getting good at what they do. They went to art school, design school, bought hundreds of books and read them all. They got good at what they do because they put so much effort in.

I pretty much started designing by accident. I was in a band and we needed some artwork and what not, so I opened up Photoshop and saw what I could throw together - nothing great. It was pretty awful now I think about it, but it started me off. I started making more things in Photoshop - playing with icon design, typographic posters and so on; but I never really knew what I was doing. I had the chance to change that - in high school, college and in university, I could have quite easily said one day "I'm going to do something more art-based" but I didn't realise what it was I could have had.

<!--more-->

Seeing all these great designers made me look at what I had - the previous design - and notice all the little flaws. I couldn't pin why certain things didn't look right, I just knew they should look more like what Luke Beard or Trent Walton were putting together. Over the course of a few months, I'd completely reevaluated my website and it's design, checking it against the pros - Newspapers, Fashion websites, Type foundries - the people who were holding the torch for designers. There was an awful lot of talk about typography scattered around.
<h2>Typography</h2>
Until about a week ago, typography for me was just an arrangement of nice fonts, conveying a message. Something like the CSS experiment I threw together. But the more I read about it, the more I realised how wrong I was. In "The Elements of Typographic Style", Robert Bringhurst tells us that:
<blockquote>In a world rife with unsolicited messages, typography must often draw attention to itself before it will be read. Yet in order to be read, it must relinquish the attention it has drawn</blockquote>
Typography should honor the content, not the other way round. Leading, kerning, font stacks - all these things were new and confusing to me, but with the help of the following websites, books, and blogs (note the oxford comma - which I'm a convert to now) I was able to take these important factors and apply them to the redesign of the site:
<ul>
	<li>The most influential website has been the <a href="http://webtypography.net/">Elements of Typographic Style Applied to the Web</a> - a guideline to the dos and don'ts of web typography. This was the very first website I looked at for the redesign (at which point it just bewlidered me) as well as the very last (so I could run through and correct any bad habits I'd picked up along the way). It's based on <a href="http://www.amazon.co.uk/Elements-Typographic-Style-Robert-Bringhurst/dp/0881792063">the book</a> by Robert Bringhurst, which is said to be the 'typographers bible'.</li>
	<li>Next up is the fantastic <a href="https://shop.smashingmagazine.com/smashing-book-2-intl.html">Smashing Book #2</a>, a worthwhile investment for any web or graphic designer. The opening chapter gives a thorough yet brief and easy to grasp introduction to some basic graphic design principles, such as contrast, line and typography.</li>
	<li>The other big player is Mark Boulton's <a href="http://www.markboulton.co.uk/journal/comments/five-simple-steps-to-better-typography">Five Simple Steps to Better Typography</a> - he gives the complex world of typography an approachable and entertaining outlook. A definate addition to the instapaper list, and I even invested in <a href="http://www.fivesimplesteps.com/products/a-practical-guide-to-designing-for-the-web">the book</a> that he wrote.</li>
</ul>
Now usually, I'd opt against the built in fonts and web standard fonts found in most browsers, and go for something a little more custom. In my first website, I used Droid Sans &amp; Chunk Five, number two was Lobster &amp; Droid Sans, and the last theme was <a href="http://www.google.com/webfonts/family?family=Cabin&amp;subset=latin">Cabin</a> &amp; <a href="http://www.google.com/webfonts/family?family=Kreon&amp;subset=latin">Kreon</a> - a stand-up combination that served me well. In fact, it was this combination I intended to use for the redesign. So I spent a good couple of days marking up the HTML and CSS, sorting out the line heights and letter spacing, and preparing the site for launch - I even <a href="http://drbl.in/byOf">dribbble'd</a> a little. It was only about an hour before Wordpressing the theme that I decided against it. I was testing the site in all the browsers I saw fit - Chrome, Firefox, Safari, and iOS. When I opened it up on the iPad simulator however, the custom fonts simply wouldn't load, so it fell back to Georgia on the body - which I thought looked simply amazing. So I rehauled the entire font selection for the site and went for Futura &amp; Georgia - falling back on Josefin Sans/Arial &amp; Times New Roman.

Some of the more minor design decisions I made included things like line height, font sizes etc, so I'll brush through them real quickly. The font size is set at 100% - the default for browsers, usually 16 px, simply because there's a reason those default sizes are set - they're readable. The line height is set to 1.5 - about 24 px. I was avoiding using pixel based values, keeping the typography under the control of the user, as is should be. For things like dates, and section headings, I used a sans-serif font with letter-spacing of 0.1 em. I also applied a subtle letter spacing to the blockquotes, as well as making it lighter, centered (but aligned left) and giving it plenty of space in margins and padding.
<h2>Contrast</h2>
Once I'd addressed my biggest handicap (typography) I tried my hand at evaluating the site's contrast. I don't like to admit it, but the last theme had pretty bad contrast. Sure black text on white background supplied pretty solid contrast for the body, but everything else was up in the air. The sidebar looked like the content half the time, blockquotes were pretty poorly designed - things just weren't sitting right. I was determined to do it right this time.

One of the biggest influences in the whole feel and layout of the site comes from <a href="http://simplebits.com/">Dan Cederholm's website</a> which executes media queries beautifully, with content and arbitrary information clearly set apart from each other. So I grabbed a copy of Andy Taylor's <a href="http://cssgrid.net">CSS Grid</a> for easy mobile and tablet compatibility, and got the layout up. Using Dan Cederholm's faux column effect, the sidebar is clearly set apart from the main content area this time. Repetitive sections like the meta information at the end of each article helped to create some contrast between each post. The post titles contrast a great amount from the rest of the content, and are heavily influenced by <a href="http://alistapart.com">A List Apart</a>.

The footer is completely inverse from the rest of the page, with a near-black background and off-white text. The font is also less bold. Generally speaking, when light text is set against dark background, the contrast can be lessened.
<h2>Line</h2>
Great care was taken in the layout of the website. Rules set by the typographic grid are followed, the content is 9 columns wide with the sidebar taking 3 columns, the navigation is lined up with the sidebar, and it all looks much nicer. Font sizes were kept as consistent as possible, to make following the baseline grid easier. Aligned images don't break the flow of content as they once did. Lists hang off the edge of the content, just as they should.

There are also a few subtle and not-so-subtle lines around the site dividing content up - between each post, between the header and content, under section headers etc. Each one was considered carefully, colored appropriately, weighted thoughtfully, and drawn with care.
<h2>Color</h2>
If you've known the site since day one, you'll probably have guessed I like the color blue. It's played a big part in every iteration of the site to date, as well as the majority of my shots on dribbble and snaps on Forrst. It's a lovely color, but I've grown something of an obsession for it, that I was determined to get over. Yes yes, I know, the links and headings are still blue. But that's it. Everything else is black, white, green, and cream. I chose fairly neutral colors for most of the site, with bright colors dictating points of interest. After all, that's the point of bright colors right?

It's also worth noting that I removed the color change in the evening. It was a lovely effect, but that was really it. The bottom line is, user experience and consistency is more important than personal preference. I prefer to use the dark theme on instapaper, and I preferred browsing my site using the dark theme. But when you open a newpaper, or go to the New York Times website, it's black text on white body. This is the usual convention, and should be followed. If you miss it, let me know. I'll work something out.
<h2>Lessons learned</h2>
There's far too much here for me to try and talk to you about, and I'd do a terrible job even if I tried. But some of the most basic things I learnt are as follows:
<ul>
	<li><strong>Criticise yourself</strong> - This might be hard, particularly if you're anything like me and <em>detest</em> criticism. But it's the most important thing I did in the redesign. I told myself I knew nothing compared to the pro's whose websites I lusted after, which was true. And it helped me on the path to righteousness.</li>
	<li><strong>Learn from the pros</strong> - Rather than browsing through dribbble looking longingly at posts, wondering <em>how</em> these people got so good, pick up the book written by that guy and find out their process. They'll have learnt from someone better than them, so pick their book up too. I hate reading, but it's something you absolutely must do in order to get better. Maybe one day you'll write your own!</li>
	<li><strong>Stick to conventions, but escape your own comfort zone</strong> -  Another potentially scary task, but it's important to get out of your bad habits (and maybe even your good ones) just to pick up the ones that are the general consensus, or ones that work surprisingly well. Mine was the color blue, and custom fonts. You'll be surprised with what you discover if you accidentally load your site without those fonts, or with a completely new color.</li>
	<li><strong>Don't forget your roots</strong> - Not necessarily your personal roots as a designer, but the roots of the practice - a practice which is now hundreds and thousands years old. The golden ratio has its roots in Egyptian times, and things like small caps get their influence from the Romans. The Elements of Typographic Style by Robert Bringhurst has been credited as a fantastic resource not just for tyopgraphers, but for any designer. I have yet to invest, but it's on my wishlist. There's a reason that people do so well in this business, and it's down to their commitment to the traditions, schools and practices they've attended and stick to.</li>
</ul>
