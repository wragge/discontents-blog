---
ID: 1709
post_title: Topic modelling in the archives
author: Tim Sherratt
post_date: 2012-05-17 00:11:02
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/topic-modelling-in-the-archives/
published: true
tmac_last_id:
  - "640027533476413440"
  - "640027533476413440"
---
There seems to be a lot of topic modelling going on at the moment. Any why not? Projects like <a href="http://dsl.richmond.edu/dispatch/">Mining the Dispatch</a> are demonstrating the possibilities. Tools like <a href="http://mallet.cs.umass.edu/index.php">Mallet</a> are making it easy. And generous DHers like <a href="http://tedunderwood.wordpress.com/2012/04/07/topic-modeling-made-just-simple-enough/">Ted Underwood</a> and <a href="http://www.scottbot.net/HIAL/?p=221">Scott Weingart</a> are doing a great job explaining what it is and how it works.

I've talked briefly about using topic modelling to <a title="Mining the treasures of Trove" href="http://discontents.com.au/words/conference-papers/mining-the-treasures-of-trove">explore digitised newspapers</a>, something that the <a href="http://mappingtexts.org/">Mapping Texts</a> project has also been investigating. But I've also been following with interest Chad Black's <a href="http://parezcoydigo.wordpress.com/2011/09/23/an-algorithmic-approach-to-legal-culture-in-the-early-modern-spanish-empire/">use of algorithmic techniques</a>, including topic modelling, to look for local variations amidst the legal system of the early modern Spanish empire.

As part of the <a href="http://invisibleaustralians.org/">Invisible Australians</a> project, Kate and I are <a href="http://invisibleaustralians.org/blog/2011/12/inside-the-bureaucracy-of-white-australia/">exploring the bureaucracy</a> of the White Australia Policy. In particular, we're interested in the interaction between policy and practice, between the highly-centralised bureaucracy and the activities of individual port officials. Like Chad, we're interested in mapping local variations -- to try and understand the bureaucracy from the point of view of an individual forced to live within its restrictions.

I recently gave a presentation about the project at Digital Humanities Australasia (post coming soon!), and in preparation I decided to try a few topic modelling experiments. They were very simple, but I was impressed by the possibilities for exploring archival systems.

The problem I started with was this. The workings of the White Australia Policy are well documented by records held by the <a href="http://naa.gov.au">National Archives of Australia</a>. Some series within the archives are specifically related to the operations of the policy -- such as those containing <a href="http://invisibleaustralians.org/blog/2010/08/collecting-cedt-applications-and-certificates/">many thousands of CEDTs</a>. But there are also general correspondence series created by the customs offices in each state, as well as the Commonwealth Department of External Affairs which administered the Immigration Restriction Act (responsibility was later taken by the Department of Home and Territories and it's successors). These general correspondence series are important, because they often include details of difficult or controversial cases -- those that required a policy judgment, or prompted a change in existing practices. But how do you find relevant files within series that can contain large numbers of items?

<a href="http://www.naa.gov.au/cgi-bin/Search?Number=A1">Series A1</a>, for example, is a correspondence series created by the Department of External Affairs. It contains more than 60,000 items. Past research tells us that amongst these 60,000 files are records of important policy discussions relating to White Australia. But these files tend to be labelled with the names of the people involved, so unless you know the names in advance they can be difficult to find.

Mitchell Whitelaw's <a href="http://visiblearchive.blogspot.com.au/2009/08/exploring-a1-items-to-documents.html">A1 Explorer</a>, part of the <a href="http://visiblearchive.blogspot.com.au/">Visible Archive project</a>, lets you to explore the contents of Series A1 in a easy and engaging way. But while the A1 Explorer provides new opportunities for discovery, it doesn't offer the fine-grained analysis we need to sift out the files we're after. And so... topic modelling.

The process was pretty simple. While I can dip into my bag of screen-scrapers to harvest series directly from the NAA's <a href="http://www.naa.gov.au/collection/using/search/">RecordSearch</a> database, there was already an <a href="http://data.gov.au/dataset/commonwealth-agencies/">XML dump of A1</a> available from data.gov.au. So I extracted the basic file metadata from the XML and wrote the identifiers and titles out to a text file, one item per line. Following <a href="http://mallet.cs.umass.edu/import.php">the instructions on the website</a> I then loaded this file into Mallet:

<pre class="brush: bash; gutter: true; first-line: 1; highlight: []; html-script: false">/Applications/Mallet/bin/mallet import-file --input ./A1.txt --output A1.mallet --keep-sequence --remove-stopwords</pre>

Then it was just a matter of firing up the topic modeller:

<pre class="brush: bash; gutter: true; first-line: 1; highlight: []; html-script: false">/Applications/Mallet/bin/mallet train-topics --input ./A1.mallet --output-state ./A1.gz --output-doc-topics ./A1-topics.txt --output-topic-keys ./A1-keys.txt --num-topics 40</pre>

Again, I just <a href="http://mallet.cs.umass.edu/topics.php">followed the examples</a> on the Mallet site.

Once it was finished I opened up <a href="http://discontents.com.au/wp-content/uploads/2012/05/A1-keys.txt">A1-keys.txt</a> to browse the 'topics' Mallet had found. The results were intriguing. There are a large number of applications for naturalisation in A1, so it's no surprise that 'naturalisation' figures prominently in a number of the topics. What was more interesting was the way Mallet had grouped the naturalisation files. For example:

<code>naturalization christian hans hansen jensen petersen andersen nielsen larsen christensen johannes jens niels pedersen andreas johansen martin jorgensen</code>

and

<code>naturalisation certificate giuseppe salvatore frank la leo samios spina sorbello leonardo fisher natale patane torrisi barbagallo luka rossi ross</code>

Based on the co-occurrence of names within the file titles, Mallet had created groupings that roughly reflected the ethnic origins of applicants. It makes sense when you think about what Mallet is doing, but I still found it pretty amazing.

Mallet also found clusters around the major activities of the department, such as the administration of the territories. But of most interest to us was:

<code>1	0.55539	passport ah student exemption students lee wong chinese young deserter education sing wing chong readmission son hing chin wife</code>

The Chinese names alongside words such as 'readmission' and 'wife' suggested that this topic revolved around the administration of the White Australia Policy. This was easy to test. In A1-topics.txt was a list of every file in the series and their weightings in relation to each of the topics. I wasn't sure what was a reasonable cut-off value to use in assessing the weightings, but after a bit of trial and error I fixed on a value of 0.7. I then just extracted the identifiers of every file that had a weighting greater than 0.7 for this topic. I used the identifiers to build <a href="http://wraggelabs.com/shed/naa/">a simple web page</a> that Kate and I could browse. I also included links back to RecordSearch so we could explore further.

[caption id="attachment_1768" align="aligncenter" width="520" caption="Browse the full list"]<a href="http://wraggelabs.com/shed/naa/"><img src="http://discontents.com.au/wp-content/uploads/2012/05/Screen-Shot-2012-05-16-at-11.23.10-PM-520x224.png" alt="" title="Screen Shot 2012-05-16 at 11.23.10 PM" width="520" height="224" class="size-large wp-image-1768" /></a>[/caption]

It's a pretty impressive result. Instead of fumbling with the uncertainties of keyword searches, we now have a list of more than 1,300 files that are clearly of relevance to <a href="http://invisibleaustralians.org">Invisible Australians</a>. There's a few false positives and there are likely to be other files that we'll have missed altogether, but now we have a much clearer picture of the types of files that are included and how they are described.

And that was at my first attempt, simply using the default settings. I'm now starting to play around with some of Mallet's configuration options to see what sort of difference they make. I'm also keen to try out <a href="http://radimrehurek.com/gensim/">GenSim</a>, a topic modelling package for Python.

I'm really excited about the possibilities of these sort of tools for analysing the contents of archival descriptive systems, something I mentioned in my Digital Humanities Australasia paper. Much more to come on this I suspect...


