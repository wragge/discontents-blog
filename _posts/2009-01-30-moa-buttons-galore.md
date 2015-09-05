---
ID: 626
post_title: MoA buttons galore
author: Tim Sherratt
post_date: 2009-01-30 16:41:40
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/moa-buttons-galore/
published: true
tmac_last_id:
  - "640027563591532544"
---
<a href="http://mappingouranzacs.naa.gov.au/">Mapping our Anzacs</a>, in case you don't know, provides a Google map interface to the 375,000+ WWI service records held by the National Archives of Australia. Amongst other other things, you can add <a href="http://our-anzacs.tumblr.com/">scrapbook posts</a> to individual entries and create tributes. It's meant to encourage exploration, so go on... explore!

If you'll do, you'll notice that there are direct links into the National Archives' database <a href="http://naa.gov.au/collection/recordsearch/index.aspx">RecordSearch</a>. However, there are currently no links going to other way. Why does this matter? Well perhaps you'd like to use NameSearch to find an individual record, but then add a scrapbook post in Mapping our Anzacs. Up until now you had to find them all over again. But not any more...

Introducing our new range of 'View in Mapping our Anzacs' buttons:
<ul>
	<li>For the discerning Firefox devotee we have a <a href="http://userscripts.org/scripts/show/41314">Greasemonkey userscript</a> which adds a button to the RecordSearch item details page.</li>
	<li>For fashion-challenged IE user we have a bookmarklet. Just right click on this link – <a href="javascript:if%20(document.location.href.match(/ItemDetail.asp/i)){var%20matches=document.body.innerHTML.match(/SeriesDetail.asp?M=0&amp;amp;B=([dw/]+)/i);series=matches[1];var%20matches=document.body.innerHTML.match(/Barcode</B><BR>(d+)</i);barcode=matches[1];if%20(series=='B2455'){window.location='http://mappingouranzacs.naa.gov.au/details-permalink.aspx?barcode_no='+barcode;}}">View in Mapping our Anzacs</a> – and save it as a favourite in your 'Links' folder (you may need to enable the 'Links' toolbar first by checking Tools > Toolbars > Links.)</li>
</ul>
Yes, it's true... you could use the Bookmarklet with Firefox (just drag it to your bookmarks toolbar), but Greasemonkey is so much more chic.

Once you're fully button-enabled just head into RecordSearch, find an item in series B2455 (the WWI service records) and click! Hurrah! You will be instantly transported to Mapping our Anzacs.

You can test out your new button by heading here:
<ul>
<li><a href="http://www.aa.gov.au/cgi-bin/Search?O=I&Number=3445411">B2455, WRAGGE C L E</a></li>
</ul>

