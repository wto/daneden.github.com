---
layout: post
title: Max CSS In Depth
tags:
- Code
- Design
- Geeky
- Personal
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
  _edit_last: '1'
  _yoast_wpseo_linkdex: '0'
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  dsq_thread_id: '759573999'
---
Yesterday morning, I spent five minutes writing up <a href="http://daneden.me/max-css">an idea</a> I'd had in my head for quite some time. It turned out to become far more popular than I had anticipated - reaching over 10,000 hits in 24 hours thanks to links from <a href="https://twitter.com/search/%23maxcss">Twitter</a>, <a href="http://news.ycombinator.com/item?id=4217477">Hacker News</a>, <a href="http://www.netmagazine.com/news/dev-urges-max-css-help-newcomers-122072">.Net magazine</a>, and <a href="https://twitter.com/smashingmag/status/222579256675414017">Smashing Magazine</a> amongst others. The idea was simple - alongside our compressed and minified CSS files, we should include an uncompressed, no holds barred, comment-laden version of our CSS files for people to take a look at for learning purposes.

"Max CSS" has had a bit of a mixed reaction. Most people seem to agree with the sentiment, if not the proposed execution. A few people just don't get it. So I'm going to take a minute to assess some of the more popular/common/heated concerns that have been raised on Twitter, Hacker News, and elsewhere.

<!--more-->

<h2>&ldquo;Just use web inspector/firebug/etc.&rdquo;</h2>

Sure, tools like web inspector will tell you the styles for any given element on a page, theoretically helping new designers and developers learn techniques by way of example. But that's not what Max CSS is about. Max CSS is encouraging the preservation of a CSS file's structure and comments from the author, explaining potentially bizarre declarations, hacks, or methods used, and the reasoning behind their code.

There's so much more to writing good CSS than the code itself. In fact, I'd say that commenting and structure are almost more important than the quality of the code itself in terms of maintainability - well documented and organised code is crucial for development of any site, with any number of people in a team. In short, Max CSS is about the author's comments and organisation, ;<em>not the code itself.</em>

If, for example, we took <a href="http://www.stubbornella.org/content/2010/06/25/the-media-object-saves-hundreds-of-lines-of-code/">the media object</a> in a large, minified CSS file, we'd probably get something like this:

<pre class=prettyprint>.media{padding:10px;overflow:hidden}
.media .img{float:left;margin-right:10px}</pre>

A bit of an eyesore, but you get the general idea. However, someone new to CSS might not get it completely, or might go blindly in and copy the code into their own site or app, completely unaware of the meaning behind the code. Jump to our <code>style.max.css</code> and we can see the author's original intentions, clearly documented with comments:

<pre class=prettyprint>/*------------------------------------*\
    $MEDIA
    .media object for containing an image or some other media and corresponding text/content.
    Usage example:
    &lt;div class=media>
        &lt;img class=img src="profile.jpg" alt="">
        &lt;div class=bd>This is my face. There are many like it, but this one is mine.&lt;/div>
    &lt;/div>
\*------------------------------------*/

.media {
    padding: 10px;
    overflow: hidden; /* Clear floats - though a more reliable clearfix is recommended */
}

        .media .img {
            float: left;
            margin-right: 10px;
        }</pre>

And just like that, we've taught our designer/developer in-the-making how to clear a float, as well as informing them of better ways to do so, and demonstrating some decent practices for organising and structuring CSS. Knowledge is power.

<h2>&ldquo;Minifying helps prevent code from being stolen.&rdquo;</h2>

Hardly. There are <a href="http://procssor.com">tools</a> available that allow developers to paste in minified CSS and have it reformatted for readability. Not to mention the fact that tools like web inspector allow you to view the CSS of any element - and whadyaknow, it formats it for you and everything. A quick copy-and-paste, and your code has been stolen.

But once again, if you find yourself worrying about this, you're not really getting the idea of Max CSS - it's a learning tool. Most new designers and developers start out by 'stealing' code. Replicating websites on their own computers (though admittedly, sometimes on live sites) for practice. It's healthy. We've <em>all</em> been there. By giving those who want to learn unrestricted access to the fully documented CSS, at least we can point out potentially odd parts of code and explain what's going on.

<h2>&ldquo;A steep learning curve is healthy for up-and-coming designer/developers.&rdquo;</h2>

It was <a href="http://news.ycombinator.com/item?id=4217982">this comment</a> in particular that really got me. This chap seems to think that the world of web design is dictated by natural selection - survival of the fittest.

What?

Forgive me, but "survival of the fittest" is the very last thing I'd ascribe to the web design and development community. The complete opposite. I have never come across a more forgiving, more helpful, more universally accepting, curious, or happy community than the web design and development community I'm proud to call myself a part of. I can't even imagine another industry like this one. We have a magnificent gift, fellow web workers. We can make our own future. And the future of those after us. We can literally change the world. And if you're too busy designing like your life depends on it, in a "survival of the fittest" state of mind, you're going to end up with CSS that's impossible to maintain by your future self, let alone those who might pick up your code later on.

By hiding your secrets, you're doing no one any favors. Someone might well come across a problem in your CSS you might otherwise have never noticed, and give you a helping hand in fixing it. But not if you minify it.

You might be able to give someone a piece of code that'll help them with a problem they've been having for years.

But not if you minify it.

<h2>Other, smaller concerns.</h2>

There were a few other things people mentioned. Namely:

<h3>&ldquo;This is what <a href="http://github.com">GitHub</a> is for!&rdquo;</h3>
Correct. If you'd rather put your unminified CSS up on GitHub, then that's great! Not only does it encourage the same kind of explorative learning that inspired the idea for Max CSS, but you're also allowing a wider community to significantly and easily contribute directly to your product. All good things.

<h3>&ldquo;Why would you call it *.max.css? Why not omit the .max?&rdquo;</h3>
This was mainly due to the fact that some systems - such as WordPress - require you to call the stylesheet simply <code>style.css</code>. The <code>.max</code> was a way around that. But you can call it whatever the heck you want.

<h3>&ldquo;But I&rsquo;m using LESS/SASS!&rdquo;</h3>
<a href="http://daneden.me/2012/05/preprocessors/" title="Preprocessors">Why?</a> But personal preferences aside, good for you. You've found a workflow that works, which is good. There's not much you have to change, though - simply provide a link to the unprocessed and unminified LESS/SASS files.

<h2>I still don't get it.</h2>

I'm not sure I do either. All I know is that it gives me such joy to look at the CSS another developer has worked on - get my head around the techniques they've used and let that lead me to questioning my own approach. Can I do better? Probably. Can I help another person do better? Hopefully.

Not minifying your CSS - or providing a direct link to the unminified version - is the best thing we can do to encourage new designers and developers. Well, second best - right after actually taking the time out to reply to their tweets and emails.

Be helpful. It's what newbie you needed when you started.
