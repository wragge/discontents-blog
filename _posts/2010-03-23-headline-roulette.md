---
ID: 834
post_title: Headline roulette
author: Tim Sherratt
post_date: 2010-03-23 22:26:29
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/headline-roulette/
published: true
tmac_last_id:
  - "640027557467832321"
---
I've been doing a fair bit of coding in recent weeks and I thought I'd better write a few details down before I forget about them.

As previously noted, I've been gathering together various historical data sets for a project at the National Museum of Australia. One resource that I was keen on including was the fantastic <a href="http://newspapers.nla.gov.au/ndp/del/home">Australian Newspapers</a> project at the National Library of Australia. What I had in mind was being able to give a sense of context to any historical event by calling up the headlines for that particular time.

Unfortunately there's no API for the newspapers project (or Trove in general), though apparently it's in the works. So I had to reverse engineer the advanced search page to work out the various query options, and then build a screen scraper to harvest the results. I played around with the search options a bit to fine tune the results, finally deciding to limit them to 'news' articles with more than 1000 words. Annoyingly, only 10 results are returned at a time.

I had hoped to parse the results as xml, but a rogue &lt;br&gt; tag broke the XHTML, so I fell back on <a href="http://www.crummy.com/software/BeautifulSoup/">Beautiful Soup</a> – a Python module that makes screen scraping considerably easier by tidying up HTML structures. After than it was pretty straightforward. Soon I had <a href="http://bitbucket.org/wragge/nla-newspapers/">my own Python module</a> to query the newspapers database and process the results.

The next step was to use the module to build a simple API that would let us quickly grab a set of headlines for a particular date and place. <a href="http://www.djangoproject.com/">Django</a> and <a href="http://bitbucket.org/jespern/django-piston/wiki/Home">Piston</a> made this easy. To see headlines from Victoria on 1 January 1901, for example:

<a href="http://wraggelabs.com/api/newspapers/1901-01-01/nsw/">http://wraggelabs.com/api/newspapers/1901-01-01/nsw/</a>

That was pretty cool and it started me thinking about what else I might do with the data. At first I was planning some sort of browser, like my <a href="http://wraggelabs.com/abs/">Population Browser</a>, but that seemed a bit boring. So I decided to create a simple game that grabbed a random headline and asked you to try and guess the date. After further refinement I decided to impose a limit of 10 guesses, with 'higher' or 'lower' prompts to get you moving in the right direction. Yes, basically it was a rip-off of The Price is Right – but an interesting, ironic and historically engaged rip-off...

This required me to make a change to the API and Python module so that I could retrieve a random headline. Basically it just meant generating a query based on random values for the day, month, year and state. For the interface I once again delved into JQuery's box of tricks. With all the kerfuffle about ChatRoulette in the media, the name seemed obvious – <a href="http://wraggelabs.com/newsroulette/">Wragge's Headline Roulette</a> was born.

[caption id="attachment_839" align="aligncenter" width="300" caption="Test your historical nous with Headline Roulette!"]<a href="http://wraggelabs.com/newsroulette/"><img class="size-medium wp-image-839" title="headline-roulette" src="http://discontents.com.au/wp-content/uploads/2010/03/headline-roulette-300x151.jpg" alt="Headline roulette screen capture" width="300" height="151" /></a>[/caption]

It's a very simple little app, but a number of people have said how much fun it is. The bad news is that imminent changes to the NLA newspapers site are probably going to break it (at least in its current form). So enjoy it while you can. When the NLA makes an API available I might work on something a little more sophisticated.

Of course, the broader point is that there are a whole range of cultural materials out there waiting to be remixed and re-used in various forms. Get hacking...