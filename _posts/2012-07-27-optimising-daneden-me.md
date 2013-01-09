---
layout: post
title: Optimising daneden.me
tags:
- Design
status: trash
type: post
published: false
meta:
  _edit_last: '1'
  _yoast_wpseo_linkdex: '0'
  _yoast_wpseo_meta-robots-noindex: '0'
  _yoast_wpseo_metakeywords: ''
  _yoast_wpseo_metadesc: ''
  _yoast_wpseo_title: ''
  _yoast_wpseo_meta-robots-adv: none
  _yoast_wpseo_canonical: ''
  _yoast_wpseo_redirect: ''
  _yoast_wpseo_meta-robots-nofollow: '0'
  _yoast_wpseo_focuskw: ''
  _wp_trash_meta_time: '1357727847'
  _wp_trash_meta_status: draft
---
Mobble plugin - cutting out extra resources eg ads, optimising large image output
Typekit async - stops Typekit from preventing the rest of the content from loading. However, FOUT is bad - though not as bad as no content
Removing Facebook - cuts down load by ~250k
Other optimisations - smush.it, one CSS file, scripts at foot, server-size gzip, some caching w/ cachebusting
If it wasn't a personal site? Caching, minifying (but with max.css link), CDN
