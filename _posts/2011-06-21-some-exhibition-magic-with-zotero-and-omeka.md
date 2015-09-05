---
ID: 1207
post_title: >
  Some exhibition magic with Zotero and
  Omeka
author: Tim Sherratt
post_date: 2011-06-21 09:21:17
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/some-exhibition-magic-with-zotero-and-omeka/
published: true
tmac_last_id:
  - "640027543794491392"
---
[caption id="attachment_1220" align="alignright" width="243" caption="Letter from CKR Kilby (‘Parkwood’, Hall FCT)"]<a href="http://theweatherprophets.org/items/show/77"><img class="size-medium wp-image-1220" title="inigo-letter" src="http://discontents.com.au/wp-content/uploads/2011/06/inigo-letter-243x300.jpg" alt="" width="243" height="300" /></a>[/caption]

[RAW]One of my most exciting archival discoveries was a cache of letters written by farmers from across NSW in 1938. Seeking to marshal support for the long-range weather forecaster <a typeof="foaf:Person" property="foaf:name" content="Jones, Inigo" rel="foaf:isPrimaryTopicOf" href="http://nla.gov.au/nla.party-571417">Inigo Jones</a>, <em>The Land</em> newspaper asked it's readers to send their opinions of the 'weather prophet'. And they did. One hundred and two letters were received, and duly forwarded to the Minister for the Interior. These 102 letters now reside in the <a typeof="foaf:Organization" property="foaf:name" content="National Archives (Australia)" rel="foaf:isPrimaryTopicOf" href="http://nla.gov.au/nla.party-549486">National Archives of Australia</a>.[/RAW]

I tell the full story of the newspaper's campaign in <a href="http://www.scribd.com/doc/48717640/Inigo-Jones-The-Weather-Prophet">Inigo Jones: The Weather Prophet</a>. but I've always wanted to do something more with the letters. Inspiration finally arrived this year when a conference on rural media was organised to mark the <em>The Land</em>'s centenary. I decided to create a little exhibition using the letters and, in doing so, provide myself with a platform for further research.
<h3>Step one: assembling the letters with Zotero</h3>
I'd already asked for the file containing the letters to be digitised, so images of all of the letters were available through <a href="http://naa.gov.au/collection/recordsearch/index.aspx">RecordSearch</a>. <a href="http://zotero.org">Zotero</a> ships with a RecordSearch translator that I wrote some years ago, so 102 clicks later, I'd captured both the metadata and all of the images into my own database.

The Zotero translator saves individual pages with a generic title, so I then had to do some manual editing. I also had partial transcripts of the letters which I'd created during my original research. I simply cut and pasted the transcripts into a note field in Zotero and tidied them up. Pretty soon <a href="http://www.zotero.org/wragge/items/collection/3CT9EJ2M">my collection</a> was complete.
<h3>Step two: creating an exhibition with Omeka</h3>
[caption id="attachment_1225" align="alignright" width="296" caption="The Weather Prophets"]<a href="http://theweatherprophets.org/"><img class="size-medium wp-image-1225" title="inigo-omeka" src="http://discontents.com.au/wp-content/uploads/2011/06/inigo-omeka-296x300.jpg" alt="" width="296" height="300" /></a>[/caption]

I actually started building the exhibition during an <a href="http://www.thatcampmelbourne.org/registration/boot-camp-sessions/building-an-online-collection/">Omeka Bootcamp session</a> I ran at <a href="http://www.thatcampmelbourne.org/">THATCamp Melbourne</a>. Starting with nothing but a LAMP server and my Zotero library, I had the basics of site up within the hour.

It was simply a matter of installing <a href="http://omeka.org/">Omeka</a>, adding the <a href="http://omeka.org/codex/Plugins/ZoteroImport">Zotero import plugin</a>, creating an API key in my Zotero profile, and then pointing the Zotero import plugin to my collection. (The API key is necessary if you want to download files, such as my images.)  With a press of a button the internets started chugging away and pretty soon all the letters were in Omeka. Hey presto -- <a href="http://theweatherprophets.org/items/browse?collection=4">instant exhibition</a>!

With the framework built I could start to play a bit. First I installed Omeka's <a href="http://omeka.org/codex/Plugins/Geolocation">geolocation plugin</a> and started mapping where the letters had come from. Google's geocoder did a pretty good job of finding many of the small country towns, but I also made use of Geoscience Australia's gazetteer. In the end, I managed to geolocate all but one letter. Hey presto -- <a href="http://theweatherprophets.org/items/map">a map</a>!

I thought the pre-installed 'Summer' theme suited my exhibition, but I did make a few minor tweaks here and there. This included adding some RDFa into the <a href="http://theweatherprophets.org/items/browse?collection=5">list of references</a> (which were also imported from Zotero).
<h3>Step three: going deeper with Voyeur Tools</h3>
[caption id="attachment_1230" align="alignright" width="300" caption="Word cloud of the letters created by Voyeur Tools"]<a href="http://theweatherprophets.org/exhibits/show/inigo-jones/letters-to-the-land/cloud"><img class="size-medium wp-image-1230 " title="inigo-cloud" src="http://discontents.com.au/wp-content/uploads/2011/06/inigo-cloud-300x192.jpg" alt="" width="300" height="192" /></a>[/caption]

The transcripts of the letters were all available on the site, but I thought it would be interesting to analyse their content a bit more systematically. To do this, I exported the collection from Zotero and wrote a few lines of Python code to save each transcript in a separate text file, named after the letter's author. I could then zip up the transcripts and feed them to <a href="http://voyeurtools.org/">Voyeur Tools</a>.

Most of the letters are pretty short, so there's a limited amount to be gleaned from them in isolation. Voyeur Tools did, however, make it easy for me to explore further the prevalence of the phrase '<a href="http://theweatherprophets.org/exhibits/show/inigo-jones/letters-to-the-land/right-track">on the right track</a>'.

What will be more interesting will be to compare the letters to other bodies of text about Inigo Jones, weather forecasting and rural life. I'm hoping <a href="http://discontents.com.au/shed/mining-the-treasures-of-trove-part-1">to start mining</a> some of this sort of material from the Trove newspapers database.

<h3>Next steps?</h3>
Using Zotero , Omeka and Voyeur Tools it was quick and easy to build my own little research hub. It's still a work-in-progress of course -- that's the point! Now I can continue to assemble and analyse my sources, while giving my work a public face. Magic!