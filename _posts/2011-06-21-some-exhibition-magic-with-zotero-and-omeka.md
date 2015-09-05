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
[caption id="attachment_1220" align="alignright" width="243" caption="Letter from CKR Kilby (‘Parkwood’, Hall FCT)"][<img class="size-medium wp-image-1220" title="inigo-letter" src="http://discontents.com.au/wp-content/uploads/2011/06/inigo-letter-243x300.jpg" alt="" width="243" height="300" />][1][/caption] [RAW]One of my most exciting archival discoveries was a cache of letters written by farmers from across NSW in 1938. Seeking to marshal support for the long-range weather forecaster <a typeof="foaf:Person" property="foaf:name" content="Jones, Inigo" rel="foaf:isPrimaryTopicOf" href="http://nla.gov.au/nla.party-571417">Inigo Jones</a>, *The Land* newspaper asked it's readers to send their opinions of the 'weather prophet'. And they did. One hundred and two letters were received, and duly forwarded to the Minister for the Interior. These 102 letters now reside in the <a typeof="foaf:Organization" property="foaf:name" content="National Archives (Australia)" rel="foaf:isPrimaryTopicOf" href="http://nla.gov.au/nla.party-549486">National Archives of Australia</a>.[/RAW] I tell the full story of the newspaper's campaign in [Inigo Jones: The Weather Prophet][2]. but I've always wanted to do something more with the letters. Inspiration finally arrived this year when a conference on rural media was organised to mark the *The Land*'s centenary. I decided to create a little exhibition using the letters and, in doing so, provide myself with a platform for further research. 
### Step one: assembling the letters with Zotero I'd already asked for the file containing the letters to be digitised, so images of all of the letters were available through 

[RecordSearch][3]. [Zotero][4] ships with a RecordSearch translator that I wrote some years ago, so 102 clicks later, I'd captured both the metadata and all of the images into my own database. The Zotero translator saves individual pages with a generic title, so I then had to do some manual editing. I also had partial transcripts of the letters which I'd created during my original research. I simply cut and pasted the transcripts into a note field in Zotero and tidied them up. Pretty soon [my collection][5] was complete. 
### Step two: creating an exhibition with Omeka [caption id="attachment_1225" align="alignright" width="296" caption="The Weather Prophets"]

[<img class="size-medium wp-image-1225" title="inigo-omeka" src="http://discontents.com.au/wp-content/uploads/2011/06/inigo-omeka-296x300.jpg" alt="" width="296" height="300" />][6][/caption] I actually started building the exhibition during an [Omeka Bootcamp session][7] I ran at [THATCamp Melbourne][8]. Starting with nothing but a LAMP server and my Zotero library, I had the basics of site up within the hour. It was simply a matter of installing [Omeka][9], adding the [Zotero import plugin][10], creating an API key in my Zotero profile, and then pointing the Zotero import plugin to my collection. (The API key is necessary if you want to download files, such as my images.)  With a press of a button the internets started chugging away and pretty soon all the letters were in Omeka. Hey presto -- [instant exhibition][11]! With the framework built I could start to play a bit. First I installed Omeka's [geolocation plugin][12] and started mapping where the letters had come from. Google's geocoder did a pretty good job of finding many of the small country towns, but I also made use of Geoscience Australia's gazetteer. In the end, I managed to geolocate all but one letter. Hey presto -- [a map][13]! I thought the pre-installed 'Summer' theme suited my exhibition, but I did make a few minor tweaks here and there. This included adding some RDFa into the [list of references][14] (which were also imported from Zotero). 
### Step three: going deeper with Voyeur Tools [caption id="attachment_1230" align="alignright" width="300" caption="Word cloud of the letters created by Voyeur Tools"]

[<img class="size-medium wp-image-1230 " title="inigo-cloud" src="http://discontents.com.au/wp-content/uploads/2011/06/inigo-cloud-300x192.jpg" alt="" width="300" height="192" />][15][/caption] The transcripts of the letters were all available on the site, but I thought it would be interesting to analyse their content a bit more systematically. To do this, I exported the collection from Zotero and wrote a few lines of Python code to save each transcript in a separate text file, named after the letter's author. I could then zip up the transcripts and feed them to [Voyeur Tools][16]. Most of the letters are pretty short, so there's a limited amount to be gleaned from them in isolation. Voyeur Tools did, however, make it easy for me to explore further the prevalence of the phrase '[on the right track][17]'. What will be more interesting will be to compare the letters to other bodies of text about Inigo Jones, weather forecasting and rural life. I'm hoping [to start mining][18] some of this sort of material from the Trove newspapers database. 
### Next steps? Using Zotero , Omeka and Voyeur Tools it was quick and easy to build my own little research hub. It's still a work-in-progress of course -- that's the point! Now I can continue to assemble and analyse my sources, while giving my work a public face. Magic!

 [1]: http://theweatherprophets.org/items/show/77
 [2]: http://www.scribd.com/doc/48717640/Inigo-Jones-The-Weather-Prophet
 [3]: http://naa.gov.au/collection/recordsearch/index.aspx
 [4]: http://zotero.org
 [5]: http://www.zotero.org/wragge/items/collection/3CT9EJ2M
 [6]: http://theweatherprophets.org/
 [7]: http://www.thatcampmelbourne.org/registration/boot-camp-sessions/building-an-online-collection/
 [8]: http://www.thatcampmelbourne.org/
 [9]: http://omeka.org/
 [10]: http://omeka.org/codex/Plugins/ZoteroImport
 [11]: http://theweatherprophets.org/items/browse?collection=4
 [12]: http://omeka.org/codex/Plugins/Geolocation
 [13]: http://theweatherprophets.org/items/map
 [14]: http://theweatherprophets.org/items/browse?collection=5
 [15]: http://theweatherprophets.org/exhibits/show/inigo-jones/letters-to-the-land/cloud
 [16]: http://voyeurtools.org/
 [17]: http://theweatherprophets.org/exhibits/show/inigo-jones/letters-to-the-land/right-track
 [18]: http://discontents.com.au/shed/mining-the-treasures-of-trove-part-1