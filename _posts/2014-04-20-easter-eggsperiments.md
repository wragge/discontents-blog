---
ID: 2273
post_title: Easter eggsperiments
author: Tim Sherratt
post_date: 2014-04-20 23:23:13
post_excerpt: ""
layout:
  - default
permalink: >
  http://discontents.com.au/easter-eggsperiments/
published: true
hide_post_title:
  - default
unlink_post_title:
  - default
hide_post_meta:
  - default
hide_post_date:
  - default
hide_post_image:
  - 'yes'
unlink_post_image:
  - default
builder_switch_frontend:
  - "0"
post_image:
  - ""
tmac_last_id:
  - "640027508637724672"
content_width:
  - default_width
feature_size:
  - blank
---
No, nothing to do with Easter or eggs, but it's Easter Sunday and who can resist a good opportunity for a bad pun?

This is another catch-up post, pulling together some recent experiments. If nothing else, it'll help me keep track of things I'm otherwise likely to forget.
<h2 id="wwi">WWI Faces</h2>
In our last instalment I was <a title="Enriching WWI data with the Trove API" href="http://discontents.com.au/enriching-wwi-data-with-the-trove-api/">playing around with some WWI data</a> from the State Library of South Australia. I'm really pleased to report that SLSA staff have used my experiments to help them add Trove links to more than 6,000 of their <a href="http://www.catalog.slsa.sa.gov.au/search~S1/?searchtype=g&amp;searcharg=Heroes+of+the+Great+War&amp;searchscope=1&amp;sortdropdown=-&amp;SORT=D&amp;extended=0&amp;searchlimits=&amp;searchorigarg=gHeroes+of+the+Great+War">Heroes of the Great War</a> records. Here's <a href="http://www.catalog.slsa.sa.gov.au/record=b2556499~S1">an example</a> -- note the 'article' link which goes straight to a digitised newspaper article in Trove. With some good data and bit of API wrangling we've now established rich linkages between an important WWI resource and Trove. Win!

I've also continued my fiddling with articles from the Adelaide <em>Chronicle</em> as I start to think about how Trove's newspapers might be used in a WWI exhibition being developed by the National Library. At the end of my last post I'd created a list of articles from the <em>Chronicle</em> that were likely to include biographical details of WWI personnel. I knew that many of these included portrait photos, so I filtered them on Trove's built-in 'illustrated' facet and saved the page images for the remaining articles. You can browse the resulting <a href="https://www.dropbox.com/photos/album/PiQJmSJWRT5t02L">collection of pages</a> on Dropbox. As you can see there are indeed many portraits of service people.

So the next step was to try and extract the portraits from the pages. This was rather familiar territory, as I'd already used a facial detection script to create <a title="the real face of white australia" href="http://discontents.com.au/the-real-face-of-white-australia/">The Real Face of White Australia</a>. But I wasn't sure how the pattern recognition software would cope with the lower quality newspaper images. After getting all the necessary libraries installed (the hardest bit of the whole process), I pointed the script at the page images and... it worked!

[caption id="attachment_2275" align="aligncenter" width="1024"]<a href="http://discontents.com.au/wp-content/uploads/2014/04/wwi-faces.png"><img class="size-large wp-image-2275" src="http://discontents.com.au/wp-content/uploads/2014/04/wwi-faces-1024x695.png" alt="A small sample of the faces extracted from the Chronicle." width="1024" height="695" /></a> A small sample of the faces extracted from the Chronicle.[/caption]

From 141 pages I extracted 1,738 images, and most of them were faces. You can <a href="http://wraggelabs.com/shed/trove/faces/">browse all 1,738</a>, but be warned, I've just dumped them onto a single page and added a bit of Isotope magic -- so they'll take a fair while to load and your browser might object. You'll also notice that I haven't tried to filter out photos of non-service people, I just wanted to see if it worked. And it does. Even in this rough form you can sense some of the emotive power. What's really amazing is the way that even small images of faces in group photographs were identified. All I was aiming for at this stage was a proof of concept -- yes, I can extract photos of WWI service people from newspapers. Hmmm...
<h2 id="space">Trove in space</h2>
All the faces above were from one South Australian newspaper. Several years ago I worked on a project to <a title="Local heroes" href="http://discontents.com.au/local-heroes/">map places of birth and enlistment</a> of WWI service people, and while I have no interest in the national mythologies surrounding WWI, I do still wonder about the local impact of war -- all those small communities sending off their sons and daughters...

So I'm wondering whether we might be able to use the digitised newspapers in Trove to navigate <em>from place to face</em>. To choose a town anywhere in Australia, and present photographs of service personnel published in nearby newspapers.

I now know I can extract the photos, but how can we navigate Trove newspapers by location? Time for a new experiment...

The Trove API provides a <a href="http://api.trove.nla.gov.au/newspaper/titles?encoding=json">complete list of digitised newspaper titles</a>. You'll notice that some of the titles include a place name as part of the summary information in brackets, while many others will include place names in their titles, for example:
<ul>
	<li>Illawarra Daily Mercury (<span style="color: #ff0000;">Wollongong</span>, NSW : 1950 - 1954)</li>
	<li>Hawkesbury Herald (<span style="color: #ff0000;">Windsor</span>, NSW : 1902 - 1945)</li>
	<li><span style="color: #ff0000;">Kiama</span> Examiner (NSW : 1858 - 1859)</li>
	<li><span style="color: #ff0000;">Narromine</span> News and <span style="color: #ff0000;">Trangie</span> Advocate (NSW : 1898 - 1955)</li>
</ul>
I haven't had much luck getting automated named entity extraction tools to work on short text strings like this, so I decided to roll my own using Geoscience Australia's <a href="http://www.ga.gov.au/metadata-gateway/metadata/record/gcat_76695">Gazetteer of Australia 2012</a>. I opened up the GML file containing all Australian places and saved the populated locations to my own Mongo database. This gave me a handy place name database, complete with geo-locations.

Next I went to work on the newspaper titles. Extracting the places from the summary information was easy because they followed a regular pattern, but finding them in the body of the title was trickier. First I had to exclude those words that were obviously not place names. Aside from the usual stopwords ('and' and 'the'), there are many words that commonly occur in newspaper titles -- 'Herald', 'Star', 'Chronicle' etc. To find these words I pulled apart all the titles and calculated the frequency of every word. You can <a href="https://gist.github.com/wragge/11111579">explore the raw results</a> -- 'Advertiser' (116) wins by a large margin, with 'Times' (67) in second place. From these results I could create a list of words that I knew were not places and could safely be ignored.

Then it was just a matter of tokenising the titles (breaking them up into individual words), removing all the stopwords (the standard list and my special list), and then looking up the words in my place name database. I did this in two passes, first as bigrams (pairs of words), and then as single words -- this allowed me to find compound place names like 'North Melbourne'. The Trove API gives you s 'state' value for each title, so I could use this in the query to increase accuracy.

If I found a place name, I added the place details, including the latitude and longitude, to the title record from the API and included it in my own newspaper title database.

So I ended up to two databases -- one with geolocated places, and another with geolocated newspapers. That meant I could build <a href="http://damp-island-3738.herokuapp.com/">a simple interface</a> to find newspaper titles by place. It's nothing fancy -- just another proof of concept -- but it works pretty well. Just type in a place name and select a state and a query is run against the place name database. If the place is found then the latitude and longitude is fed to the titles database to find the closest newspapers. After removing some duplicates, the 10 nearest newspapers are displayed.

[caption id="attachment_2279" align="aligncenter" width="610"]<a href="http://damp-island-3738.herokuapp.com/"><img class="size-full wp-image-2279" src="http://discontents.com.au/wp-content/uploads/2014/04/Screen-Shot-2014-04-20-at-9.53.55-pm.png" alt="Find Trove newspapers by place" width="610" height="561" /></a> Find Trove newspapers by place[/caption]

Building some sort of map interface on top of this is pretty trivial. What's more important is to do some analysis of my place matching to see what I might have missed. But so far so good!
<h2 id="troveis">Trove is...</h2>
Trove is more than newspapers. This is a message the Trove team tries to emphasise at every opportunity. The digitised newspapers are an incredible resource of course, but there's so much other interesting stuff to explore.

To try and give a quick and easy introduction to this richness, I created a simple dashboard-type view of Trove, imaginatively titled <a href="http://troveis.dhistory.org/">Trove is...</a>

[caption id="attachment_2282" align="aligncenter" width="641"]<a href="http://troveis.dhistory.org/"><img class="size-full wp-image-2282" src="http://discontents.com.au/wp-content/uploads/2014/04/troveis-2.png" alt="What is Trove?" width="641" height="669" /></a> What is Trove?[/caption]

Trove is... gives a basic status report on each of the 1o Trove zones, with statistics updated daily (except for the archived websites as there's no API access at the moment). The BIG NUMBERS are counter-balanced by a single randomly-selected example from each zone. It's a summary, an overview, a portal and a snapshot. Reload the page and the zones will be reordered and the examples will change.

It's pretty simple, but I think it works quite well, and thanks to Twitter Bootstrap it looks really nice on my phone! But while the idea was simple, the implementation was pretty tricky -- particularly the balance between randomness and performance. If all the examples were truly random, drawn from the complete holdings to Trove on every page reload, you'd spend a lot of time watching spinning arrows waiting for content to appear. I tried a number of different approaches and finally settled on a system where random selections of 100 resources per zone are made every hour by background processes and cached. When you load the page, this cache is queried and an item selected. So if you keep hitting reload you'll probably notice that some examples reappear. It's random, but at any moment the pool of possibilities is quite limited. Come back later in the day and everything will be different.

Anyway, if anyone asks you what Trove is, you now know where to point them...
<h2 id="abcrn">Who listens to the radio?</h2>
After a lot of hard work, the Trove team was <a href="http://www.nla.gov.au/blogs/trove/2014/04/17/harvesting-radio-national">excited to announce recently</a> that more than 200,000 records from 54 ABC Radio National programs were available through Trove.

To make it a bit easier to explore this wonderful new content, I created a <a href="http://safe-headland-1733.herokuapp.com/">simple search interface.</a> All it really does is help you build a query using the RN program titles, and then sends the query off to Trove. Not fancy, but useful (my family motto).

Of course, I couldn't leave my Twitter bot family out of the action. <a href="https://twitter.com/TroveBot">@TroveBot</a> has been Radio National enabled. Just tweet the tag #abcrn at him to receive a randomly-selected Radio National story. To search for something amidst the RN records, just tweet a keyword or two and add the #abcrn tag to limit the results. Consult the <a href="https://github.com/wragge/trovebot">TroveBot manual</a> for complete operating instructions.
<h2 id="inaword">In a word...</h2>
But the Radio National content is not just findable through the Trove web interface -- all that lovely data is freely accessible through the Trove API. That includes just about every segment of every edition of the ABC's flagship current affairs programs, AM, PM, and The World Today from 1999 onwards. What sort of questions could you ask of this data?

I'll be writing something soon on the Trove blog about accessing these riches, but I couldn't resist having a play. So I harvested all the RN data via the API and built a new thing...

[caption id="attachment_2288" align="aligncenter" width="1024"]<a href="http://inaword.dhistory.org/"><img class="size-large wp-image-2288" src="http://discontents.com.au/wp-content/uploads/2014/04/Screen-Shot-2014-04-12-at-11.31.59-am-1024x368.png" alt="What's in a word?" width="1024" height="368" /></a> What's in a word?[/caption]

It's called <a href="http://inaword.dhistory.org/">In a word: Currents in Australian affairs, 2003–2013</a>, and for once it's quite well documented, so I won't go into details here. I'll just say that it's one of my favourite creations, and I hope you find it interesting.
<h2 id="tungwah">Addendum (21 April) -- The Tung Wah Newspaper Index</h2>
See, I told you I forget things...

I recently finished resurrecting the <a href="http://resources.chineseaustralia.org/tungwah/">Tung Wah Newspaper Index</a>. Kate has <a href="http://chineseaustralia.org/?p=2025">described the original project</a> on her blog, and there's a fair bit of contextual information on the site, so I won't go into details here. Suffice it to say it's an important resource for Chinese Australian history that had succumbed to technological decay.

The original FileMaker database has been MySqld, Solrised, and Bootstrapped to get it all working nicely. I also took the opportunity to introduce a bit of LOD love, with plenty of machine-readable data built-in.

The whole site follows an interface as API type pattern. So if you want a resource as JSON-LD, you just change the file extension to .json. To help you out, there are links at the bottom of each page to the various serialisations, and of course you can also use content negotiation to get what you're after. There's some examples of all this in the <a href="https://github.com/wragge/chaf-django/tree/master/chaf/tungwah">GitHub repository</a>, as well as a CSV dump of the whole database.

&nbsp;