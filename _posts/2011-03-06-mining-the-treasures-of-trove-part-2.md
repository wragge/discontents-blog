---
ID: 1174
post_title: Mining the treasures of Trove (part 2)
author: Tim Sherratt
post_date: 2011-03-06 23:44:02
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/mining-the-treasures-of-trove-part-2/
published: true
tmac_last_id:
  - "640027547279843328"
---
One of the advantages of building something yourself is that if you're not happy with it you can tweak, change, modify and adapt until you are. But one of the disadvantages is that sometimes you get so caught up in all the tweaking, changing and adapting that you overlook a much simpler solution. So [I had a harvester][1] that could save the publication details and content of all the newspaper articles in a search on [Trove][2]. But the warm glow of self-satisfaction quickly began to fade as I started to think about how I wanted to use the content I was harvesting. The harvester saved the text of articles organised in directories by newspaper title. This seemed to make sense. It meant that you could easily analyse and compare the content of different newspapers. But what if you wanted to examine changes over time? In that case it'd be much easier if the articles were organised by year -- then I could just pull out the a folder from a particular year, feed it to [VoyeurTools][3], and start tracking the trends. There ensued some minor tinkering. As a result, you can now you can pass an additional option to [the harvest script][4], telling it whether to save the article texts and pdfs in directories by year or newspaper. Simply set the 'zip-directory-structure' option in harvest.ini to either 'title' or 'year'. If you're using the command-line you can use the '-d' flag to set your preference. Easy. But that set me wondering whether it might be possible to generate an overview, showing the number of articles matching a search over time. So I started on a modification of my harvest script that did just that -- cycling through the search results, adding up the numbers. It wasn't until I ran the new script for the first time that I realised there was a much simpler alternative. All I needed to do was repeat the search for each year in the search span and grab the total results value from the page. D'uh... So instead of sending hundreds or perhaps thousands of requests to Trove, all I needed was one for each year. From there it was easy and soon I had my first graph. [caption id="" align="aligncenter" width="500" caption="My first graph: Chinese in Australia (The Chinese Australian expert in my house predicted the 1888 peak.) "][<img title="Chinese in Australia - Trove graph" src="http://farm6.static.flickr.com/5180/5455553450_9fbd539d2f.jpg" alt="" width="500" height="330" />][5][/caption] I was pretty pleased with that, but of course the raw numbers of articles on their own are rather misleading. The more interesting question was what proportion of the total number of articles for that year the search represents. Another quick tweak and I was grabbing the overall totals and calculating the proportions. [caption id="" align="aligncenter" width="500" caption="Total numbers versus proportions -- Chinese in Australia #2"][<img title="Trove graph - Chinese in Australia with proportions" src="http://farm6.static.flickr.com/5100/5455948202_5174a7a3de.jpg" alt="" width="500" height="336" />][6][/caption] At this point I invited my Twitter followers to suggest some possible topics -- you can [see the results on Flickr][7]. But what do the peaks and troughs represent? I wanted to use the graphs as a way of exploring the content itself. This was possible as I'd saved the data as JSON and used [jqPlot][8] to create the graphs in an ordinary HTML page. Courtesy of some clever hooks in the backend of jqPlot I could capture the value of any point as it was clicked. That gave me the year, so all I had to do was combine this with the search keyword values and send off a request to [Trove][2]. So now instead of just looking at the graphs, you could explore them. [caption id="attachment_1185" align="aligncenter" width="300" caption="Explore -- Chinese in Australia #3"][<img class="size-medium wp-image-1185" title="chinese-graph" src="http://discontents.com.au/wp-content/uploads/2011/03/chinese-graph-300x218.png" alt="" width="300" height="218" />][9][/caption] Perhaps you're wondering how I managed to pull the Trove results into the page? Just a bit of simple AJAX magic combined with my own [unofficial Trove API][10]. (More about that in the next exciting installment!) I've created a [little gallery of graphs][11] to explore. I'm still open to suggestions! The code for gathering the data is all on [Bitbucket][4], so start building your own. Just run the 'do_totals.py' script in the bin directory from the command line. The script takes two flags: 
*   -q (--query) the url of your Trove search (compulsory)
*   -f (--filename) the path and filename for your data file (don't include an extension) The script will create a javascript file containing two JSON objects, 'totals' and 'ratios'. These can then be fed to jqPlot. View the source of one of my interactive graphs to see how. Of course it would be really nice to create a web service where people could create, share, compare and combine their graphs -- but that might have to await a generous benefactor... 

<p style="text-align: center;">
</p>

 [1]: http://discontents.com.au/shed/mining-the-treasures-of-trove-part-1
 [2]: http://trove.nla.gov.au/newspaper?q=
 [3]: http://voyeurtools.org/
 [4]: https://bitbucket.org/wragge/trove-tools/overview
 [5]: http://www.flickr.com/photos/55336121@N00/5455553450/
 [6]: http://www.flickr.com/photos/55336121@N00/5455948202/
 [7]: http://www.flickr.com/photos/55336121@N00/sets/72157626078999182/
 [8]: http://www.jqplot.com/
 [9]: http://wraggelabs.com/shed/trove/graphs/chinese.html
 [10]: http://wraggelabs.appspot.com/api/newspapers/
 [11]: http://wraggelabs.com/shed/trove/graphs/