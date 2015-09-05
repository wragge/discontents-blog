---
ID: 2249
post_title: Enriching WWI data with the Trove API
author: Tim Sherratt
post_date: 2014-03-09 22:38:31
post_excerpt: ""
layout:
  - default
permalink: >
  http://discontents.com.au/enriching-wwi-data-with-the-trove-api/
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
  - default
unlink_post_image:
  - default
builder_switch_frontend:
  - "0"
tmac_last_id:
  - "640027511972204544"
---
I can't resist a challenge, particularly when it involves lots of new historical data and an excuse to muck around with the <a href="http://trove.nla.gov.au/general/api">Trove API</a>. So when Katie Hannan from the State Library of South Australia asked me about putting the API to work to enrich one of their World War I datasets, I had to dive in and have a play.

The dataset consists of references to South Australian WWI service personnel published in the Adelaide <em>Chronicle</em> between 1914 and 1919. In a massive effort starting back in 2000, SLSA staff manually extracted more than 13,000 references and grouped them under 9709 headings, mostly names. You can explore the data in the SLSA catalogue as part of the <a href="http://www.catalog.slsa.sa.gov.au/search~S1?/gHeroes+of+the+Great+War/gheroes+of+the+great+war/-3%2C-1%2C0%2CB/exact&amp;FF=gheroes+of+the+great+war&amp;1%2C9706%2C">Heroes of the Great War</a> collection.

It's great data, but it would be even better if there was a direct link to each article in Trove -- hence Katie's interest in the possibilities of the API!

[caption id="attachment_2258" align="aligncenter" width="988"]<a href="http://nla.gov.au/nla.news-page8611372"><img class="size-full wp-image-2258" alt="Chronicle (Adelaide, SA : 1895 - 1954) 14 Sep 1918, p. 24, http://nla.gov.au/nla.news-page8611372" src="http://discontents.com.au/wp-content/uploads/2014/03/Screen-Shot-2014-03-09-at-9.11.39-pm.png" width="988" height="646" /></a> Chronicle (Adelaide, SA : 1895 - 1954) 14 Sep 1918, p. 24,<br />http://nla.gov.au/nla.news-page8611372[/caption]

Katie sent me a <a href="https://github.com/wragge/trove-wwi-names/blob/master/data/slsa_great_war.csv">spreadsheet</a> containing the data. Each row corresponds to an individual entry and includes an identifier, a name, a year, and a list of references separated by semicolons. My plan was simple, for each row I'd construct a search based on the name, then loop through the search results to try find an article that matched the date and page number of each reference. This might seem a bit cumbersome, but currently there's no way of searching Trove for newspaper articles published on a particular day.

You'll find <a href="https://github.com/wragge/trove-wwi-names">all of the code on GitHub</a>. I've tried to include plenty of comments to make it easy to follow along.

Let's look at the entry for <strong>Lieutenant Frank Rosevear</strong>. It includes the following references: <strong>'Chronicle, 7 September 1918, p. 27, col. c;Chronicle, 14 September 1918, p. 24, col. a p.38, col. d'</strong>. If you look closely, you'll see that there's two page numbers for 14 September 1918, so there's actually three references included in this string. The first thing I had to do was to pull out all the references and format them in a standard way.

Assuming that the last name was the surname, I then constructed a query that searched for an exact match of the surname together with at least one of the other names. In Lieutenant Rosevear's case the query would've been 'fulltext:"Rosevear" AND ("Lieutenant" OR "Frank")'. Note the use of the 'fulltext' modifier to indicate an <em>exact</em> match. To this query I added a date filter to limit the search to the specified year and an 'l-title' value to search only the Adelaide <em>Chronicle</em>.

You can see the <a href="http://desolate-bastion-1864.herokuapp.com/?url=http%3A%2F%2Fapi.trove.nla.gov.au%2Fresult%3Fq%3Dfulltext%3A%22Rosevear%22+AND+%28%22Lieutenant%22+OR+%22Frank%22%29+date%3A%5B1918+TO+1918%5D%26l-title%3D291%26zone%3Dnewspaper%26encoding%3Djson">results for this query</a> in my Trove API console. Try modifying the query string to see what difference it makes.

Once the results came back from the API I compared them to the references, looking for matches on both the date and page number. You might notice that the second result from the API query, dated 7 September 1918, is a match for one of our references. Yay! This gets saved to a list of strong matches. But what about the other references?

Just in case there's been a transcription error, or the page numbering differed across editions,  I relax the rules a bit in a second pass and accept matches on the date, but <em>not</em> the page. These are saved to a list of close matches.

This second pass doesn't help much with  Lieutenant Rosevear's missing references, so we have to broaden our search query a bit. This time we <a href="http://desolate-bastion-1864.herokuapp.com/?url=http%3A%2F%2Fapi.trove.nla.gov.au%2Fresult%3Fq%3Dfulltext%3A%22Rosevear%22+date%3A%5B1918+TO+1918%5D%26l-title%3D291%26zone%3Dnewspaper%26encoding%3Djson">search on the surname only</a>. Bingo! The first result is a match and points us to one of the 'Heroes of the Great War' series.

[caption id="attachment_2256" align="aligncenter" width="296"]<a href="http://nla.gov.au/nla.news-article87553854"><img class="size-full wp-image-2256" alt="'HEROES OF THE GREAT WAR: THEY GAVE THEIR LIVES FOR KING AND COUNTRY.', Chronicle (Adelaide, SA : 1895 - 1954) 14 Sep 1918, p. 24, http://nla.gov.au/nla.news-article87553854" src="http://discontents.com.au/wp-content/uploads/2014/03/Screen-Shot-2014-03-09-at-9.05.47-pm.png" width="296" height="429" /></a> 'HEROES OF THE GREAT WAR: THEY GAVE THEIR LIVES FOR KING AND COUNTRY.', Chronicle (Adelaide, SA : 1895 - 1954) 14 Sep 1918, p. 24,<br />http://nla.gov.au/nla.news-article87553854[/caption]

It took a while, but my script eventually worked it's way through all 9709 entries like this, writing the results out to csv files containing the <a href="https://github.com/wragge/trove-wwi-names/blob/master/data/slsa_strong.csv">strong</a> and <a href="https://github.com/wragge/trove-wwi-names/blob/master/data/slsa_close.csv">close</a> matches. It also created <a href="https://github.com/wragge/trove-wwi-names/blob/master/data/slsa_results.csv">a summary</a> for each entry, listing the original number of references alongside the number of strong and close matches.

Ever since I read Trevor Munoz's post on <a href="http://trevormunoz.com/notebook/2014/01/10/borrowing-data-science-tools-more-work-with-nypl-open-data-part-three.html">using Pandas</a> with data from the NYPL's <em>What’s on the Menu?</em> project, I've wanted to have a play with it. So I decided to use Pandas to produce some quick stats from my <a href="https://github.com/wragge/trove-wwi-names/blob/master/data/slsa_results.csv">results file</a>.
<pre class="brush: python;">&gt;&gt;&gt; import pandas as pd
&gt;&gt;&gt; df = pd.read_csv('data/slsa_results.csv')
# How many entries?
&gt;&gt;&gt; len(df)
9709
# How many references?
&gt;&gt;&gt; df['references'].sum()
13504
# How many entries had strong matches?
&gt;&gt;&gt;len(df[df.strong &gt; 0])
6440
# As a percentage thank you...
&gt;&gt;&gt; 100 * len(df[df.strong &gt; 0]) / len(df)
66
# In how many entries did the number of refs = the number of strong matches
&gt;&gt;&gt; len(df[df.references == df.strong])
4399
# As a percentage thank you...
&gt;&gt;&gt; 100 * len(df[df.references == df.strong]) / len(df)
45
# How many entries had at least one strong or close match?
&gt;&gt;&gt; len(df[df.total &gt; 0])
8989
# As a percentage thank you...
&gt;&gt;&gt; 100 * len(df[df.strong &gt; 0]) / len(df)
92</pre>
Not bad. The number of strong matches equalled the number of references in 45% of cases, and overall 66% of entries had a least one strong match. I might be able to get those numbers up by tweaking the search query a bit, but of course the main limiting factor is the quality of the OCR. If the article text isn't good enough we're never going to find the names we're after.

Katie tells me that the State Library intends to point volunteer text correctors towards identified articles. As the correctors start to clean things up, we should be able to find more matches simply by re-running this script at regular intervals.

But what articles should they point the volunteers to? Many of them included the title 'Heroes of the Great War', so they're easy to find, but there were others as well. By analysing the matches we've <em>already</em> found we can pull out the most frequent titles and build a list of likely candidates. Something like this:
<pre class="brush: python">title_phrases = [
'heroes of the great war they gave their lives for king and country',
'australian soldiers died for their country',
'casualty list south australia killed in action',
'on active service',
'honoring soldiers',
'military honors australians honored',
'casualty lists south australian losses list killed in action',
'australian soldiers died for his country',
'died for their country',
'australian soldiers died for the country',
'australian soldiers died for their country photographs of soldiers',
'quality lists south australian losses list killed in action',
'list killed in action',
'answered the call enlistments',
'gallant south australians how they won their honors',
'casualty list south australia died of wounds',
]</pre>
Now we can feed these phrases into a series of API queries and automatically generate <a href="https://github.com/wragge/trove-wwi-names/blob/master/data/articles.csv">a list of articles</a> that are likely to contain details of WWI service people. This list should provide a useful starting point for keen text correctors.

I might not have completely solved Katie's problem, but I think I've shown that the Trove API can be usefully called into action for these sorts of projects. Taking this approach should certainly save a lot of manual searching, clicking, cutting and pasting. And while I've focused on the South Australian data, there's no reason why similar approaches couldn't be applied to other WWI projects.