---
ID: 1515
post_title: 'Extracting editorials #2'
author: Tim Sherratt
post_date: 2011-12-19 23:18:49
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/extracting-editorials-2/
published: true
tmac_last_id:
  - "640027538706710528"
---
As I explained in <a title="Extracting editorials #1" href="http://discontents.com.au/shoebox/digital-humanities/extracting-editorials-1">the first of this series</a>, I'm documenting my efforts to extract every editorial published in the <em>Sydney Morning Herald</em> in 1913 from the Trove newspaper database. It's an experiment both in text mining and historical writing -- an attempt to put the method up front.

While I didn't think there was anything very thrilling in the first instalment, recording my thoughts and assumptions in this way has already proved useful. In a comment, <a href="http://discontents.com.au/shoebox/digital-humanities/extracting-editorials-1#comment-2371">Owen Stephens noted</a> that his attempt to reproduce my search query produced fewer results. After a little bit of poking around I realised that the fulltext modifier, which I often use to switch off fuzzy matching, counteracts the 'search headings only' flag. So my query was returning results that had the string 'The Sydney Morning Herald' anywhere in the article.

Try it for yourself.

<a href="http://trove.nla.gov.au/newspaper/result?l-textSearchScope=headings+only%7Cscope%3Aheadings&amp;l-title=The+Sydney+Morning+Herald...%7Ctitleid%3A35&amp;l-word=*ignore*%7C*ignore*&amp;fromyyyy=1913&amp;toyyyy=1913&amp;sortby=dateAsc&amp;q=fulltext%3A%22The+Sydney+Morning+Herald%22&amp;l-category=Article%7Ccategory%3AArticle&amp;s=0">Here's my original query</a> -- searching for fulltext:"The Sydney Morning Herald" in headings only (supposedly). You'll notice that it returns 335 results and it's clear from a quick scan that a number are false positives (they don't follow the pattern for editorials).

<a href="http://trove.nla.gov.au/newspaper/result?l-textSearchScope=headings+only%7Cscope%3Aheadings&amp;l-title=The+Sydney+Morning+Herald...%7Ctitleid%3A35&amp;l-word=*ignore*%7C*ignore*&amp;fromyyyy=1913&amp;toyyyy=1913&amp;sortby=dateAsc&amp;l-category=Article%7Ccategory%3AArticle&amp;q=%22The+Sydney+Morning+Herald%22">Here's Owen's query</a> -- searching for "The Sydney Morning Herald" in headings only. It returns 294 results, without any obvious false positives.

So my attempt to disable fuzzy matching actually produced a less accurate result! Weird.

Actually, I think one important benefit of this sort of text mining is that it helps you understand how the search engines you're using actually work. Once you start poking and prodding, the idiosyncrasies start to emerge.

Anyway, I harvested Owen's cleaner result set and opened up the resulting csv file. As it seemed in Trove, there we're very few false positives. Indeed there were only two articles that didn't seem to follow the standard editorial format, and these were notes added to the editorial page. On the other hand, there were obviously about 20 editorials missing. I could have manually worked through the csv file to identify the missing dates, but I thought I'd try to create some tools that would do the work for me.

What I wanted was the details of the first editorial in every edition of the newspaper in 1913 -- so there should be one, and only one, article for each day on which the newspaper was published. I needed a tool that would analyse the csv file and do two things:
<ul>
	<li>identify dates that occur multiple times (false positive alert!)</li>
	<li>identify dates that are absent from the result set (missing in action!)</li>
</ul>
The resulting code is <a href="https://github.com/wragge/Trove-newspapers">all on GitHub</a> if you want follow along. I wrote a Python script that opens up the csv file, extracts all the date strings, converts them to datetime objects and then saves them to a list. Once that's done it's pretty easy to loop through and find duplicates:

<pre class="brush: python">
def find_duplicates(list):
    &#039;&#039;&#039;
    Check a list for suplicate values.
    Returns a list of the duplicates.
    &#039;&#039;&#039;
    seen = set()
    duplicates = []
    for item in list:
        if item in seen:
            duplicates.append(item)
        seen.add(item)
    return duplicates
</pre>

Finding missing dates was a little more complicated, but Google came to the rescue with some handy code samples. All I had to do was set a start and end date (in this case 1 January 1913 and 31 December 1913) and create a timedelta object equal to a day. Then it's just a matter of adding the timedelta to the start date, comparing the new date to the dates extracted from the csv file, and continuing on until you hit the end. If the new date isn't in the csv file, then it gets added to the missing list.

<pre class="brush: python">
if year:
        start_date = datetime.date(year, 1, 1)
        end_date = datetime.date(year, 12, 31)
    else:
        start_date = article_dates[0]
        end_date = article_dates[-1]
    one_day = datetime.timedelta(days=1)
    this_day = start_date
    # Loop through each day in specified period to see if there&#039;s an article
    # If not, add to the missing_dates list.
    while this_day &lt;= end_date:
        if this_day.weekday() not in exclude: #exclude Sunday
            if this_day not in article_dates:
                missing_dates.append(this_day)
        this_day += one_day
</pre>

I've tried to make the code as reusable as possible, so you can either supply a year, or the script will read start and end dates from the csv file itself.

All that left me with two more lists of dates: 'duplicates' and 'missing'. At first I just wrote these out to a text file, but then I decided it would be useful to write the results to an html page. That way I could add links that would take me to the actual issue within Trove, helping me to quickly find the missing editorial.

Unfortunately there's no direct way to go from a date to an issue -- you first need to find the issue identifier. How do you do this? If you dig around in the code beneath <a href="http://trove.nla.gov.au/ndp/del/title/35">the page for each newspaper title</a>, you'll find that the ajax interface pulls in a json file with issue information. You can access this through a url like: http://trove.nla.gov.au/ndp/del/titlesOverDates/[year]/[month]. Here's an example for <a href="http://trove.nla.gov.au/ndp/del/titlesOverDates/1913/01">January 1913</a>.

The json includes all issues for all titles in the specified month. So you then have to loop through to find a specific title and day. Once you have the issue identifier you can just attach it to a url:

<pre class="brush: python">
def get_issue_url(date, title_id):
    &#039;&#039;&#039;
    Gets the issue url given a title and date.
    &#039;&#039;&#039;
    year, month, day = date.timetuple()[:3]
    url = &#039;http://trove.nla.gov.au/ndp/del/titlesOverDates/%s/%02d&#039; % (year, month)
    issues = json.load(urllib2.urlopen(url))
    for issue in issues:
        if issue[&#039;t&#039;] == title_id and int(issue[&#039;p&#039;]) == day:
            issue_id = issue[&#039;iss&#039;]
    return &#039;http://trove.nla.gov.au/ndp/del/issue/%s&#039; % issue_id
</pre>

[caption id="attachment_1533" align="alignright" width="250" caption="My results file with links to Trove"]<a href="http://discontents.com.au/wp-content/uploads/2011/12/Screen-Shot-2011-12-19-at-4.43.15-PM1.png"><img src="http://discontents.com.au/wp-content/uploads/2011/12/Screen-Shot-2011-12-19-at-4.43.15-PM1-250x469.png" alt="" title="Screen Shot 2011-12-19 at 4.43.15 PM" width="250" height="469" class="size-medium wp-image-1533" /></a>[/caption]

Finally, to save myself having to cut and paste the missing dates back into the csv file, I added a few lines to write them in automatically.

So now I have a handy little html page, complete with dates and links, that I'm working through to find all the missing editorials. All I need for the next stage are the urls for the editorial and the page on which it's published. I'm just cutting and pasting these from the citation box in Trove into the csv file. Once this is done I can start trying to find <strong>all</strong> the editorials.

PS: I noted in my first post that one benefit in finding the editorials was that the main news articles usually appeared on the page after the editorials. I've been thinking some more about ways to identify 'major' news stories. Word length perhaps? But not always. Hmmm, but major stories do seem to be published at the top of the page. After a bit more poking around in the code I found that there's a 'y value' assigned to each article that indicates its position on the page. So if I harvest all the articles on the page after the editorials and then rank them by their y values? Interesting...