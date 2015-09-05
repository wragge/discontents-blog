---
ID: 2232
post_title: An addition to the family
author: Tim Sherratt
post_date: 2014-01-27 19:19:46
post_excerpt: ""
layout:
  - default
permalink: >
  http://discontents.com.au/an-addition-to-the-family/
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
  - "640027512207110145"
---
What's the collective noun for a group of Twitter bots? Inspiration is failing me at the moment, so let's just say that the Trove bot family recently welcomed a new member -- [@TroveBot][1]. [caption id="attachment_2240" align="aligncenter" width="447"][<img class="size-full wp-image-2240" alt="Proof cover for Rogue Robot, Thrills Incorporated pulp series, 1951. By Belli Luigi." src="http://discontents.com.au/wp-content/uploads/2014/01/nla.pic-vn6097959-v.jpg" width="447" height="600" />][2] Proof cover for Rogue Robot, Thrills Incorporated pulp series, 1951. By Belli Luigi.[/caption] @TroveBot is a sibling of [@TroveNewsBot][3], who's been tweeting away since [June last year][4]. But while @TroveNewsBot draws his inspiration from 120+ million historical newspaper articles, @TroveBot digs away in the millions of books, theses, pictures, articles, maps and archives that make up the rest of [Trove][5]. Trove, as we always like to remind people, is not just newspapers. Like @TroveNewsBot, the newcomer tweets random finds at regular intervals during the day. But both bots also respond to queries. Just tweet a few keywords at them and they'll have a poke around Trove and reply with something that seems relevant. There's various ways of modifying this basic search, as explained on the GitHub pages of [TroveNewsBot][6] and [TroveBot][7]. @TroveBot's behaviour is a little more complex because of Trove's zone structure. The zones bring together resources with a similar format. If you want to get a more detailed idea of what's in them, you can play around with my [Zone Explorer ][8](an experiment for every occasion!). If you just tweet some keywords at @TroveBot he'll search for them across all the zones, then choose one of the matching zones at random. If you want to limit your search to a particular zone or format, just add one of the format tags listed on the [GitHub site][7]. Let's say you want a book about robots, just tweet: 'robots #book'. Or a photos of pelicans, try 'pelican #photo'.  It's really that easy. https://twitter.com/TroveBot/status/424779517660393472 But you don't just have to use keywords, you can also feed @TroveBot a url. Perhaps you want to find a thesis in Trove that is related to a Wikipedia page -- just tweet the url together with the tag '#thesis'. Yes, really. https://twitter.com/TroveBot/status/424787074152005633 Behind the scenes @TroveBot makes use of [AlchemyAPI][9] to extract keywords from the url you supply. These keywords are then bundled up and shipped off to Trove for a response. You probably know that @TroveNewsBot is similarly url-enabled. This allows him to do things like [respond to the tweets][10] of his friends [@DigitalNZBot][11] and [@DPLABot][12], and offer regular commentary on the ABC News headlines. https://twitter.com/TroveNewsBot/status/426112094790893568 So what would happen if @TroveBot and @TroveNewsBot started exchanging links? Would they ever stop? Would they break the internet? With the Australian Tennis Open coming to a climax over the last few days I thought it was a suitable time to set up a game of bot tennis. To avoid the possibility of internet implosion, I decided to act as intermediary, forwarding the urls from one to the other. The rules were simple -- the point was lost if a bot failed to respond or repeated a link from earlier in the match. https://twitter.com/wragge/status/427417681071849472 As a sporting spectacle the inaugural game wasn't exactly scintillating. In fact, the first game is still locked at 40-40. But it's been interesting to see the connections that were made. It's also been a useful opportunity for me to find bugs and tweak their behaviours. You can catch up with the [full, gripping coverage][13] via Storify. After a few more experiments I'm thinking I might try and set up a permanent, endless conversation between them. It would be fascinating to see where they'd end up over time -- the links they'd find, the leaps they'd make. Hmm, collective nouns... What about a *serendipity* of bots?

 [1]: https://twitter.com/TroveBot
 [2]: http://trove.nla.gov.au/version/186071643
 [3]: https://twitter.com/TroveNewsBot
 [4]: http://discontents.com.au/conversations-with-collections/ "Conversations with collections"
 [5]: http://trove.nla.gov.au
 [6]: https://github.com/wragge/trovenewsbot
 [7]: https://github.com/wragge/trovebot
 [8]: http://dhistory.org/trove/zone-explorer/
 [9]: http://www.alchemyapi.com/
 [10]: http://storify.com/wragge/conversations-between-bots
 [11]: https://twitter.com/digitalNZbot
 [12]: https://twitter.com/DPLAbot
 [13]: http://storify.com/wragge/inaugural-trove-bots-tennis-open