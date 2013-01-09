---
layout: post
title: A Smoother Page Load (via @jonikorpi)
tags:
- Code
- Design
- Development
- span_all
status: publish
type: post
published: true
meta:
  yourls_tweeted: '1'
  yourls_shorturl: http://drwys.so/16
  views: '142'
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
  dsq_thread_id: '459142378'
---
<a title="Joni Korpi" href="http://jonikorpi.com">Joni Korpi</a>, creator of the LESS framework, offered a great little tutorial on avoiding the Flash of Unstyled Text (FLOUT) that comes with web fonts, including from services such as Typekit.

While loading the fonts, Typekit adds a <code>.wf-loading</code> class to the page. By hiding the text elements initially, then having them switch back to full opacity when it's finished loading - with a nice little transition - you can fade your page in gracefully.

See his brilliant article <a title="A Smoother Page Load - Joni Korpi" href="http://jonikorpi.com/a-smoother-page-load/">right here</a>.
