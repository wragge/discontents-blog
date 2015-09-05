---
ID: 727
post_title: Some archives hacking
author: Tim Sherratt
post_date: 2009-11-05 10:31:07
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/some-archives-hacking/
published: true
tmac_last_id:
  - "640027562060550144"
---
It's great to see that the National Archives of Australia has released a large swag of data through the new <a href="http://data.australia.gov.au/">data.australia.gov.au</a> site. In the <a href="http://data.australia.gov.au/84">Commonwealth Agencies</a> zip file you can find xml dumps of all the publicly accessible agency and series data in RecordSearch, as well as item data for series A1. This is the same data that Mitchell Whitelaw visualised so brilliantly in his <a href="http://visiblearchive.blogspot.com/">Visible Archive</a> project. There's also item data and images from series A3560 – the <a href="http://data.australia.gov.au/77">Mildenhall photographs of early Canberra</a>.

What's even more exciting is that people are already using this data. At the recent GovHack event in Canberra the <a href="http://catherinestyles.com/2009/11/02/wtfgd-first-steps/">What The Federal Government Does</a> team worked on visualising the activities of government by using functions data pulled from the agencies file. Another group has generated a really nice <a href="http://mildenhall.creativepossums.net/">tag cloud and photo gallery</a> from the Mildenhall data. With further GovHack sessions to follow and the <a href="http://mashupaustralia.org/">MashupAustralia</a> contest open until 13 November, let's hope for some more inspired archives hacking.

Seeing RecordSearch data out in the world like this reminded me of a little project I started a while back and then set aside. It was a simple PHP script that scraped data from RecordSearch and spat it out either as XML or JSON. Mitchell used a version of this script in his <a href="http://visiblearchive.blogspot.com/2009/08/exploring-a1-items-to-documents.html">A1 Explorer</a> in order to find out the number of pages in each digitised file.

I've now expanded and improved the script so that it provides data on items, series, agencies and persons. The output includes all the basic fields as well as links between entities – such as related series, controlling agencies etc. As an added bonus you also get some useful totals (where they're available): items include the number of pages, series include the number of items described on RecordSearch, and agencies include the number of series recorded. I've also fiddled with mod_rewrite to provide a more rest-ful interface.

For XML output use the url <strong>http://discontents.com.au/shed/rs/xml/ </strong>followed by the appropriate identifier – a barcode for an item, a CA number for an agency, a CP number for a person or a series number.

Some examples:
<ul>
	<li> Series A1 – <a href="http://discontents.com.au/shed/rs/xml/a1">http://discontents.com.au/shed/rs/xml/a1</a></li>
	<li>Item B2455, WRAGGE C L E – <a href="http://discontents.com.au/shed/rs/xml/3445411">http://discontents.com.au/shed/rs/xml/3445411</a></li>
	<li>CSIR Head Office – <a href="http://discontents.com.au/shed/rs/xml/CA+486">http://discontents.com.au/shed/rs/xml/CA+486</a></li>
	<li>Alfred Deakin – <a href="http://discontents.com.au/shed/rs/xml/CP+9">http://discontents.com.au/shed/rs/xml/CP+9</a></li>
</ul>
As you might have guessed, to get JSON output you just substitute 'json' for 'xml' in the url.

Being dependent on screen scraping, it's inherently a bit fragile, but I'm hoping it might be of some use. My intention was to use it to start exploring some new ways of using and interacting with the data. The code itself is <a href="http://bitbucket.org/wragge/rswrapper/">available at BitBucket</a>. It's not very elegant, but I don't want to spend much time cleaning it up at the moment. If it seems like it might be useful, I'll probably rewrite the whole thing in python and publish it through Google's AppEngine.