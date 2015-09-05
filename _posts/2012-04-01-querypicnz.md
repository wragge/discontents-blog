---
ID: 1621
post_title: QueryPicNZ
author: Tim Sherratt
post_date: 2012-04-01 13:17:02
post_excerpt: ""
layout: post
permalink: http://discontents.com.au/querypicnz/
published: true
tmac_last_id:
  - "640027535368060929"
  - "640027535368060929"
---
You may have noticed I have a bit on an interest in exploring ways of using digitised historical newspapers. In the last year or so I've spent a lot of time [scraping, mining, processing and visualising][1] content from the Trove collection of digitised Australian newspapers. But what about other countries? Recently I was invited to a [digital history workshop][2] organised by Sydney Shep ([@nzsydney][3]) at the Victoria University of Wellington. In between sessions I started to play with the [DigitalNZ API][4] guided by Chris McDowall ([@fogonwater][5]). In anticipation of the forthcoming Trove API I'd already done a bit of work converting [QueryPic][6] to run in the browser. It didn't take long to adapt this to work with New Zealand newspapers available through [Papers Past][7]. **So presenting for your enjoyment and education... [QueryPicNZ][8].** [caption id="attachment_1641" align="aligncenter" width="520" caption="Wind, rain and snow in QueryPicNZ"][<img class="size-large wp-image-1641" title="Screen Shot 2012-04-01 at 1.07.28 PM" src="http://discontents.com.au/wp-content/uploads/2012/04/Screen-Shot-2012-04-01-at-1.07.28-PM-520x367.png" alt="" width="520" height="367" />][9][/caption] Like [QueryPic][6], the New Zealand version graphs newspaper search results over time. But thanks to the DigitalNZ API it has a number of advantages: 
*   it runs in your browser -- no need to download or run any scripts
*   results appear almost instantly
*   easy to combine queries -- just search on a new word or phrase
*   easy to remove queries -- just use the 'Clear last' button
*   easy to share -- just copy the provided link or use the Tweet button It's limited to simple word or phrase searches at the moment, but eventually I'll add the ability to process more sophisticated queries. I also want to add a way of saving, sharing and citing graphs. For now the 'share' link simply regenerates the graph, so if the content has changed the result could well be different. The code is 

[available on GitHub][10]. Ultimately, I want to combine Trove and Papers Past so that you can query and combine content from either Australia or New Zealand... perhaps even other countries?

 [1]: http://discontents.com.au/tag/trove
 [2]: http://victoria.ac.nz/wtapress/research/digital-history-workshop-2012
 [3]: https://twitter.com/#!/nzsydney
 [4]: http://www.digitalnz.org/developers
 [5]: https://twitter.com/#!/fogonwater
 [6]: http://discontents.com.au/shed/hacks/querypic "QueryPic"
 [7]: http://paperspast.natlib.govt.nz/cgi-bin/paperspast
 [8]: http://wraggelabs.com/shed/querypicnz
 [9]: http://wraggelabs.com/shed/querypicnz/?q=wind&q=rain&q=snow
 [10]: https://github.com/wragge/QueryPicNZ