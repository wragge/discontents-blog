---
ID: 932
post_title: Embedded archives
author: Tim Sherratt
post_date: 2010-06-27 22:00:17
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/embedded-archives/
published: true
tmac_last_id:
  - "640027553751810048"
---
Some of you may have noticed that my [Hacking a research project][1] post featured a file from the [National Archives of Australia][2] embedded as a [Cooliris][3] widget. Huh? To jog your memory, here it is again: [caption align="aligncenter" width="460" caption="These certificates allowed non-white Australians travelling overseas to re-enter the country. NAA: ST84/1, 1906/21-30"][RAW] <img style="visibility:hidden;width:0px;height:0px;" border=0 width=0 height=0 src="http://counters.gigya.com/wildfire/IMP/CXNID=2000002.11NXC/bT\*xJmx\*PTEyNzY3NzEwMDA5MjQmcHQ9MTI3Njc3MTAwNTYyOSZwPTkwMjA1MSZkPSZnPTEmb2Y9MA==.gif" /> [/RAW][/caption] No, it's not just an image, it's a little 3D wall. You can pan and zoom to your heart's content. You can enlarge an image, view fullscreen -- you can even share an image via Twitter. Fun for all the family! Regular viewers will recall my previous encounters with CoolIris -- [Archives in 3D][4] and [CoolIris enabled scrapbook][5] -- but these relied on having the CoolIris plugin installed. The embeddable Flash version wouldn't work when the images were coming from the NAA because it upset Flash's cross-domain settings. So how did I get it to work? For various other projects I've been playing with simple image proxies using Python and Django, so I just applied the same principles. The image proxy makes it seem as if the images are coming from a local source, thus keeping Flash happy. Hurrah! I've added a few little tweaks, so you can now view any digitised file in the National Archives of Australia in a CoolIris wall. Just go the the [file browser page][6] and enter a barcode. Even better you can install a bookmarklet. Just drag this link to your bookmarks bar (or save as a favourite) -- [RAW][View on wall][7].[/RAW] Then go to an item page in [RecordSearch][8] and click on the bookmarklet for 3D magic. If you want to share a link to a file displayed in the 3D file browser, just use a url of the form: `http://wraggelabs.com/recordsearch/wall/[barcode]` -- where [barcode] is fairly obviously the barcode of the file you want to view. For example: 
*   <http://wraggelabs.com/recordsearch/wall/3445411/> If you want to embed one of the mini-walls in your blog post it's easy. Just go to the 

[CoolIris Express][9] site and create your own wall. When it asks you for content source, click on 'Media RSS' and then in the 'Feed URL' box put: `http://wraggelabs.com/recordsearch/rss/[barcode]` -- where [barcode] is... well, you know... I think this a pretty interesting way to view, browse and navigate digitised files. Using Flash, rather than a browser plugin makes it more accessible, but I'd still rather have something based on open software and standards. I think it won't be too long before we see something similar using Canvas and Javascript. That'll be really exciting.

 [1]: http://discontents.com.au/shed/experiments/hacking-a-research-project
 [2]: http://naa.gov.au/
 [3]: http://cooliris.com/
 [4]: http://discontents.com.au/shoebox/archives-shoebox/archives-in-3d
 [5]: http://discontents.com.au/shed/hacks/cooliris-enabled-scrapbook
 [6]: http://wraggelabs.com/recordsearch/wall/
 [7]: javascript:(function(){window.location='http://wraggelabs.com/recordsearch/wall/'+document.evaluate('//td[b="Barcode"]',document,null,XPathResult.FIRST_ORDERED_NODE_TYPE,null).singleNodeValue.lastChild.textContent})();
 [8]: http://naa.gov.au/collection/recordsearch/index.aspx
 [9]: http://www.cooliris.com/yoursite/express/