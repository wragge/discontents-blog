---
ID: 1621
post_title: QueryPicNZ
author: Tim Sherratt
post_date: 2012-04-01 13:17:02
post_excerpt: ""
layout: post
permalink: http://discontents.com.au/querypicnz/
published: true
tmac_last_id:
  - "640027535368060929"
  - "640027535368060929"
---
You may have noticed I have a bit on an interest in exploring ways of using digitised historical newspapers. In the last year or so I've spent a lot of time <a href="http://discontents.com.au/tag/trove">scraping, mining, processing and visualising</a> content from the Trove collection of digitised Australian newspapers. But what about other countries?

Recently I was invited to a <a href="http://victoria.ac.nz/wtapress/research/digital-history-workshop-2012">digital history workshop</a> organised by Sydney Shep (<a href="https://twitter.com/#!/nzsydney">@nzsydney</a>) at the Victoria University of Wellington. In between sessions I started to play with the <a href="http://www.digitalnz.org/developers">DigitalNZ API</a> guided by Chris McDowall (<a href="https://twitter.com/#!/fogonwater">@fogonwater</a>). In anticipation of the forthcoming Trove API I'd already done a bit of work converting <a title="QueryPic" href="http://discontents.com.au/shed/hacks/querypic">QueryPic</a> to run in the browser. It didn't take long to adapt this to work with New Zealand newspapers available through <a href="http://paperspast.natlib.govt.nz/cgi-bin/paperspast">Papers Past</a>.

<strong>So presenting for your enjoyment and education... <a href="http://wraggelabs.com/shed/querypicnz">QueryPicNZ</a>.</strong>

[caption id="attachment_1641" align="aligncenter" width="520" caption="Wind, rain and snow in QueryPicNZ"]<a href="http://wraggelabs.com/shed/querypicnz/?q=wind&amp;q=rain&amp;q=snow"><img class="size-large wp-image-1641" title="Screen Shot 2012-04-01 at 1.07.28 PM" src="http://discontents.com.au/wp-content/uploads/2012/04/Screen-Shot-2012-04-01-at-1.07.28-PM-520x367.png" alt="" width="520" height="367" /></a>[/caption]

Like <a title="QueryPic" href="http://discontents.com.au/shed/hacks/querypic">QueryPic</a>, the New Zealand version graphs newspaper search results over time. But thanks to the DigitalNZ API it has a number of advantages:
<ul>
	<li>it runs in your browser -- no need to download or run any scripts</li>
	<li>results appear almost instantly</li>
	<li>easy to combine queries -- just search on a new word or phrase</li>
	<li>easy to remove queries -- just use the 'Clear last' button</li>
	<li>easy to share -- just copy the provided link or use the Tweet button</li>
</ul>
It's limited to simple word or phrase searches at the moment, but eventually I'll add the ability to process more sophisticated queries. I also want to add a way of saving, sharing and citing graphs. For now the 'share' link simply regenerates the graph, so if the content has changed the result could well be different.

The code is <a href="https://github.com/wragge/QueryPicNZ">available on GitHub</a>.

Ultimately, I want to combine Trove and Papers Past so that you can query and combine content from either Australia or New Zealand... perhaps even other countries?