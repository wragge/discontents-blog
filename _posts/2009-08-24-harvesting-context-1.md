---
ID: 670
post_title: 'Harvesting context #1: Flickr comments'
author: Tim Sherratt
post_date: 2009-08-24 09:57:52
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/harvesting-context-1/
published: true
tmac_last_id:
  - "640027563591532544"
---
Instead of idly waiting for visitors to stumble over their holdings on some lonely information by-way,  archives are starting to push their content out into the bustling metropolis of the social web. They are going where the people are. Photographic collections, in particular, are gaining new lives and new audiences thanks to Flickr.

But that's only part of the story. Released into the wild, these photos are slowly picking up the habits of the locals. They are making friends, building connections, even speaking with new accents and dialects. Commented, tagged, organised, linked – they are building new contexts for themselves outside of the cloying control of archival descriptive systems.

Unfortunately it seems there is often a chasm between the old lives of the photos, documented in databases and finding aids, and their new post-institutional careers. This is a pity because the new contexts they are gathering can help us both understand and find them. What can we do to overcome this divide? How could finding aids harvest and display the user-generated content that aggregates around collection items living in the outside world?

The good news is that the tools to start doing this already exist – Flickr has a <a href="http://www.flickr.com/services/api/">powerful API</a> that makes it easy to extract photo metadata. Time for a bit of experimenting...<!--more-->

The first result is a <a href="http://userscripts.org/scripts/show/56135">userscript that displays Flickr comments</a> in a number of collection databases. Just <a href="http://userscripts.org/about/installing">install it</a> and then try it out:
<ul>
	<li>National Archives of Australia Photosearch - <a href="http://naa12.naa.gov.au/scripts/SearchOld.asp?O=PSI&amp;Number=7802286">try it!</a></li>
	<li>State Records NSW Photo Investigator - <a href="http://investigator.records.nsw.gov.au/asp/photosearch/photo.asp?4481_a026_000090">try it!</a></li>
	<li>National Archives and Records Administration ARC - <a href="http://arcweb.archives.gov/arc/action/ExternalIdSearch?id=522882">try it!</a></li>
</ul>
[caption id="attachment_697" align="aligncenter" width="300" caption="Flickr comments in PhotoSearch"]<a href="http://discontents.com.au/wp-content/uploads/2009/08/photosearch.png"><img class="size-medium wp-image-697" title="Flickr comments in PhotoSearch" src="http://discontents.com.au/wp-content/uploads/2009/08/photosearch-300x199.png" alt="Flickr comments in PhotoSearch" width="300" height="199" /></a>[/caption]

Gory details follow...

So to begin with I thought I'd just harvest comments from Flickr and display them within existing collection interfaces. As before (<a href="http://discontents.com.au/shoebox/archives-shoebox/archives-in-3d">here</a> and <a href="http://discontents.com.au/shoebox/archives-shoebox/moa-buttons-galore">here</a>), <a href="https://addons.mozilla.org/firefox/addon/748">Greasemonkey</a> was my tool of choice for hacking finding aids. The plan was to trigger a Greasemonkey script when you arrive at a photo in a collection database, the script would then:
<ul>
	<li>extract a unique identifier for the photo that could be used to find it in Flickr</li>
	<li>send off a request through the Flickr API to see if the photo was there</li>
	<li>if so, then fire off another request to retrieve any comments</li>
	<li>format the comments and insert them at a suitable point in the DOM of the database page</li>
</ul>
Easy! Obviously for the script to work there needed to be a way of connecting entries in the database with photos on Flickr. In practice this means that the photos need to be described at item level, and that a unique identifier needs to be used somewhere in the description of the photo both on Flickr and in the collection database.

Any archive that meets these criteria is a candidate for inclusion. Only three pieces of information are necessary:
<ul>
	<li>the institution's Flickr id</li>
	<li>an expression to extract the identifier from the database page</li>
	<li>an expression to identify the point on the database page at which the comments should be inserted</li>
</ul>
The expressions could use XPath or regular expressions – whatever it takes to find the desired elements. I'm using <a href="http://jquery.com/">JQuery</a>, so that makes selecting elements a lot easier. For example, NARA ARC includes the item identifier in a div with the class 'arcID', so I just select that element using JQuery and then use regex matching to pull out the number:

[code language="javascript"]this.identifier = $('.arcID').text().match(/ARC Identifier (d+)/i)[1];[/code]

To start with I've included the databases of three institutions:
<ul>
	<li>the National Archives of Australia's <a href="http://naa.gov.au/collection/photosearch/index.aspx">PhotoSearch</a> database</li>
	<li>State Records of NSW's <a href="http://investigator.records.nsw.gov.au/asp/photosearch/introduction.htm">Photo Investigator</a></li>
	<li>the US National Archives and Records Administration's <a href="http://www.archives.gov/research/arc/">Archival Research Catalog</a></li>
</ul>
This is the code to save the settings for each institution:

[code language="javascript"]
if (document.location.href.match(/naa.gov.au/scripts/PhotoSearchItemDetail.asp/i)) {
this.name = 'NAA';
this.identifier = document.location.href.match(/M=0&B=(d+)/)[1];
this.flickrId = '24849862@N08';
this.position = 'table:last';
} else if (document.location.href.match(/records.nsw.gov.au/asp/photosearch/photo.asp?/i)) {
this.name = 'StateRecordsNSW';
this.identifier = document.location.href.match(/photo.asp?([dw_]+)/i)[1];
this.flickrId = '27331537@N06';
this.position = 'table:first';
} else if (document.location.href.match(/arcweb.archives.gov/arc/action/ShowFullRecord|arcweb.archives.gov/arc/action/ExternalIdSearch/i)) {
this.name = 'NARA';
this.identifier = $('.arcID').text().match(/ARC Identifier (d+)/i)[1];
this.flickrId = '35740357@N03';
this.position = '.genPad:first';
}
[/code]

From there it's just a matter of building the calls to the API using Greasemonkey's built-in  GM_xmlhttpRequest method. Once the comments are retrieved, they're given some basic formatting and inserted at the point in the DOM identified by the siteDetails.position property. Once again, JQuery greatly simplifies all the DOM manipulation. If there are no comments then a suitable message is inserted together with a link to the photo in Flickr. Finally some CSS is added to prettify it all a little bit.

You can <a href="http://userscripts.org/scripts/review/56135">view the full code</a> on the Userscripts site.

Of course, it would be good to have this sort of stuff happening on the server side. In fact, with a few small modifications, this script could just be dropped into the code of any of the collection databases I've used. But in the meantime, Greasemonkey gives us a chance to play around with some of the possibilities – to start thinking about what finding aids might be like.

So what's next? I'd like to do some playing around with tags and locations, perhaps using them to suggest related photos. I've also just realised that Flickr machine tags allow semantic markup... hmmm...

If you have any suggestions for databases to add to this script – let me know!