---
ID: 699
post_title: Playing with pipes
author: Tim Sherratt
post_date: 2009-09-10 18:38:25
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/playing-with-pipes/
published: true
tmac_last_id:
  - "640027562840715264"
---
The ever-informative Twitter alerted me recently to the History Trust of South Australia's [object of the month][1]. It made me think that it would be nice if there was some way of bringing together all those objects, photos and documents featured by our cultural institutions. Some sort of combined RSS feed perhaps? Something like this... <script src="http://pipes.yahoo.com/js/listbadge.js">{"pipe_id":"d9507f84ba0046394fb34a99de0709bf","_btype":"list"}</script> Well, yes... I couldn't resist having a go. My tool of choice for this was [Yahoo Pipes][2] which has various modules for manipulating and creating RSS feeds. Check out [my script on the Yahoo Pipes site][3] to create a badge like this, play some more or inspect its innards. If you're feeling adventurous you can even clone the script and tinker away yourself – it's the best way to learn.<!--more--> At the moment the script aggregrates content from the Flickr photostreams of: 

*   National Archives of Australia
*   State Records NSW
*   State Library of NSW
*   State Library of Queensland
*   State Library of South Australia
*   Australian War Memorial
*   Powerhouse Museum These are mixed up with the contents of the Powerhouse's '

[Object of the week][4]' blog and the NAA's '[Find of the Month][5]'. I'm happy to add more sources – leave your suggestions below. Most of it was ridiculously easy. I just added the RSS feeds from Flickr and the Powerhouse blog, then fed them through a module to sort them into date order. 'Find of the month' was trickier because there was no existing RSS feed – time for some screen-scraping! First I scraped a list of the urls for 2009, then for each month I pulled out the title and date, as well as the first paragraph to act as a description, and the first image. Then I turned all these bits and pieces into an RSS feed and joined it up with the rest. Yahoo Pipes makes this sort of thing simple, even for non-coders. Interestingly, too, it's not just a matter of creating an RSS feed – [as you can see][3] Yahoo Pipes emits the data in a variety of formats. You can subscribe to the RSS feed, create a badge or slurp up the data in JSON to power some new application.

 [1]: http://www.history.sa.gov.au/history/object%20of%20the%20month.htm.html
 [2]: http://pipes.yahoo.com/
 [3]: http://pipes.yahoo.com/wragge/featureditems
 [4]: http://www.powerhousemuseum.com/collection/blog/
 [5]: http://naa.gov.au/whats-on/online/find-of-the-month/index.aspx