---
ID: 1259
post_title: 'When did the &#8216;Great War&#8217; become the &#8216;First World War&#8217;?'
author: Tim Sherratt
post_date: 2011-08-29 23:38:38
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/when-did-the-great-war-become-the-first-world-war/
published: true
tmac_last_id:
  - "640027542410383360"
---
[caption id="attachment_1293" align="alignright" width="250" caption="Townsville Daily Bulletin, 9 December 1939"]<a href=" http://nla.gov.au/nla.news-article62826197"><img src="http://discontents.com.au/wp-content/uploads/2011/08/townsville-daily-bulletin-9-Dec-1939-250x322.png" alt="" title="townsville-daily-bulletin-9-Dec-1939" width="250" height="322" class="size-medium wp-image-1293" /></a>[/caption]

I'm interested in time -- in the way we imagine, manipulate, experience and describe time, particularly in the service of ideas such as 'progress'.

This was one of the themes of <a title="Atomic wonderland" href="http://discontents.com.au/shoebox/history-of-australian-science/atomic-wonderland">Atomic Wonderland</a>, but beyond constructing a few case studies it's not all that easy to study. Or at least it wasn't. Now projects such as <a href="http://victorianbooks.org/">Victorian Books</a> are showing how we can explore the changing weights of ideas across times and cultures by analysing the contents of large textual collections.

Returning visitors will be probably be aware of <a href="http://discontents.com.au/tag/trove">my own experiments</a> mining the contents of the National Library of Australia's digitised newspapers database, available through <a href="http://trove.nla.gov.au/newspaper">Trove</a>. So far I've focused on the development of generic tools and techniques, but I thought it would be interesting to apply these to my study of 'progress'. Happily the NLA agreed and have awarded me a <a href="http://www.nla.gov.au/harold-white-fellowships/2012-national-library-of-australia-fellowships-announced">Harold White Fellowship for 2012</a> to do just that. Yippee!

I'll be taking up the fellowship in February, but in preparation I've started to develop a few little sketches that prod at our fondness for periodisation. Labels such as 'the Roaring Twenties', 'the Great Depression' or even 'the First World War' are so familiar that we sometimes forget that they themselves have a history.

To begin with I decided to examine the question of when 'the Great War' became 'the First World War'. At some point we realised that the Great War was not the final act in a centuries-long drama of European jealousy and jostling, but the first in a series of global conflicts. Can newspapers tell us when?

I <a href="http://discontents.com.au/shed/experiments/mining-the-treasures-of-trove-part-2">already had a script</a> that would generate a basic time series from a Trove query string. It simply takes the query, fires off a separate search for each year and grabs the number of matching articles. If the number of matches is more than zero, it also retrieves the total number of articles for that year and calculates the proportion matching the query. The results are saved in a json file which can be easily visualised using something like <a href="http://www.highcharts.com/">HighCharts</a>. The original script needed a few tweaks to streamline the process, but I'll describe these in detail in my next post.

For this experiment I constructed two queries. The first simply searched for the phrase '<a href="http://trove.nla.gov.au/newspaper/result?q=&exactPhrase=the+great+war&l-category=Article|category%3AArticle">the great war</a>' between 1900 and 1954. The second was a bit more complicated -- it searched for <a href="http://trove.nla.gov.au/newspaper/result?l-category=Article|category%3AArticle&sortby=dateAsc&q=%22the+first+world+war%22+OR+%22world+war+one%22+OR+%22world+war+i%22+OR+%22world+war+1%22">any of the phrases</a> 'first world war', 'world war one', 'world war 1' or 'world war i' across the same period. I fed the queries to my script and after a bit of ker-chugging, whirring and clunking I ended up with a graph.

[caption id="attachment_1278" align="alignright" width="250" caption="Click to view the full interactive graph."]<a href="http://wraggelabs.com/shed/time/the_great_war-2011-08-16.html"><img src="http://discontents.com.au/wp-content/uploads/2011/08/great_war_graph-252x300.jpg" alt="" title="When did the Great War become the First World War?" width="250" height="297" class="size-medium wp-image-1278" /></a>[/caption]

The result is not really surprising. As you can see <a href="http://wraggelabs.com/shed/time/the_great_war-2011-08-16.html">on the full graph</a>, the two lines cross late in 1941. With German victories across Europe and North Africa, the opening of the Eastern Front and, finally, the Japanese attack on Pearl Harbour, 1941 seems to make sense. But it's interesting to see this reflected so clearly in such a rough and ready analysis.

What is perhaps more intriguing is the huge spike in 1939. Of course it makes sense that people would be referring back to the Great War as the prospect of a new conflict loomed, but it does make you wonder about the context of these discussions and how they might have developed as war edged closer.

Notable too are the earlier blips in the First World War count -- the first centred on 1916 and the second on 1935. The peak in 1916 is actually due to the tags and comments added by Trove users. The standard 'search everything' option in Trove includes these as well as the text of the articles themselves. By using other search options you can choose to exclude the tags that match your query, but that seems rather messy. It would be nicer if Trove gave you the option of ignoring these matches from the start.

[caption id="attachment_1286" align="alignright" width="250" caption="The West Australian, 24 May 1935"]<a href="http://nla.gov.au/nla.news-article32886350"><img src="http://discontents.com.au/wp-content/uploads/2011/08/first_world_war-300x298.jpg" alt="" title="first_world_war" width="250" height="248" class="size-medium wp-image-1286" /></a>[/caption]

The second blip is a bit more interesting. By clicking on the graph and exploring the results from Trove, you can see that it's due to the screening of a documentary film called '<a href="http://www.imdb.com/title/tt0976117/">The First World War</a>'. The film used archival footage drawn from a number of nations and was based on Laurence Stalling's book <em>The First World War: A Photographic History</em>. As one newspaper article noted: 'this picture presents war, stripped of its gaudy trappings, and fearful in its grim reality'.

By way of comparison I <a href="http://ngrams.googlelabs.com/graph?content=the+Great+War%2Cthe+First+World+War&year_start=1900&year_end=1954&corpus=0&smoothing=0">tried a similar query</a> using the Google Books Ngram viewer. The crossover point seems a little later, but of course books take longer to publish than newspapers. There is, however, no peak in 1939 for 'the Great War' -- at least not if you use the combined 'English' corpus. If you examine the British-English and American-English corpora separately it's a rather different story. Querying the British-English corpus produces <a href="http://ngrams.googlelabs.com/graph?content=the+Great+War%2Cthe+First+World+War&year_start=1900&year_end=1954&corpus=6&smoothing=0">something much closer</a> to our Trove graph, complete with a spike around 1939. Again, this is only as we'd expect given the lesser significance of the First World War in American history. 

This is, of course, only a sketch -- something to prompt new questions or suggest avenues for attack. It's made me want to find out a bit more about the nature of discussions in 1939, so I've fired up my <a href="http://wraggelabs.com/emporium/trove-tools/harvester/">Trove Newspaper Harvester</a> and downloaded the text of all 6,582 articles from 1939 that include the phrase 'the Great War'. More about that soon...