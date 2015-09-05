---
ID: 823
post_title: Out of the cube
author: Tim Sherratt
post_date: 2010-02-26 15:57:44
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/out-of-the-cube/
published: true
tmac_last_id:
  - "640027559275552768"
---
For a project that I'm working on at the National Museum of Australia, I've started collecting various sources of date-identified data. Most recently I had a go at extracting [historical population data][1] from the Australian Bureau of Statistics. The data can all be downloaded as .xls files, but they're not simple, flat spreadsheets – they're data cubes. As the name suggests, data cubes are organised along a number of dimensions. In the case of the population data it's year, state and gender. This means that you can't just export the data to CSV and suck it into your database – first you've got to flatten the cube. No doubt there are other ways to do this, but I just wrote a simple python script. It uses [xlrd][2] to read from the spreadsheet, does a bit or reorganisation, then writes the output to a CSV file. The code, for what it's worth, is [available at Bitbucket][3]. Once I had the CSV file I just imported it into MySQL and used Django and [Piston][4] to build a basic API. So if you want to know the population of NSW in 1856, you just go to: <http://wraggelabs.com/api/json/population/nsw/1856/> The number of infant deaths in Tasmania in 1932: <http://wraggelabs.com/api/json/infantdeaths/tas/1932/> The number of female births in Australia in 1959: <http://wraggelabs.com/api/json/births/australia/females/1959/> I'm sure you get the picture. You can change the 'json' to 'xml' if you'd like another flavour of data. [caption id="attachment_830" align="aligncenter" width="300" caption="The API in action - a simple population browser"][<img class="size-medium wp-image-830" title="pop_browser" src="http://discontents.com.au/wp-content/uploads/2010/02/pop_browser-300x140.png" alt="Screenshot of population browser" width="300" height="140" />][5][/caption] With an API delivering JSON you can start playing around with all sorts of fun AJAX-y stuff. To demonstrate I built a [simple population browser][5] using JQuery. Just drag the slider!

 [1]: http://www.abs.gov.au/AUSSTATS/abs@.nsf/mf/3105.0.65.001
 [2]: http://pypi.python.org/pypi/xlrd
 [3]: http://bitbucket.org/wragge/abs-data-cube-processor/
 [4]: http://bitbucket.org/jespern/django-piston/wiki/Home
 [5]: http://wraggelabs.com/abs/