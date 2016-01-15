---
ID: 2690
post_title: DIY online exhibitions
author: Tim Sherratt
post_date: 2016-01-15 16:23:42
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/diy-online-exhibitions/
published: true
ct_tracks_video_key:
  - ""
ct_tracks_video_display_key:
  - post
ct_tracks_video_youtube_title:
  - "0"
ct_tracks_video_youtube_related:
  - "0"
ct_tracks_video_youtube_logo:
  - "0"
ct_tracks_video_youtube_captions:
  - "0"
citation:
  - ""
internet_archive:
  - ""
doi:
  - ""
github:
  - ""
---
I'm no longer part of the mighty <a href="http://trove.nla.gov.au/">Trove</a> team at the National Library of Australia. But hacking Trove was a passion long before I took on the manager's role and that, of course, will continue.

I'm particularly interested in what happens when we aggregate cultural collections and make the results available in a machine-readable form, such as through an <a href="http://help.nla.gov.au/trove/building-with-trove">API</a>. This is what Trove, <a href="http://www.digitalnz.org/">DigitalNZ</a>, the <a href="http://dp.la/">Digital Public Library of America</a>, and <a href="http://www.europeana.eu/portal/">Europeana</a> all do -- dispersed and disparate collections go in one end, reusable metadata comes out the other. The APIs of these services provide single, standard entry points to a diverse collection of collections. Using them you can build applications that enable us to connect and compare, rather than just find.

But to use an API you generally need to know how to code, and that's a problem for many. How can you make use of these aggregated riches without becoming lost forever amidst the arcane byways of code?  I think those of us who build with code can do more to cultivate the middle ground between API and apps -- to create frameworks, skeletons, examples and demos that can be shared and customised by non or novice coders. Reusable apps built on reusable data.

Late last year I created an app that pulls together the contents of selected Trove lists and displays them in an attractive way. <a href="http://help.nla.gov.au/trove/using-trove/creating-contributing/lists">Trove lists</a> are user-created collections of items available through Trove, and their contents are accessible through the API. So just plug in some lists and my app creates an instant exhibition.

&nbsp;

[caption id="attachment_2693" align="aligncenter" width="711"]<a href="http://wragge.github.io/celestial-empire/#/"><img class="size-large wp-image-2693" src="http://discontents.com.au/wp-content/uploads/2016/01/Screen-Shot-2016-01-15-at-3.49.34-PM-1024x876.png" alt="The app in action for the Celestial Empire exhibition" width="711" height="608" /></a> The app in action for the Celestial Empire exhibition[/caption]

The app is currently being used to <a href="http://wragge.github.io/celestial-empire/#/">feature Trove content</a> related to the National Library's <a href="https://www.nla.gov.au/exhibitions/celestial-empire">Celestial Empire</a> exhibition, but I developed it to support easy reuse and customisation. It's built with <a href="https://angularjs.org/">AngularJS</a>, so the result is just a single HTML page with some Javascript and CSS attached -- no database or CMS required, just a little space on a webserver.

There are two versions of the code available: the <a href="https://github.com/wragge/trove-lists-exhibition">complete development environment</a>, and a <a href="https://github.com/wragge/diy-trove-exhibition">pre-compiled version</a> for quick customisation. If you're a coder you can obviously grab the <a href="https://github.com/wragge/trove-lists-exhibition">original repository</a> and set up everything using Grunt and Bower. You're then free to tinker with the navigation or the functionality as you so wish.

But I thought most people would just want to plug in their own lists and maybe tweak the styles a bit. That's where the <a href="https://github.com/wragge/diy-trove-exhibition">pre-compiled version</a> is useful. All the AngularJS stuff has been neatly packed away into a couple of script files, exposing just the bits that people are most likely to change. Even better, I've taken advantage of GitHub's own <a href="https://pages.github.com/">Pages</a> service to set out a simple series of steps that guide you through from customisation to publication. The only coding required is some simple edits to a single HTML file. Create your own online exhibition in minutes, using nothing but a GitHub account! Magic!

[caption id="attachment_2692" align="aligncenter" width="711"]<a href="https://github.com/wragge/diy-trove-exhibition/blob/gh-pages/index.html"><img class="size-large wp-image-2692" src="http://discontents.com.au/wp-content/uploads/2016/01/Screen-Shot-2016-01-15-at-3.55.02-PM-1024x426.png" alt="Just edit a few lines of HTML and you're done!" width="711" height="296" /></a> Just edit a few lines of HTML and you're done![/caption]

The <a href="https://github.com/wragge/diy-trove-exhibition/blob/gh-pages/readme.md">steps are all described</a> in the GitHub repository, as are more advanced opportunities for customisation. A non-coder can easily set up an exhibition, but with just a little more confidence you can start tweaking the CSS to build your own custom style.

The app pulls data from the Trove API each time it loads, so any changes you make to the lists themselves will be immediately reflected in the exhibition. You can also include extra contextual information by adding descriptions to your lists and notes to list items in Trove -- this will be automatically displayed in the exhibition.

Kate Bagnall recently used this framework to create her own exhibition, <a href="http://baibi.github.io/chinese-in-nsw-in-pictures/#/">The Chinese in New South Wales -- A history in pictures to 1940</a>. She's also written a <a href="http://chineseaustralia.org/building-a-diy-trove-list-exhibition">useful blog post</a> describing the process of putting it together. Catriona Bryce has created exhibitions on <a href="http://treen42.github.io/Explore-Canberra-in-Trove/#/">Canberra</a> and the <a href="http://catrionaexhibition.github.io/A-tour-of-the-Southern-Highlands/#/">Southern Highlands</a>.

Feel free to play around and see what you can create!