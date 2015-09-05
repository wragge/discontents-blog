---
ID: 2197
post_title: Have collection, will travel
author: Tim Sherratt
post_date: 2014-01-04 21:24:14
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/have-collection-will-travel/
published: true
tmac_last_id:
  - "640027512207110145"
---
A few years ago it seemed fashionable for cultural institutions to create a 'My [insert institution name]' space on their website where visitors could create their own online exhibits from collection materials. It bothered me at the time because it seemed to be a case of creating silos within silos. What could people do with their collections once they'd assembled them? I was reminded of this recently as I undertook my Christmas-break mini project to think about [Trove][1] integration with [Zotero][2]. Some years ago I created a Zotero translator for the Trove newspaper zone, but I'd much rather we just exposed metadata within Trove pages that Zotero (and other tools like [Hypothes.is][3] and [Mendeley][4]) could pick up without any special code. More about that soon... However. embedded metadata only addresses part of the problem -- there's also questions around tools and workflows. Trove includes a number of simple tools that enable users to annotate and organise resources -- tags, comments, and lists. Tags and comments... well you know what they are. Lists are just collections of resources, and like tags, they can be public or private. They may not be terribly exciting tools, but they are very heavily used. More than [2 million tags][5] have been added by Trove users, but it's lists that have shown the most growth in recent times. There are currently more than 47,000 lists and [30,000 of those are public][6]. That's a pretty impressive exercise in collection building. What are the lists about? A few months ago I harvested the titles of all public lists and threw them into Voyant for a quick word frequency check. [caption id="attachment_2201" align="aligncenter" width="520"][<img src="http://discontents.com.au/wp-content/uploads/2014/01/all-trove-lists1-520x342.png" alt="Word frequencies in the titles of Trove lists" width="520" height="342" class="size-large wp-image-2201" />][7] Word frequencies in the titles of Trove lists[/caption] Given what we know about Trove users, it wasn't surprising to see that many of the lists related to family history, but there are a few wonderful oddities buried in there as well. I love to be surprised by the passions of Trove users. I suspect these tools are popular because they're simple and open-ended. There are few constraints on what you can use for a tag or add to a list. Following some threads about game design recently I came upon [a discussion of 'underspecified' tools][8] -- 'the use of which you can never fully predict'. By underspecifying we leave open possibilities for innovation, experimentation and play. It seems like a pretty good design approach for the cultural heritage sector. But wait a minute, you might be wondering, what sort of Trove Manager magic did I have to weave in order to extract those thousands of list titles? None, none at all. *You* could do exactly the same thing. I've been talking a lot in recent months about [Trove as a platform][9] rather than a website -- something to build on. One of our main construction tools is, of course, the [Trove API][10]. I suppose a good cultural heritage API is also underspecified -- focused enough to be useful, but fuzzy enough to encourage a bit of [screwing around][11]. What you may not know about the Trove API is that as well as giving you access to around 300 million resources, it lets you access user comments, tags and lists. I'm looking forward to researchers using the API to explore the various modes of meaning-making that occur around resources in Trove. But right now one thing it offers is portability -- the collections people make can be moved. And that brings us back to Zotero. Why should a Trove user have to decide up front whether they want to use Zotero or create a Trove list? Pursuing [Europeana's][12] exciting vision of putting collections in our workflows we need to recognise that workflows change, projects grow, and new uses emerge. We should support and encourage this by making it as easy as possible for people to move their stuff around. So of course I had to build something. My Christmas project has resulted in [some Python code][13] that lets you export a Trove list or tag to a Zotero collection -- API to API. Again it's a simple idea, but I think it opens up some interesting possibilities for things like collaborative tagging projects -- with a few lines of code hundreds of tagged items could be saved to Zotero for further organisation or annotation. Along the way I ended up starting a more general [Trove-Python library][14] -- it's very incomplete, but it might be useful to someone. It's all on GitHub -- shared, as usual, not because I think the code is very good, but because I think it's really important to share examples of what's possible. Hopefully someone will find a slender spark of inspiration in my crappy code and build something better. Needless to say, this isn't an official Trove product. So what do you do if you want to export a list or tag? First of all get yourself Python 2.7 and set up a virtualenv where you can play without messing anything up. Then install my library... <pre class="brush: shell; gutter: true; first-line: 1; highlight: []; html-script: false">git clone https://github.com/Trove-Toolshed/trove-python.git
cd trove-python
python setup.py install</pre> You'll also need to install 

[PyZotero][15]. Once that's done you can fire up Python and export a list from the command line like this... <pre class="brush: python; gutter: true; first-line: 1; highlight: []; html-script: false">from pyzotero import zotero
from trove_python.trove_core import trove
from trove_python.trove_zotero import export

zotero_api = zotero.Zotero(&#039;[Your Zotero user id]&#039;, &#039;user&#039;, &#039;[Your Zotero API key]&#039;)
trove_api = trove.Trove(&#039;[Your Trove API key]&#039;)

export.export_list(list_id=&#039;[Your Trovelist id]&#039;, zotero_api=zotero_api, trove_api=trove_api)</pre> Obviously you'll also need to get yourself a 

[Trove API key][10], and a Zotero key for your user account. Exporting items with a particular tag is just as easy... <pre class="brush: python; gutter: true; first-line: 1; highlight: []; html-script: false">from pyzotero import zotero
from trove_python.trove_core import trove
from trove_python.trove_zotero import export

zotero_api = zotero.Zotero(&#039;[Your Zotero user id]&#039;, &#039;user&#039;, &#039;[Your Zotero API key]&#039;)
trove_api = trove.Trove([&#039;Your Trove API key&#039;])
exporter = export.TagExporter(trove_api, zotero_api)

exporter.export(&#039;[Your tag]&#039;)</pre> What do you end up with? Here's my 

[test list][16] on Trove and the [resulting Zotero collection][17]. Here's a set of resources tagged with ['inigo'][18], and here's [the collection][19] I created from them. You'll notice that I added a few little extras, like attaching pdf copies where they're available. Sorry, no GUIs, no support, and not much documentation. Just a bit of rough code and some ideas to play with.

 [1]: http://trove.nla.gov.au
 [2]: http://zotero.org
 [3]: http://hypothes.is/
 [4]: http://www.mendeley.com/
 [5]: http://trove.nla.gov.au/tag?
 [6]: http://trove.nla.gov.au/list/result?q=
 [7]: http://discontents.com.au/wp-content/uploads/2014/01/all-trove-lists1.png
 [8]: http://leapfrog.nl/blog/archives/2008/11/17/a-playful-stance-my-game-design-london-2008-talk/
 [9]: http://www.nla.gov.au/our-publications/staff-papers/from-portal-to-platform
 [10]: http://trove.nla.gov.au/general/api
 [11]: http://www.playingwithhistory.com/wp-content/uploads/2010/04/hermeneutics.pdf
 [12]: http://europeana.eu/
 [13]: https://github.com/Trove-Toolshed/trove-python/tree/master/trove_python/trove_zotero
 [14]: https://github.com/Trove-Toolshed/trove-python
 [15]: https://github.com/urschrei/pyzotero
 [16]: http://trove.nla.gov.au/list?id=50196
 [17]: https://www.zotero.org/wragge/items/collectionKey/64KM5QZX
 [18]: http://trove.nla.gov.au/result?q=publictag:(inigo)
 [19]: https://www.zotero.org/wragge/items/collectionKey/7JBIBPWF