---
ID: 1655
post_title: >
  The new QueryPic (or what a difference
  an API makes)
author: Tim Sherratt
post_date: 2012-04-17 23:06:55
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/the-new-querypic-or-what-a-difference-an-api-makes/
published: true
tmac_last_id:
  - "640027535368060929"
---
It seems a bit late to be introducing the newest version of [QueryPic][1]. Folks are already using it to explore the contents of digitised newspapers made available through [Trove][2] and [Papers Past][3]. Some, like the [National Library of New Zealand][4], [Andrew S. Bowman][5] and the [Carnamah Historical Society][6] are already blogging about it. But I suppose I'd better document a few things... As I noted in my [post about QueryPicNZ][7] (yes I now have a rather confusing proliferation of QueryPics), I was waiting for the Trove API to become public. Last week I noticed a little 'API' link pop up in the Trove footer and so I set to work... [caption id="attachment_1662" align="aligncenter" width="520" caption=""The past" versus "the future" in the new QueryPic"][<img class="size-large wp-image-1662" title="new_querypic" src="http://discontents.com.au/wp-content/uploads/2012/04/new_querypic-520x477.png" alt="" width="520" height="477" />][8][/caption] My [original version of QueryPic][9] ([recently reviewed][10] in the *Journal of the Digital Humanities*) used a series of Python scripts to harvest and scrape content from the Trove web pages. This meant that you had to download the scripts and be code-confident enough to run them in a terminal. It's still a useful tool and I'll be updating it as well, but I wanted to create something quicker and simpler that encouraged people to explore and play. The latest version of [QueryPic][1] (QueryPic+, QueryPic Web, <del>QueryPic 2.0</del>?) simply runs in your browser. It uses JQuery to grab data on the fly from the [Trove][11] and [DigitalNZ][12] APIs. Like previous versions, it uses the [HighCharts][13] library to turn the data into pretty graphs. What does it do? It's really pretty basic. QueryPic just displays the number of articles matching your search query over time. By default, these are displayed as a proportion of the total articles available for that year, but a dropdown field lets you switch to view the raw numbers. It's simple, but it's also remarkably evocative, suggestive and fun. **[Just try it!][1]** Why stop at just one query? To compare frequency patterns you can add as many as you like. Just keep entering new words or phrases. If you notice an interesting peak or trough you can just click on it and another API request will be fired off to retrieve the first 20 matching articles. So it's also a new way of exploring the newspaper databases themselves. There are plenty of limitations -- not all newspapers are digitised, for example, and the quality of the OCR is patchy. The [National Library of New Zealand's post][4] does a great job summing up a number of issues relating to Papers Past. It's not magic, it's not perfect, but is it useful? I think so. Tasks for the future: 
*   Create some sort of backend that makes it easy to save , share and cite your query data. The 'share' link just regenerates the graph which, of course, might change as new articles are added to the databases.
*   Make it possible to add more complex queries -- I want to keep the interface simple, so I'll probably create a bookmarklet to take any Trove or Papers Past query and display it using QueryPic.
*   As I mentioned over at the [WraggeLabs Emporium][14], I intend to rewrite my various Trove tools to work with the new API. This will include the classic Python version of QueryPic. I still think it's useful for harvesting your own data.

<div>
  The <a href="https://github.com/wragge/QueryPic">code</a> is on my GitHub site and you can also follow updates at the <a href="http://wraggelabs.com/emporium/trove-tools/newspaper-search-summariser/">QueryPic page</a> in the WraggeLabs Emporium.
</div>  

 [1]: http://wraggelabs.com/shed/querypic/
 [2]: http://trove.nla.gov.au/newspaper/
 [3]: http://paperspast.natlib.govt.nz/cgi-bin/paperspast
 [4]: http://beta.natlib.govt.nz/blog/a-tale-of-two-islands
 [5]: http://andrew-s-bowman.blogspot.com.au/2012/04/querypic-new-tool-for-historical.html
 [6]: http://carnamah.blogspot.com.au/2012/04/mentions-of-carnamah-in-australian.html
 [7]: http://discontents.com.au/shed/experiments/querypicnz "QueryPicNZ"
 [8]: http://wraggelabs.com/shed/querypic/?q=%22the%20past%22|aus&q=%22the%20future%22|aus
 [9]: http://discontents.com.au/shed/hacks/querypic "QueryPic"
 [10]: http://journalofdigitalhumanities.org/1-1/reviews/querypic/
 [11]: http://trove.nla.gov.au/general/api
 [12]: http://digitalnz.org.nz/
 [13]: http://www.highcharts.com/
 [14]: http://wraggelabs.com/emporium/2012/04/the-new-api-powered-future/