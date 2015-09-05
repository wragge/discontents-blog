---
ID: 1462
post_title: 'Extracting editorials #1'
author: Tim Sherratt
post_date: 2011-11-21 23:24:29
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/extracting-editorials-1/
published: true
tmac_last_id:
  - "640027540644564992"
---
<a href="http://nla.gov.au/nla.news-article15387373"><img class="alignright size-full wp-image-1468" title="smh_editorial" src="http://discontents.com.au/wp-content/uploads/2011/11/smh_editorial.png" alt="" width="249" height="328" /></a>

In <a href="http://writinghistory.trincoll.edu/data/hermeneutics-of-data-and-historical-writing-gibbs-owens/">their chapter</a> in <em>Writing History in the Digital Age</em>, Trevor Owens and Fred Gibbs encourage historians to write about the ways they work with data -- to document their methods, their working assumptions, their dead ends and their discoveries. It's an important argument and one that makes me wonder again <a title="Every story has a beginning" href="http://discontents.com.au/shoebox/every-story-has-a-beginning">about forms of publication</a> that might integrate narrative, methods and sources.

In the meantime though we have blogs. My problem is that I'm easily bored so by the time I get to the end of a project or experiment I'm already thinking about the next one. Going back and trying to write things up seems a bit of a chore (which is why I'm always way behind in my blog writing). Also leaving the writing to the end means that I tend to take shortcuts -- leaving out some of the 'boring' procedural stuff or the 'stupid' ideas that just didn't work.

But Trevor and Fred's chapter has made me think I should be a bit more diligent, so as I start a new series of text-mining experiments I've decided to write things up as I'm doing them. So be warned, this could get messy...

So what do I want to do? You might not be surprised to learn that it's another Trove newspaper database experiment. I want to see if I can harvest newspaper editorials over a certain period and then analyse these to build up a picture of what issues, events or ideas were perceived as important. As I'm currently looking at ways of harvesting digital sources relating to 1913 for an exhibition being developed by the <a href="http://nma.gov.au">National Museum of Australia</a>, I'm going to start by focusing on 1913.

But editorials are opinion pieces, wouldn't it be better to harvest 'news' articles?

First of all, I'm thinking that editorials will be fairly easy to identify and extract -- there's no real way in Trove to separate out current news from other sorts of articles. Secondly, I'm assuming that the issues that make it into editorials have some importance attached to them. Attached by whom, you may well ask -- whose voice is being represented in the editorial? This is an important question and I'm thinking that it could be explored in interesting ways by harvesting editorials from a range of papers and regions. Thirdly, finding the editorials might actually help me find the major news articles, simply because in this period the main news stories were often on the page after the editorials.

So how do I find them? Looking at the <em>Sydney Morning Herald</em> for 1913, you can see that the editorials follow a regular pattern:
<ul>
	<li>the first editorial is always headed with the name of the paper and the date, followed by the title</li>
	<li>subsequent editorials that follow have a title but no subtitle (most other types of articles have a subtitle)</li>
	<li>editorials are published on an even-numbered page, usually about half way through the newspaper</li>
</ul>
To check this I conducted a search for<a href="http://trove.nla.gov.au/newspaper/result?l-textSearchScope=headings+only%7Cscope%3Aheadings&amp;l-title=The+Sydney+Morning+Herald...%7Ctitleid%3A35&amp;l-word=*ignore*%7C*ignore*&amp;fromyyyy=1913&amp;toyyyy=1913&amp;sortby=dateAsc&amp;q=fulltext%3A%22The+Sydney+Morning+Herald%22&amp;l-category=Article%7Ccategory%3AArticle&amp;s=0"> articles including 'The Sydney Morning Herald' in their title</a>. The search returns 335 results. Of course we'd expect there to be 312 (6 x 52), but it looks like there's quite a few false positives and some days missing altogether (presumably due to OCR errors). You can see there's a fair bit of consistency in the pages that editorials appear on, but it doesn't quite seem consistent enough to rely on. So I've decided that as a first step I'll <a title="Mining the treasures of Trove (part 1)" href="http://discontents.com.au/shed/mining-the-treasures-of-trove-part-1">harvest</a> all the articles from this query. I'll then do some manual cleaning to remove the articles that aren't editorials and try and identify and retrieve the missing days.

Remember, this won't give me all the editorials, only the first editorial from each day. To get all the editorials, I'll have to write a new script that will take this first result set, retrieve all the articles from the editorial page and then try to work out which of the articles are editorials -- they should be the ones that come after the first editorial and have no subtitle. Or that's the theory.

I've harvested the query. You can <a href="https://docs.google.com/spreadsheet/ccc?key=0AoLhQYoG1_hmdDE3MU1PNkc1YU9FOGNHajJrWjNwYWc">view the spreadsheet</a> on Google Docs if you feel so moved.

[After I wrote the sentence above I checked the CSV file properly and realised I'd stuffed up. There's a bit of a bug in my harvester that means if the query string you use includes a start value, the harvester wil retrieve the same page of results over and over again... I really need to fix that. :-) I'm now running it again. You wanted warts and all, right?]

[After I wrote the paragraph above I checked my new harvest and realised I'd stuffed up again. There were only half as many results as there should have been! So I poked around and realised some recent changes I'd made to the harvest script meant I was only getting odd numbered results (I was incrementing the row value twice). A lesson in what happens when you do this stuff late at night... Trying again. ]
<div>I'm not sure when I'll have time to do the cleaning. But hey folks this is what research is like for people like me who have to try and fit it in around the edges of their lives. You can expect posts to come in sudden bursts and then dry up altogether for long periods as other priorities intrude.</div>
&nbsp;