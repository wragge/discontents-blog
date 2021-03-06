---
ID: 1601
post_title: 'Extracting editorials #3'
author: Tim Sherratt
post_date: 2012-02-20 09:11:54
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/extracting-editorials-3/
published: true
tmac_last_id:
  - "640027537897340928"
---
By my own criteria I've already failed... I started this series of posts with the intention of documenting the process of finding and extracting editorials as I was actually doing the work. But here I am about to describe some work I finished a few weeks back. Oh well...

In my previous instalments (<a title="Extracting editorials #1" href="http://discontents.com.au/shoebox/digital-humanities/extracting-editorials-1">here</a> and <a title="Extracting editorials #2" href="http://discontents.com.au/shed/hacks/extracting-editorials-2">here</a>), I focused on the <em>Sydney Morning Herald.</em> Having continued the hunt for missing editorials I started in the last post, I've now got a CSV file with the urls of the first editorial published in every edition of the <em>SMH</em> from 1913. Good-o, I thought, I can now start harvesting and analysing some content.

But then ensued a crisis of faith. The whole point of this exercise was to be able to build up some comparisons  -- between newspapers, between states, between the city and the bush. But the process of actually finding the editorials seemed beset with difficulties. Could the rules I developed for the <em>SMH</em> be applied elsewhere? Could I ever assemble a useful set of editorials without large amounts of human intervention? I decided to try a few quick experiments to see whether the whole project was worth pursuing.

I started with a few assumptions:
<ol>
	<li>The first (and only the first) editorial in any issue is headed with the name of the newspaper.</li>
	<li>Editorials are published on even numbered pages.</li>
	<li>Editorials vary in length between about 100 and 1500 words.</li>
</ol>
These assumptions were based on my own experience as a long-time newspaper researcher and on some preliminary poking around. For example, when I looked at <em>The Argus</em> I noticed that editorials were typically followed by news summaries. Unfortunately, these are treated as a single article in Trove, resulting in large blocks of text that are only part editorial. By specifying an upper word limit I hoped to filter these sorts of articles out. Similarly, there are sometimes brief announcements or publication details headed with the name of the newspaper. The lower word limit was intended to exclude these.

The next step was to harvest every article from 1913 that was headed with the name of its publication. I created a script to generate a list of all the newspapers that published issues in 1913. Then I called my existing harvester to download all the matching articles and save the details to a series of CSV files -- one CSV file per newspaper.

In the previous instalment of this series I created a script to check the CSV output of my harvester for missing or duplicate dates. I extended this to perform a series of tests on each article based on the assumptions above. First, I filtered out articles on odd-numbered pages, then articles that were too short or too long. Finally I checked the remainder for missing or duplicate issue dates.

The details of the articles in each category were written out to JSON files. Using these files and a bit of JQuery magic I could quickly build a <a href="http://wraggelabs.com/shed/trove/editorials/">simple web interface</a> that allowed me to explore the results.

[caption id="attachment_1613" align="aligncenter" width="476" caption="Summary details of each newspaper"]<a href="http://wraggelabs.com/shed/trove/editorials/"><img class="size-full wp-image-1613" title="editorials-list-cropped" src="http://discontents.com.au/wp-content/uploads/2012/02/editorials-list-cropped.jpg" alt="" width="476" height="536" /></a>[/caption]

You can browse the summary results for the full list of newspapers, or you can drill down to view the actual articles assigned to each category.

[caption id="attachment_1616" align="aligncenter" width="520" caption="Full details"]<a href="http://discontents.com.au/wp-content/uploads/2012/02/editorials-details-cropped.jpg"><img class="size-large wp-image-1616" title="editorials-details-cropped" src="http://discontents.com.au/wp-content/uploads/2012/02/editorials-details-cropped-520x372.jpg" alt="" width="520" height="372" /></a>[/caption]

I'll save the full analysis for the next post, but if you play around with the results you quickly notice a few things. First, letters to the editor often include the name of the newspaper! If you look at <em>The Mercury</em>, for example, you'll notice I've identified 1057 potential editorials -- most of which are letters. Fortunately they should be fairly easy to filter out. In most cases the 'even numbers only' assumption worked pretty well, and the word length filters did remove quite a lot of false positives. There are still plenty of problems, but I'm encouraged enough to continue. Yes, there will be a Part #4!

&nbsp;