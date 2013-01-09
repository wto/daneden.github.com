---
layout: post
title: Typekit's Web Font Loader is Awesome
tags:
- Code
- Design
- Development
- Geeky
- Personal
status: publish
type: post
published: true
meta:
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_focuskw: ''
  _edit_last: '1'
  dsq_thread_id: '568756134'
  _yoast_wpseo_redirect: ''
  _yoast_wpseo_linkdex: '0'
---
It really is. I've <a href="http://daneden.me/2011/07/a-smoother-page-load-via-jonikorpi/" title="A Smoother Page Load (via @jonikorpi)">touched on this briefly</a> before, pointing to Joni Korpi's <a href="http://jonikorpi.com/a-smoother-page-load/">experiences</a> with the loader, but I've only really started using the tool for my own benefit. It's actually something I came across while I was putting together <a href="http://dribbble.com/shots/394795-Design-Happy">Design Happy</a>, my super-secret in-the-works project. Since it's still under wraps, I can't show off the cool stuff I've been doing with the loader.

<h2>Twenty one years in the making</h2>
It's a happy coincidence that my birthday is coming up, which gave me a great, restriction-free creative project to show off the power of the web font loader with. If you're in a hurry, you can see the final thing <a href="http://daneden.me/twentyone">right here.</a> Best served in Webkit. Let's dig in.
<!--more-->
Since we're using Typekit, it'd make sense to use a few fonts from them right? The fonts from Typekit on the page are <a href="https://typekit.com/fonts/futura-pt">Futura PT</a> and <a href="https://typekit.com/fonts/adelle-web">Adelle Web.</a> As web fonts go, these are pretty heavy file sizes. As well as these, I added <a href="http://www.google.com/webfonts/specimen/Six+Caps">Six Caps</a>, this time from Google's web font directory.

I also tried to get some relatively heavyweight image files on there - there's a picture of me when I was born, me in the present, and a birds-eye view of my hometown, Stockport. All together, the page weighs in at 863kb. Nothing too monumental, but a pretty weighty page.

When you open the page though, the load doesn't (or shouldn't) seem too long a wait. The content is hidden and in its place, a friendly loading gif shows something's going on. This is possible thanks to Typekit's loader.

The loader was actually made in a <a href="https://developers.google.com/webfonts/docs/webfont_loader">collaborative effort</a> by Google and Typekit. Basically, while the fonts are loading from whichever service, the html document is given a class of <code>wf-loading</code>. With this class, I can hide the content, thus preventing any weird behavior as remote font files are downloaded. Then, once the fonts have loaded, the content can be brought back - a class of <code>wf-active</code> (or <code>wf-inactive</code> if for some reason loading the fonts failed) takes over where the loading class once was. In the CSS for that page, <code>wf-active</code> is given a nice fading entrance.

Now, that's all good and well. Fight the <a href="http://paulirish.com/2009/fighting-the-font-face-fout/">FOUT</a> and all that. But what really got me thinking with this tool is the possibility of using it for lazy loading 'real' content. By using the asynchronous loader, we can set off the web fonts loading while the rest of the content loads while it's hidden from the user's eyes. If you're on a decent connection, the supporting images in the page will have loaded with absolutely no wait after the content appeared. Isn't that great? If you're using Typekit, you've got a lazy loading plugin already set up for you.

<h2>So what?</h2>
Forgive me for making such a big deal out of this, but it really does matter. Take a look over <a href="http://www.intuity.de/en/open-thoughts-about-performance/">this article</a> by Intuity Media Labs - particularly the section titled "Shaping the assumed performance". By showing the user that something is loading with a simple animation, rather than showing the content's load itself, we can speed up the process in the user's mind. The Typekit font loader gives a super simple way to make this kind of loading really easy. Couple that with some animations to ease the content in once it's loaded, and you've got yourself one hell of a happy user.
