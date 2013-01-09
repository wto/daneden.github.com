---
layout: post
title: Web Fonts as icons
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
  yourls_shorturl: http://drwys.so/2a
  dsq_thread_id: '486157178'
---
The rise of web fonts has been an exciting time for web designers. No more are we shackled to the standards of Georgia and Arial - no more will we have to use images for titles - no more do we have to rely on technology such as Cufon to serve the fonts we want to use. But it also means we can look into other possibilities - specifically, using web fonts for infinitely scalable icons and images.

They're actually in use on this website. The post/page navigation buttons and the twitter/facebook buttons at the top of the page are fully scalable web fonts - in this case, the extensive <a href="http://www.justbenicestudio.com/studio/websymbols/">Web Symbols</a> font from Just Be Nice Studio. I really do think that web fonts are the bee's knees. Very little data to download, cheaper in bandwidth terms to download than a bunch of bitmap images for icons. But that's not to say they don't come with their own slew of problems.

<!--more--><a href="http://typekit.com">Typekit</a> have touched briefly on why they don't serve icon fonts, saying this on the subject:
<blockquote>Not only should the website look like we want it to, we also need to make sure the underlying code is standards-compliant so that search engines, screen readers, translation tools, or web archives can make sense of the text. This is why we make sure that each “drawer” contains what it says on the label...

This is also why we do not accept symbol fonts in our library: since no Unicode values yet exist for most of those characters, the only way to use them is to map the images to letters and numbers. The result is gibberish for anyone using an alternate means of reading the site.</blockquote>
I couldn't agree more with what Typekit justifies here. Whenever I use a web font for icons these days, there's a huge churning worry inside me, shouting out "THINK ABOUT THE SOURCE CODE!" The characters mapped to the icons in use on this site are at least relevant - t for Twitter, f for Facebook, &lt; for previous and &gt; for next. But Owlr for example uses icons that bear little relevance to their corresponding character. I for a snap, K for a link, H for code. I felt a little less worried about this, since I knew that most visitors to the site were going to be using a mobile, and are unlikely to be using a screen reader or other method of access. But what can be done?

One popular answer seems to be employing pseudo elements to display the icon. Here's a simple example:
<pre class="prettyprint">&lt;a class="snap-icon" href="javascript:void();"&gt;A Snap&lt;/a&gt;</pre>
A perfectly semantic link, with no silly <code>span</code> or other additional markup for our icon. Our CSS could look something like this:
<pre class="prettyprint">a[class*="-icon"] {
    text-indent: -9999px; // we can hide the original anchor text if we want to
}

a[class*="-icon"]:before {
    font-family: "WebSymbolsRegular";
}

a.snap-icon:before {
    content: 'I';
}</pre>
Not too bad. This way, we get a visual description in the icon, but screen readers and search engines get the fully descriptive "A Snap" inner text.

Of course, outside of semantics there are still a bunch of other problems. Not all web browsers support <code>@font-face</code> - including the relatively new Windows Phone 7 browser. There are also some security issues. For example, Firefox will refuse to accept fonts served from an external server (i.e. you can't visit example.com and get the fonts from foobar.com) unless they're served with an "Access-Control-Allow-Origin" header from the source server. While inconvenient, it makes sense for Firefox to add this extra level of security.

In my opinion, the benefits still outweigh the drawbacks. Infinite scalability is a big plus, particularly when working with high density displays such as the iPhone 4/S retina display - no more downloading additional assets at 2x resolution. But, as Typekit has pointed out, we need to be thoughtful when using them in production websites.
