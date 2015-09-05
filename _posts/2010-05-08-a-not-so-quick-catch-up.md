---
ID: 843
post_title: (a not so) Quick catch up
author: Tim Sherratt
post_date: 2010-05-08 01:37:13
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/a-not-so-quick-catch-up/
published: true
tmac_last_id:
  - "640027556272570368"
---
The trained guinea pigs in the Wragge Labs bunker have been churning out all sorts of stuff in the last few months, and I'm way behind in my attempts to document their activities. So this is a bit of a catch-up post to try and commit a few pertinent details to the collective memory bank before they are lost forever in the sleep-deprived fog of day-to-day existence.
<h3>Identity upgrades</h3>
There have been a number of major improvements to <a href="http://wraggelabs.com/identities/">Wragge's Identity Browser</a>. Regular viewers will recall that the Identity Browser is built on top of the <a href="http://www.nla.gov.au/apps/srw/search/peopleaustralia">People Australia SRU interface</a>. You might not realise, however, that People Australia contains details of many organisations as well as people. We can only be thankful that it wasn't called Entity Australia.

The first version of my Identity Browser only searched for people, but now all your corporate-entity-identification needs are also met, with only a few minor changes to the interface so-beloved by numerous generations of identity seekers. To be specific, through the wonders of drop-down technology you can choose whether you want to search for a person or an organisation. Or not. You can also just ignore that and search for everything and get back sensible results anyway. It's your choice. Or not.

[caption id="attachment_864" align="aligncenter" width="300" caption="Gaze in awe at the power of my dropdown"]<a href="http://wraggelabs.com/identities/"><img class="size-medium wp-image-864" title="identities" src="http://discontents.com.au/wp-content/uploads/2010/05/identities-300x77.jpg" alt="" width="300" height="77" /></a>[/caption]

Ah pattern matching... there are few phrases so redolent of warm summer days, hidden pleasures, and the subtle delights of wildcard characters. The People Australia SRU interface was sadly lacking in the pattern matching department, but this has now been rectified. So now you mix your stems and asterixes with wild abandon. Searching for 'Curtin, J*' will now retrieve all those Curtins whose names begin with 'J'. Amazing isn't it?

Astonishing too is the fact that the accompanying 'Identify me!' bookmarklet continues to function with nary a murmur of protest. There is, however, a little bit of cleverness built-in to enhance your bookmarklet experience. If the text that you highlight has a comma in it, the Identity Browser will conclude that you're feeding it the name of a person – ie Surname, Firstname – and will treat the Firstname as a stem. So if you highlight 'Whitlam, G' and click on the bookmarklet, the Identity Browser will be kick-started into life, searching for everything that matches surname equals 'Whitlam' and firstname is like 'G*'. If there's no comma – ie firstname secondname – then it heads off to look for either a person whose surname equals 'secondname' and whose firstname is like 'firstname*', or an organisation whose name includes both 'firstname' and 'secondname'. Got all that?

Basically the idea was to try and provide some sensible defaults so you really don't have to think about it too much.

I have it in my head to prepare a long and rapturous homage to the wonders of machine tags. With their sly semantic ways and easy-going nature, they offer some exciting possibilities not just for user-generated content, but user-generated meanings and user-generated relationships. But for the full, ripe pleasure of that post you will have to wait another day, for now I shall simply say that as well as RDFa, the Identity Browser provides automagically-generated machine tags.

Where might you use them? Flickr's a good place to start. Try identifying the subjects and creators of Flickr photos. At the NSW Reference and Information Services Group Seminar the other day I challenged those in attendance to go forth and machine tag. Already more than 100 machine tags have been added to Flickr using my Identity Browser. Expect to hear more about the Great Flickr Machine Tag Challenge soon...

One more thing... try adding '.rdf' on to the end of an identity record – eg <a href="http://wraggelabs.com/identities/person/612109.rdf">http://wraggelabs.com/identities/person/612109.rdf</a>. Just an experiment at the moment...
<h3>More machine tag love</h3>
One night on Twitter, <a href="http://twitter.com/lifeasdaddy">@lifeasdaddy</a> pointed out that someone had started using fragments of urls from the <a href="http://trove.nla.gov.au/newspaper">NLA newspapers site</a> as tags in the <a href="http://www.powerhousemuseum.com/collection/database/?irn=244414">Powerhouse Museum's collection database</a>. In the conversation that ensued with <a href="http://twitter.com/sebchan">@sebchan</a> and others, I suggested that the PHM could encourage this sort of rich tagging by supporting machine tags, with all their wonderful juicy semantic goodness The guinea pigs got excited as well, and before I knew it, they'd constructed a little <a href="http://semweb-helper.appspot.com/">Semweb Helper app</a>.

The Semweb Helper comes with its very own custom-tailored bookmarklet. If you find an article on the NLA newspapers site that you'd like to point to, just click on the bookmarklet and marvel as a range of useful machine tags are automagically generated. Then you just pick the appropriate tag, copy and paste et voila – instant semantic gratification.

[caption id="attachment_861" align="aligncenter" width="300" caption="Try out the Semweb Helper"]<a href="http://semweb-helper.appspot.com/"><img class="size-medium wp-image-861" title="semweb-helper" src="http://discontents.com.au/wp-content/uploads/2010/05/semweb-helper-300x147.jpg" alt="Screenshot" width="300" height="147" /></a>[/caption]

It's a very simple little app, and really just a demonstration of how semantic web technologies might be made available to the masses. It was also the first time the guinea pigs had been allowed to play with the Google Apps Engine.
<h3>Who am I?</h3>
This short catch-up post has become something quite long and rambling. Did I mention that I'm sleep-deprived? Anyway, a recent addition to the Wragge Labs range of lifestyle accessories is <a href="http://wraggelabs.com/whoami/">'Who am I?' </a>– a simple little game that is something like a cross between hangman and Wheel of Fortune. Choosing a person at random from People Australia and the <em>Australian Dictionary of Biography</em>, 'Who am I?' tests your powers of logic, stamina and historical guesstimation.

Your challenge is to figure out the surname of the mystery historical personage. To help you there are a series of clues, such as their birthplace and known associates. With each guess you also see a little bit more of their portrait. But beware! For ten wrong guesses are all that are permitted to any so brave as to enter upon this quest. Not eleven or twelve, but ten and ten only. To ignore this limit is to invite ridicule and disdain – do so at your peril.

[caption id="attachment_858" align="aligncenter" width="300" caption="Play Who am I?"]<a href="http://wraggelabs.com/whoami/"><img class="size-medium wp-image-858" title="whoami" src="http://discontents.com.au/wp-content/uploads/2010/05/whoami-300x137.jpg" alt="Who am I screenshot" width="300" height="137" /></a>[/caption]

'Who am I' builds upon some work I've been doing for the National Museum of Australia – looking at ways of mashing together various types of date-identified data. As part of that project I've built a series of APIs and have scraped, pummelled and munged data from a variety of sources.

What's the point? I wonder this myself sometimes, particularly after I fling such things off into the aethernet and hear naught but a rare retweet. I am, after all, only in it for the glory, oh and the money of course. (Hmmm, I must look again at that business plan.) The point is twofold: first to highlight possibilities for the re-use and remixing of cultural data; second, to play with game-based models for discovery and exploration of cultural resources; and... err... thirdly just to try building something a little different.

Of course, if you like 'Who am I?' you will probably also want to try <a href="http://wraggelabs.com/newsroulette/">Headline Roulette</a>...
<h3>Headline Roulette Reprieve</h3>
At the end of <a href="http://discontents.com.au/shed/experiments/headline-roulette">our last instalment</a>, the future of <a href="http://wraggelabs.com/newsroulette/">Headline Roulette</a> seemed in dire peril. Changes to the National Library of Australia web site threatened its very existence. Did it have a future? Could it survive? And did anybody care?

As we pick up the story oblivion looms. The feared changes are confirmed, but just as all seems lost... is it? Could it be? Yes, an advanced search facility is added to the newspapers site within Trove. Sensing this may be their only opportunity, the guinea pigs leap into action, building <a href="http://bitbucket.org/wragge/nla-newspapers-scraper">a new screen-scraper</a>, saving Headline Roulette from doom, and setting the world upon the path to a safer, happier future.

In short, Headline Roulette will live on... so enjoy.
<h3>Handing out some presents</h3>
My head is easily turned by flattery and praise. Yes, I really am so shallow and so vain. But this means that if people say nice things to me, I'm inclined to give them presents.

As well as doing exciting things in the web 2.0 realm for the PROV, <a href="http://twitter.com/asaletourneau">@asaletourneau</a> leaves nice comments on this blog. So he earned himself a present. It's not much, but I <a href="http://userscripts.org/scripts/show/71421">built a userscript</a> that displays photos from the PROV site in a neat little slideshow (it's the non-3D javascript version of CoolIris). Install Greasemonkey, get the userscript and <a href="http://proarchives.imagineering.com.au/index_search.asp?searchid=41">try it out</a> (just do a search, then click on the 'Browse as slideshow' button').

[caption id="attachment_852" align="aligncenter" width="300" caption="PROV transport photos in a pretty slideshow"]<a href="http://discontents.com.au/wp-content/uploads/2010/05/prov-slideshow.jpg"><img class="size-medium wp-image-852" title="prov-slideshow" src="http://discontents.com.au/wp-content/uploads/2010/05/prov-slideshow-300x187.jpg" alt="Screen capture of slideshow" width="300" height="187" /></a>[/caption]

The State Library of NSW, or more specifically <a href="http://www.twitter.com/ellenforsyth">@ellenforsyth</a>, also earned my favour by inviting me to rave on about Linked Data at the afore-mentioned NSW RISG seminar. As a result, I added support for the SLNSW photo collections to my <a href="http://discontents.com.au/shoebox/archives-shoebox/harvesting-context-1">Flickr Context Harvester</a> userscript. Well... it's the thought that counts, right? Once again – install Greasemonkey, <a href="http://userscripts.org/scripts/show/56135">get the userscript</a> and then <a href="http://acms.sl.nsw.gov.au/item/itemDetailPaged.aspx?itemID=447435">try it out</a>.

[caption id="attachment_855" align="aligncenter" width="300" caption="The Flickr Context Harvester in action"]<a href="http://discontents.com.au/wp-content/uploads/2010/05/slnsw-flickr.jpg"><img class="size-medium wp-image-855" title="slnsw-flickr" src="http://discontents.com.au/wp-content/uploads/2010/05/slnsw-flickr-300x181.jpg" alt="Flickr context harvestr screenshot" width="300" height="181" /></a>[/caption]
<h3>And coming up...</h3>
Stay tuned for more on the Great Flickr Machine Tag Challenge, screencasts demonstrating my Identity Browser, some playing with relationships, and much much more. But right now the squirming baby on my lap needs a nappy change...

Did I mention that I'm sleep deprived?