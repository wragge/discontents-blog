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
It's great to see that the National Archives of Australia has released a large swag of data through the new [data.australia.gov.au][1] site. In the [Commonwealth Agencies][2] zip file you can find xml dumps of all the publicly accessible agency and series data in RecordSearch, as well as item data for series A1. This is the same data that Mitchell Whitelaw visualised so brilliantly in his [Visible Archive][3] project. There's also item data and images from series A3560 – the [Mildenhall photographs of early Canberra][4]. What's even more exciting is that people are already using this data. At the recent GovHack event in Canberra the [What The Federal Government Does][5] team worked on visualising the activities of government by using functions data pulled from the agencies file. Another group has generated a really nice [tag cloud and photo gallery][6] from the Mildenhall data. With further GovHack sessions to follow and the [MashupAustralia][7] contest open until 13 November, let's hope for some more inspired archives hacking. Seeing RecordSearch data out in the world like this reminded me of a little project I started a while back and then set aside. It was a simple PHP script that scraped data from RecordSearch and spat it out either as XML or JSON. Mitchell used a version of this script in his [A1 Explorer][8] in order to find out the number of pages in each digitised file. I've now expanded and improved the script so that it provides data on items, series, agencies and persons. The output includes all the basic fields as well as links between entities – such as related series, controlling agencies etc. As an added bonus you also get some useful totals (where they're available): items include the number of pages, series include the number of items described on RecordSearch, and agencies include the number of series recorded. I've also fiddled with mod_rewrite to provide a more rest-ful interface. For XML output use the url **http://discontents.com.au/shed/rs/xml/ **followed by the appropriate identifier – a barcode for an item, a CA number for an agency, a CP number for a person or a series number. Some examples: 
*   Series A1 – <http://discontents.com.au/shed/rs/xml/a1>
*   Item B2455, WRAGGE C L E – <http://discontents.com.au/shed/rs/xml/3445411>
*   CSIR Head Office – <http://discontents.com.au/shed/rs/xml/CA+486>
*   Alfred Deakin – <http://discontents.com.au/shed/rs/xml/CP+9> As you might have guessed, to get JSON output you just substitute 'json' for 'xml' in the url. Being dependent on screen scraping, it's inherently a bit fragile, but I'm hoping it might be of some use. My intention was to use it to start exploring some new ways of using and interacting with the data. The code itself is 

[available at BitBucket][9]. It's not very elegant, but I don't want to spend much time cleaning it up at the moment. If it seems like it might be useful, I'll probably rewrite the whole thing in python and publish it through Google's AppEngine.

 [1]: http://data.australia.gov.au/
 [2]: http://data.australia.gov.au/84
 [3]: http://visiblearchive.blogspot.com/
 [4]: http://data.australia.gov.au/77
 [5]: http://catherinestyles.com/2009/11/02/wtfgd-first-steps/
 [6]: http://mildenhall.creativepossums.net/
 [7]: http://mashupaustralia.org/
 [8]: http://visiblearchive.blogspot.com/2009/08/exploring-a1-items-to-documents.html
 [9]: http://bitbucket.org/wragge/rswrapper/