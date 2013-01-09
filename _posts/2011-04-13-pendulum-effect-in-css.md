---
layout: post
title: Pendulum effect in CSS
tags:
- Code
- Development
status: publish
type: post
published: true
meta:
  _edit_last: '1'
  yourls_tweeted: '1'
  yourls_shorturl: http://drwys.so/m
  dsq_thread_id: '458167459'
  views: '418'
  _yoast_wpseo_focuskw: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
---
Thought I'd just share a little insight into the <code>-webkit-animation</code> functionality of CSS3. I've only found a few uses for CSS animation, but it definitely has a lot of potential, particularly for AJAX-y stuff. The HTML behind this is basically a div with the class <code>container</code> and another inside it with the class <code>pendulum</code>. It's the CSS that does the hard work.
<!--more-->
<h2>The CSS</h2>
This is where the magic happens - all the CSS is as below:
<pre class="prettyprint">@-webkit-keyframes swinging {
    0% {
        -webkit-transform: rotate(-45deg);
    }

    50% {
        -webkit-transform: rotate(45deg);
    }

    100% {
        -webkit-transform: rotate(-45deg);
    }
}

body {
    text-align: center;
    background: #444;
}

.pendulum {
    margin: 0 auto;
    position: relative;
    background: #ddd;
    color: #333;
    width: 128px;
    height: 128px;
    line-height: 128px;
    -webkit-border-radius: 1000px;
    margin: 0 0 0 -53px;
    font-weight: bold;
    -webkit-box-shadow: 0 0 20px rgba(0,0,0,.3);
}

.container {
    padding-top: 200px;
    -webkit-animation: swinging 3s infinite ease-in-out;
    background: #ddd;
    width: 20px;
    -webkit-transform-origin: top;
    margin: 0 auto;
    -webkit-border-radius: 1000px;
    -webkit-box-shadow: 0 0 20px rgba(0,0,0,.3);
}</pre>
As always, there's a live demo running <a href="http://daneden.me/labs/pendulum.html" target="_blank">right here</a> - but it's for Webkit browsers only (Chrome and Safari).
