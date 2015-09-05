---
ID: 2396
post_title: Sketching with Python and Plotly
author: Tim Sherratt
post_date: 2014-11-30 13:22:12
post_excerpt: ""
layout:
  - default
permalink: >
  http://discontents.com.au/sketching-with-python-and-plotly/
published: true
content_width:
  - default_width
feature_size:
  - blank
hide_post_title:
  - default
unlink_post_title:
  - default
hide_post_meta:
  - default
hide_post_date:
  - default
hide_post_image:
  - 'yes'
unlink_post_image:
  - 'no'
builder_switch_frontend:
  - "0"
post_image:
  - >
    http://discontents.com.au/wp-content/uploads/2014/11/click_to_enter_plot_title.png
tmac_last_id:
  - "640027505869635584"
---
I'm currently trying to make some progress with my ['seams and edges' paper][1] for ALIAOnline 2015 and naturally ended up writing some code (what me procrastinate?). I was wondering about ways of exploring the 'representativeness' of an aggregation like Trove -- what's there and what's not -- so started noodling around with the [Trove API][2]. The first result was a graph representing the numbers of Trove contributors and resources by state, compared to the population of that state. All values are displayed as percentages of the total. <iframe src="https://plot.ly/~wragge/19.embed?width=460&height=345" width="460" height="345" frameborder="0" scrolling="no" seamless="seamless"></iframe> The ACT is over-represented, of course, because of the holdings of the National Library itself. The under-representation of Queensland looks interesting -- something to explore in the future. My next graph used data on languages spoken at home in Australia from the 2011 census. It compared the population speaking those languages with the number of books in that language included in Trove, again as percentages of the total. It doesn't embed very well, so view the [full-size version][3] on Plotly. As I was playing around I noticed a tweet from Bridget Griffen-Foley: https://twitter.com/BGriffenFoley/status/537129804063981568 Being in a quick-coding sort of mood I had to see how long it would take me to create a graph showing the numbers of daily newspapers in Trove (where daily is defined as more than 300 issues in a year). The answer was about fifteen minutes. <iframe src="https://plot.ly/~wragge/20.embed?width=460&height=345" width="460" height="345" frameborder="0" scrolling="no" seamless="seamless"></iframe> All of the graphs are created using the web service [Plotly][4]. Plotly has an easy-to-use [Python API][5] which means all you need to do to create a graph is to add a few lines of code. There are other Python visualisation libraries, but I like Plotly because it creates something instantly shareable -- perfectly suited to this sort of quick and dirty experimentation. I don't think any of these graphs are particularly revealing, and I've made some assumptions about the data that probably wouldn't hold up under scrutiny. But what this fiddling around emphasised was how an API and some simple tools make it possible to ask quick questions of the data. All the code is in my [Trove-Sketches][6] repository on GitHub.

 [1]: http://discontents.com.au/on-seams-and-edges/ "On seams and edges"
 [2]: http://help.nla.gov.au/trove/building-with-trove
 [3]: https://plot.ly/~wragge/21/languages-of-trove-books-compared-to-australian-population/
 [4]: https://plot.ly/
 [5]: https://plot.ly/python/
 [6]: https://github.com/wragge/trove-sketches