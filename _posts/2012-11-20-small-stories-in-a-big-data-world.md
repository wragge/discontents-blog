---
ID: 1936
post_title: Small stories in a big data world
author: Tim Sherratt
post_date: 2012-11-20 16:47:18
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/small-stories-in-a-big-data-world/
published: true
tmac_last_id:
  - "640027521786884096"
---
<em>Presented at the</em> <a href="http://www.ndf.org.nz/">National Digital Forum</a><em>, Wellington, 20 November 2012. You can also <a href="http://webcast.gigtv.com.au/Mediasite/Play/ff5fcf8f9d9146caae57ca71b54294bf1d?catalog=0218e4a1-9070-4b7f-b051-54f1933da8e9">watch the video</a>.</em>

Previously at NDF:

<ul>
	<li><a href="https://twitter.com/jonvoss">Jon</a> talked about <a href="http://www.r2.co.nz/20111129/jon-v.htm">Linked Open Data</a>...</li>

	<li><a href="https://twitter.com/fogonwater">Chris</a> talked about <a href="http://www.r2.co.nz/20111129/chris-mcd.htm">making stories</a>...</li>
</ul>

As we return to the action, Tim is wondering what happens when we bring <strong>stories</strong> and <strong>data</strong> together...

<a href="http://discontents.com.au/wp-content/uploads/2012/11/ndf2012-5.005.jpg"><img src="http://discontents.com.au/wp-content/uploads/2012/11/ndf2012-5.005-520x390.jpg" alt="" title="ndf2012-5.005" width="520" height="390" class="aligncenter size-large wp-image-1940" /></a>

As historians, as cultural heritage professionals, as people -- we make connections, we make meanings. That's just what we do.

What really excites me about Linked Open Data is not the promise of smarter searches, but the possibilities for making connections and meanings in ways that are easier to traverse -- to explore, to wander, to linger, or even to stumble.

What really frustrates me about Linked Open Data is that we still tend to talk about it as if it's all engineering -- an international plumbing project to pump data around the globe. Linked Open Data doesn't have to be an industrial undertaking, it can be a craft, a mode of expression. It can be created with love or in anger.

And anyone can do it.

I'm currently working on <a href="http://mosman1914-1918.net/project/">a project with the Mosman Library</a> in Sydney to collect information about the World War I experiences of local service people. The web resource we're building will provide Linked Data all the way down. Every time someone adds a story about a person, uploads a photograph, identifies a place, or includes a link to another resource, they will be minting identifiers, creating relationships, documenting properties -- sharing their knowledge as Linked Open Data. 

It seems to me that Linked Open Data will be a success not when we've standardised on a few vocabularies, or linked everything we possibly can to DBpedia, but when have thriving online communities creating and sharing structured data about the things that are important to them. Not just the known and notable, but the local, the contested, the endangered, the ephemeral and the oppressed.

Many of us live within a Western tradition which equates knowledge with accumulation. Linked Open Data promises new means of aggregation, new powers of discovery -- lots and lots more stuff! But it would be a tragedy if all we ended up with was a bigger database or a better search engine. <strong>I want more</strong>. I want new ways of using that data, of playing with structures and scales. I want to build rich contexts around my stories.

Last year I talked about this in <a href="http://discontents.com.au/shoebox/every-story-has-a-beginning">a keynote I gave</a> to the Australian and New Zealand Society of Indexers. To try and demonstrate some of the possibilities, I created <a href="http://wraggelabs.com/shed/presentations/anzsi/">a fancy presentation</a> and added <a href="http://wraggelabs.com/shed/presentations/anzsi/rdfa_triples.txt">a whole lot of linked data</a> to the text of my talk. But it was a bit of a cheat. The text, the triples and the presentation were still pretty much separate. What I really wanted to do was use the linked data to generate alternative views of the text, to take my story and look at it through a variety of linked data powered filters.

So for NDF this year I thought I'd have another go. I set myself a few groundrules:

<ul>
	<li><strong>Simple tools</strong> -- should be possible for anyone with a text editor.</li>
	<li><strong>No platforms</strong> -- no sneaky server-side stuff, it all had to happen in the browser, on the fly.</li>
	<li><strong>No markup madness</strong> -- I wanted there to be a close relationship between the text and the data, but I wanted the markup process to be practical -- something like creating a footnote.</li>
</ul>

So I hacked together a whole lot of existing Javascript libraries. I used them to extract all the triples from my text and follow external identifiers to get extra information. Then I queried the little databank I'd made to generate four different views of my talk...

<strong>WARNING WARNING! <a href="http://wraggelabs.com/shed/presentations/ndf2012/storydata/">Very early demo!</a> Expect bugs and general stupidity!</strong>

Now, none of this looks terribly exciting. Visually the various components look pretty familiar -- and that's part of the point, I'm showing how you can re-use existing tools and code libraries.

What's interesting, I think, is the dialogue that's evolving between text and data -- a dialogue that's taking place within one, <em>just one</em>, html document.

[caption id="attachment_1943" align="aligncenter" width="520"]<a href="http://wraggelabs.com/shed/presentations/ndf2012/storydata/"><img src="http://discontents.com.au/wp-content/uploads/2012/11/Screen-Shot-2012-11-20-at-7.36.17-PM-520x407.png" alt="" title="" width="520" height="407" class="size-large wp-image-1943" /></a> Expect bugs ye who enter here...[/caption]

So here's the text of my talk to the indexers last year. As you scroll through the document, each paragraph on the screen is examined and information about related entities -- people, places, events, objects -- are displayed in a sidebar. The text and the sidebar are linked, so if you click on a link in the text more information about the related entity opens in the sidebar.

If you want to look at the resources separately you can. You can re-order, and filter by type.

<a href="http://wraggelabs.com/shed/presentations/ndf2012/storydata/"><img src="http://discontents.com.au/wp-content/uploads/2012/11/Screen-Shot-2012-11-20-at-7.52.05-PM-520x427.png" alt="" title="Screen Shot 2012-11-20 at 7.52.05 PM" width="520" height="427" class="aligncenter size-large wp-image-1952" /></a>

Then there's the fairly traditional timeline and map views.

Most of the data that's being displayed is coming from RDFa within the document, but not all. There are links to GeoNames and DBPedia that are drawing in data on the fly. As more Linked Open Data becomes available these links can become deeper and richer.

It's a very rough demo and I have a long to-do list -- for example better links between the data views and the text, showing their context within the narrative. But hopefully you can get an idea of how it might be possible to build data-rich stories -- with layers and views that enrich, inform and engage with the narrative.

And all just with one html page, a bit of RDFa and a few Javascript libraries.

There's no magic.

You might be wondering about my ground-rules -- why did I constrain myself? Well, it has to do with this thing we call 'access'. Oftentimes when we talk about access we mean the power to consume -- the power for people to take what they're given.

But to really have access, for something to be truly open, people also have to have the power to create. To take what they're given and build something new -- to challenge, to criticise, to offer alternatives.

That means allowing people the space to have ideas, giving them the confidence to experiment, providing useful tools and the knowledge to use them. That's not a job for any particular institution, or sector, it's a challenge for all of us who build things to strip away the magic and invite others to join in.

<strong>And I think it's pretty important.</strong> I don't really want to live in a world where data is just something that other people collect about and for us. I want slow data, as Chris described last year. I want us to enjoy the textures and tastes and not get addicted to the processed product. I want to create, enrich, wield and wonder.

So my vision of the future of Linked Open Data, is not of the Giant Global Graph linking all knowledge. <strong>But a revolutionary army of data-artisans, hand-crafting their richly contextualised stories into a glorious, messy, confusing, infuriating, WONDERFUL tapestry.</strong>

Now I know you're all just waiting for me to press the <strong>BOOM!</strong> button.

<a href="http://discontents.com.au/wp-content/uploads/2012/11/Screen-Shot-2012-11-20-at-7.48.40-PM.png"><img src="http://discontents.com.au/wp-content/uploads/2012/11/Screen-Shot-2012-11-20-at-7.48.40-PM.png" alt="" title="Screen Shot 2012-11-20 at 7.48.40 PM" width="481" height="49" class="aligncenter size-full wp-image-1949" /></a>

<strong>So let's blow some shit up!</strong>

<a href="http://discontents.com.au/wp-content/uploads/2012/11/Screen-Shot-2012-11-20-at-7.46.32-PM.png"><img src="http://discontents.com.au/wp-content/uploads/2012/11/Screen-Shot-2012-11-20-at-7.46.32-PM-520x243.png" alt="" title="Screen Shot 2012-11-20 at 7.46.32 PM" width="520" height="243" class="aligncenter size-large wp-image-1946" /></a>