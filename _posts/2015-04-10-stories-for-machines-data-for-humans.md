---
ID: 2499
post_title: Stories for machines, data for humans
author: Tim Sherratt
post_date: 2015-04-10 16:44:07
post_excerpt: ""
layout:
  - default
permalink: >
  http://discontents.com.au/stories-for-machines-data-for-humans/
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
  - default
unlink_post_image:
  - default
citation:
  - ""
builder_switch_frontend:
  - "0"
tmac_last_id:
  - "640027502887354368"
---
*Presented at the New Factual Storytelling symposium, 10 April 2015, University of Canberra* I feel like the nerdy kid at the cool kids' party. There are lots of interesting and creative projects on show today and I... well I want to talk to you about metadata. Data. According to some pundits it's the new oil, or the new electricity. Fuel for economic development -- a raw material ready to be 'mined' for insights, innovation and our purchasing preferences. In the cultural heritage sector the data metaphors are more likely to be framed around liberation than exploitation. Our data wants to be 'open'. But there's still a tendency to think on an industrial scale -- it's about pumping out large datasets for potential re-use. What can be lost in metaphors of extraction and scale is an appreciation of the human origins of data. We are not buoys bobbing in the ocean reporting on the heights of passing waves. Big data is made up of many small acts of living. So today I want to talk about small-scale, free-range, artisanal data. I want to talk about data, alongside storytelling, as the product of creativity, imagination, frustration and fury. Let's think for a moment about the work of a historian -- identifying actors, defining relationships, documenting the complex networks that bring together people, places and events over time. It's painstaking, exhilirating and potentially soul-destroying work. It's also an exercise in data modelling. Whether the results are preserved in a triplestore, a spreadsheet, or on a drawer full of index cards -- it's nodes and edges, it's entities and relationships, it's data. And that's ok. Making data doesn't condemn you to a rigidly empirical, deterministic framework. There's always room for nuance, interpretation and doubt. there's always room for stories. But what happens when historians undertake the oddly-named process of 'writing up'. The complex data models are flattened down to a series of sentences neatly arranged in linear sequence -- our things become strings. The data is squeezed out and discarded, glimpsed only as fragile echoes hiding in footnotes. This is of course part of the skill of historical writing -- the ability to represent complex relationships through narrative. But why can't we have our stories and data too? This is a question I've returned to a number of times over the last few years. It's come up because I get excited about Linked Open Data's potential to deliver structured, machine-readable information via the web. But then I wonder, whose stories will we be telling to the machines. How can we explore the expressive possibilities of Linked Open Data and not be constrained by instrumentalist assumptions about the models we make. It's come up because I get excited about embedding cultural heritage collections within the passion and practice of everyday life. Why squeeze out the data from historical publications when every article could be an online exhibition, every book could be a digital portal, every footnote could be a link for exploration and aggregation? I don't really have answers, but I do make stuff. I've a [few goes][1] at trying to [create narratives][2] that [embed][3] Linked Open Data. They're not very exciting from a design point of view, but I keep coming back to them because there still seems to be a lack of alternatives. There's lots of talk about publishing Linked Open Data, but much less about how the use and consumption of Linked Open Data can be built into creative practice. So here I am again. This exercise has a number of constraints built in. The main one is NO PLATFORMS -- a historian using a series of simple tools should be able to create and publish a data-driven web page without any dependencies. It should be as simple as uploading an html page to a server. In my idealised workflow, the historian would manage their data about people, places, events and resources in a simple database capable of exporting a flavour of Linked Open Data known as JSON-LD. [<img class="aligncenter size-large wp-image-2500" src="http://discontents.com.au/wp-content/uploads/2015/04/docLab2015.004-1024x768.jpg" alt="docLab2015.004" width="1024" height="768" />][4] [<img class="aligncenter size-large wp-image-2502" src="http://discontents.com.au/wp-content/uploads/2015/04/docLab2015.006-1024x768.jpg" alt="docLab2015.006" width="1024" height="768" />][5] Then, having created their narrative, they'd mark it up in the tool of their choice to relate specific names or phrases in the text to the entities in their database. [<img class="aligncenter size-large wp-image-2503" src="http://discontents.com.au/wp-content/uploads/2015/04/docLab2015.007-1024x768.jpg" alt="docLab2015.007" width="1024" height="768" />][6] Then they'd just drop the text and the data into a html page and whack it on the web. With a bit of javascript magic to activate the data, you'd have [something like this][7]... [<img class="aligncenter size-large wp-image-2504" src="http://discontents.com.au/wp-content/uploads/2015/04/docLab2015.008-1024x768.jpg" alt="docLab2015.008" width="1024" height="768" />][7] The [demo is live][7] (though still under construction), so have a play. 
*   Scroll the text to see those carefully inserted identifiers create pop ups in the sidebar.
*   The text has itself become data, each paragraph is an object -- try filtering the text or linking to an [individual paragraph][8].
*   Browse all the [people][9], or [resources][10]. Explore all the relationships for [Inigo Jones][11].
*   Mapping to existing identifiers from sources like Trove and Wikipedia help put the 'linked' into Linked Open Data.
*   There's a rather boring [map][12], a [timeline][13] and a [wall][14] view. New views could be easily added by dropping in some extra javascript.
*   It's all data, so other visualisations and analyses might be created on the fly. That's what humans see, but what about machines? All the carefully curated data is exposed in a machine-readable form. Lots of triples... 

[<img class="aligncenter size-large wp-image-2505" src="http://discontents.com.au/wp-content/uploads/2015/04/docLab2015.009-1024x768.jpg" alt="docLab2015.009" width="1024" height="768" />][15] The code for the [viewer][16] and [maker][17] is all available if anyone wants to play with it, and I'm intending this year to develop two substantial monographs using these tools. Both have many links into cultural collections. My aim here is not to develop a fully-operational publishing system. I just want to get a better idea of what's useful, what's interesting, what's possible. To think beyond the current limits of scholarly publishing into a world where data and narrative can live together, where interpretative work is represented in all data-inflected glory.

 [1]: http://discontents.com.au/every-story-has-a-beginning/ "Every story has a beginning"
 [2]: http://discontents.com.au/small-stories-in-a-big-data-world/ "Small stories in a big data world"
 [3]: http://discontents.com.au/a-map-and-some-pins-open-data-and-unlimited-horizons/ "‘A map and some pins': open data and unlimited horizons"
 [4]: http://discontents.com.au/wp-content/uploads/2015/04/docLab2015.004.jpg
 [5]: http://discontents.com.au/wp-content/uploads/2015/04/docLab2015.006.jpg
 [6]: http://discontents.com.au/wp-content/uploads/2015/04/docLab2015.007.jpg
 [7]: http://lodbookdev.herokuapp.com/
 [8]: http://lodbookdev.herokuapp.com/#!/text/9/
 [9]: http://lodbookdev.herokuapp.com/#!/people
 [10]: http://lodbookdev.herokuapp.com/#!/resources
 [11]: http://lodbookdev.herokuapp.com/#!/people/1
 [12]: http://lodbookdev.herokuapp.com/#!/places/map
 [13]: http://lodbookdev.herokuapp.com/#!/events/timeline
 [14]: http://lodbookdev.herokuapp.com/#!/wall
 [15]: http://discontents.com.au/wp-content/uploads/2015/04/docLab2015.009.jpg
 [16]: https://github.com/wragge/lod-books-viewer
 [17]: https://github.com/wragge/lod-books-maker