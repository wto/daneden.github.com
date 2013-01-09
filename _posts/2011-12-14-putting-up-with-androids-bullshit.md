---
layout: post
title: Dispelling the Android CSS animation myths
tags:
- Code
- Design
- Development
- Geeky
- Rants
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
  dsq_thread_id: '504223161'
  _wp_old_slug: dispelling-the-android-css-animation-myths
---
We live in good times as web developer/designers. There are more fantastic resources available today than there ever have been - we have websites like <a href="http://www.quirksmode.org/">QuirksMode</a>, <a href="http://caniuse.com/">Can I Use?</a>, and the recent <a href="http://mobilehtml5.org/">Mobile HTML5</a> to tell us what features we can expect to use on a myriad of operating systems, browsers and mobile devices. Super! But there's a recurring theme across all of these websites. They all tell us that Android <em>fully supports CSS animations.</em>

[caption id="attachment_1091" align="aligncenter" width="322" caption="Android flaunting it&#39;s CSS animation support. But not so fast - there&#39;s more to it than this."]<a href="http://daneden.me/wp-content/uploads/2011/12/android.png"><img class="size-full wp-image-1091" title="Android flaunting it's CSS animation support" src="http://daneden.me/wp-content/uploads/2011/12/android.png" alt="" width="322" height="482" /></a>[/caption]

<strong>That's crazy talk, Dan!</strong> I hear you say. Open up any Android 2.0+ device and check out this <a href="http://daneden.me/labs/featuretest/">feature detection page.</a> Sitting, quite proudly, will be the words "css animation" - <a href="http://modernizr.com">Modernizr</a> says it's fully supported. So over you go to your CSS file and pump in a bunch of amazing CSS animations to make your website fly. Back to the Droid we go, and what do we find?

<!--more-->

[caption id="attachment_1092" align="aligncenter" width="322" caption="These aren&#39;t the Androids we&#39;re looking for."]<a href="http://daneden.me/wp-content/uploads/2011/12/animate.png"><img class="size-full wp-image-1092" title="Animate.css won't show here!" src="http://daneden.me/wp-content/uploads/2011/12/animate.png" alt="" width="322" height="482" /></a>[/caption]

We find absolutely nothing.

Here's the thing: CSS animations are supported by Android devices - but <strong>only if a single property is changed.</strong> As soon as you try to animate more than one property at once, the entire element disappears. In non-native Android browsers, the element will be visible for the duration of the animation, but will hide immediately after it's finished. This is true for (as far as I know) all Android devices below 4.0. Testing for 4.0 is yet to be done.

So what can we do? Well, if you're only animating a single property, such as opacity or transform, that's fine. Nothing to worry about. However, for more than one property, you'll need to put each of the properties into their own keyframe declaration. Here's a handy example:
<pre class="prettyprint">@-webkit-keyframes myAnimation {
    from {
        opacity: 0;
        -webkit-transform: translateY(-20px);
    }

    to {
        opacity: 1;
        -webkit-transform: translateY(0);
    }
}

/* That animation won't work. But, if we put each property into it's own keyframe declaration, it will work. */

@-webkit-keyframes a-opacity {
    from { opacity: 0; }
      to { opacity: 1; }
}

@-webkit-keyframes a-transform {
    from { -webkit-transform: translateY(-20px); }
      to { -webkit-transform: translateY(  0  ); }
}</pre>
This, my friends, is a very real and serious issue. The Android browser will always claim to support CSS animation. The compatibility charts will also praise Android for it's support. Web authors will write WebKit specific CSS animations which will work great on WebKit browsers - except on Android, where any content within the animated element will never see the light of day. There's no way around it, other than UA sniffing, which is undesirable to say the least.

What needs to happen, more than anything at this stage, is for people to raise awareness of this issue. I hope this gets as far as the authors of sites such as Can I Use?, Modernizr et al so that we can make sure people are aware of the issue. Tread with caution, animation authors - and help spread the word!

<mark>Update: it turns out Android 4.0 <a href="http://yfrog.com/h346935364p">actually addresses</a> this issue. Still, we need to urge the authors of these resources to explicitly mention that full support isn't available in previous versions of Android.</mark>
