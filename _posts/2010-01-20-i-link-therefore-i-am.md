---
ID: 761
post_title: I link therefore I am
author: Tim Sherratt
post_date: 2010-01-20 10:25:03
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/i-link-therefore-i-am/
published: true
tmac_last_id:
  - "640027559816728576"
---
Let me be clear. I am not Tim Sherratt the sound engineer. Nor, indeed, am I Timothy Sherratt, author of <em>Saints as Citizens: A Guide to Public Responsibilities for Christians</em>. We are three different people, spread across three continents, locked in a deadly battle for global supremacy via <a href="http://www.google.com/#hl=en&source=hp&q=tim+sherratt&btnG=Google+Search&aq=f&aql=&aqi=&oq=tim+sherratt">Google search rankings</a>. There can be only one...

Of course you probably knew I wasn't a British sound engineer or an American politics professor. There are plenty of contextual clues within this website, even on this page, to indicate that my interests lie elsewhere. But while we humans are pretty good at picking up such clues, it's much harder for computers. When Google comes to index my site, how does it know I'm not a sound engineer who likes to dabble in history? Indeed, how does Google, or any computer know that the words 'Tim Sherratt' are actually a person's name? These are questions of both identity and semantics.

Librarians have been dealing with questions of identity for many, many years developing detailed name authority records. Such records allow name variations to be cross-referenced and individuals to be uniquely identified. For example I have a control number of 'n 2005043272' in the <a href="http://authorities.loc.gov/">Library of Congress authorities database</a>, while Timothy R Sherratt, the politics professor has been assigned 'n  94106739'.

The National Library of Australia has developed its own name authority file. However, the NLA has realised that reliable identity data has a much broader application that simply cataloguing, and is using its name authority data as the foundation of an exciting new resource – <a href="http://www.nla.gov.au/initiatives/peopleaustralia/">People Australia</a>. People Australia will mesh its own records with biographical data from a variety of outside sources, creating a rich collection of interlinked identities. Already entries from the Australian Dictionary of Biography have been ingested.

So now, thanks to People Australia, if I ever get confused about who I am I just have to remember one little url – my very own persistent identifier – <a href="http://nla.gov.au/nla.party-479364">http://nla.gov.au/nla.party-479364</a>. I'm going to get a t-shirt made up.

But that doesn't help our new machine overlords very much. How can a computer tell that the words 'Tim Sherratt' describe a person and that more information about that person can be found at http://nla.gov.au/nla.party-479364? This is the sort of problem that the semantic web hopes to solve. The semantic web aims to expose the structures that are buried in our documents and databases, to make explicit the contextual clues that humans pick up, but computers ignore. As the slogan goes, it represents a change from a 'web of documents to a web of data'.

The semantic web uses a variety of tools and standards to encode information in a form that means something to computers. <a href="http://www.foaf-project.org/">FOAF</a> (Friend of a Friend) is, for example, a machine-readable ontology that describes people and their relationships. A computer visiting this page can in fact find out a fair bit about me, including my NLA persistent identifier, because there is a link to a small XML file in which my details are <a href="http://discontents.com.au/foaf.rdf">expressed using FOAF</a>.

But if this seems a little daunting, the semantic web offers another technology which is really just as easy as marking up a page in HTML – it's called RDFa. This link – <!--start_raw--><a typeof="foaf:Person" property="foaf:name" content="Sherratt, Tim" rel="foaf:isPrimaryTopicOf" href="http://nla.gov.au/nla.party-479364">Tim Sherratt</a><!--end_raw--> – is more than it seems. Here is what a computer sees:

<code>&lt;a typeof="foaf:Person" property="foaf:name" content="Sherratt, Tim" rel="foaf:isPrimaryTopicOf" href="http://nla.gov.au/nla.party-479364"&gt;Tim Sherratt&lt;/a&gt;</code>

This says that Tim Sherratt is a person whose name has the standard form 'Sherratt, Tim' and who is the primary topic of the page to be found at http://nla.gov.au/nla.party-479364. There's a fair bit of semantic goodness in that one little link. If the NLA page also expressed its data in a machine-readable form, this link could send search engines and browsers into a whole new world of associations and inferences.

But I suppose you're thinking that the code still looks a bit complicated. Well never fear, this long post is really just an introduction to a new project I've been working on – something that will help you generate markup like this with just a couple of clicks.

<h3>Introducing Wragge's identity browser</h3>

I've been interested in publishing biographical data way back from the early days of <a href="http://www.asap.unimelb.edu.au/bsparcs/">Bright Sparcs</a> and, sad as it may seem, I find the possibilities of People Australia pretty exciting. However, I don't think we should expect the NLA to do all the work. People Australia provides a framework that we can all use to enrich our own documents, databases, finding aids, and applications.

You can easily access People Australia data through <a href="http://trove.nla.gov.au/">Trove</a>. But to get a better idea of what's in the database, I'd suggest you spend some time playing with its <a href="http://www.nla.gov.au/apps/srw/search/peopleaustralia">SRU interface</a>. Using this you can query the database directly, retrieving results in XML – ready for your own application to suck up and use.

To make this even easier, I've written a <a href="http://bitbucket.org/wragge/people-australia-client/">People Australia client library</a> in Python. This enables you to quickly extract and use identity information. Using it, your own web application can talk to People Australia directly. I won't go into the details here – the code is farily heavily commented – but I welcome any feedback, suggestions or contributions. Copy it, change it, use it!

To try out my library and to provide a tool that might be of use to the average punter I've also built:

&lt;TA-DA&gt;<a href="http://wraggelabs.com/people/"><strong>Wragge's identity browser</strong></a>!&lt;/TA-DA&gt;

It's pretty simple. Search for a surname, pick a name from the result list, and view their identity details. For example, here's <a href="http://wraggelabs.com/people/612109/">Clement Wragge's details</a>.

But there are a couple of extra features that I am rather smugly pleased with. First of all, there's an <!--start_raw--><a href="javascript:(function(){var%20selText;if%20(window.getSelection){if%20(document.activeElement%20&&%20(document.activeElement.tagName.toLowerCase()=='textarea'%20||%20document.activeElement.tagName.toLowerCase()=='input')){var%20text=document.activeElement.value;selText=text.substring(document.activeElement.selectionStart,document.activeElement.selectionEnd);}else{var%20selRange=window.getSelection();selText=selRange.toString();}}else{if%20(document.selection.createRange){var%20range=document.selection.createRange();selText=range.text;}}if%20(selText!=''){var%20url='http://wraggelabs.com/people/?context='+escape(selText);window.open(url);}else{alert('Select%20some%20text%20first!');}})();">'Identify me!'</a><!--end_raw--> bookmarklet. Just drag the link to your browser's bookmarks or favourites toolbar (see below for some further notes).

Once you have the bookmarklet installed all you have to do to find the identity record for someone is to highlight their name on a webpage and click 'Identify me!'. You could then grab the People Australia ID to store in your own application, allowing you (with the help of my client library) to automatically include links to relevant entries in the <em>Australian Dictionary of Biography</em>, for example.

Even better, Wragge's identity browser will automagically generate the RDFa markup you need to semantically enrich your document. Whether you're writing a blog post, publishing an article, drafting a caption, creating a database entry, or preparing a finding aid you can quickly and easily find an individual and then cut and paste the code you need.

To show this in action I used the bookmarklet to help me mark up many of the people named in one of my articles. We humans see a <a href="http://discontents.com.au/words/magazines-articles/looking-at-the-sun">normal page with a few extra links</a>. Computers, however, can extract the embedded RDFa to get at the <a href="http://www.w3.org/2007/08/pyRdfa/extract?uri=http%3A%2F%2Fdiscontents.com.au%2Fwords%2Fmagazines-articles%2Flooking-at-the-sun&format=pretty-xml&warnings=false&parser=lax&space-preserve=true&submit=Go!&text=">structured information that's hidden in the page</a>.

Now I've got to go and semantify the rest of my articles...

Go forth and identify! And in the process help build a better web.

<h4>Notes on the bookmarklet</h4>
<ul>
<li>Internet Explorer has 'Favorites', Firefox has 'Bookmarks' – whatever you're using first make sure that your Bookmarks/Favourites toolbar is visible. Look under Tools->Toolbars in IE8, View->Toolbars in Firefox. </li>
<li>Try dragging the 'Identify me!' link to your Bookmarks/Favourites toolbar. If it doesn't work, try right clicking on the link and choose 'Bookmark this link' or 'Add to Favourites'. Make sure you add it to the toolbar folder. IE will probably give you various warnings – ignore them.</li>
<li>You should now have a working bookmarklet – highlight a name and click on it, a new window should open with results from Wragge's identity browser. IE might complain about opening a pop-up – allow pop-ups and try again.</li>
<li>The bookmarklet is pretty clever about working out which part of the highlighted text is the surname, so you can highlight names in a number of formats including:
<ul>
<li>Surname</li>
<li>Surname's</li>
<li>Surname, Othernames</li>
<li>Othernames Surname</li>
<li>Othernames Surname's</li>
</ul>
</li>
<li><del datetime="2010-01-26T12:34:24+00:00">For the moment this only works with 'straight', ie non-curly, apostrophes – but I'll fix this asap.</del> Fixed!</li>
</ul>
<h4>Notes on RDFa markup</h4>
<ul>
<li>You have a choice between visible (ie clickable) links or invisible ones. They look the same to computers, so it's just a matter of whether you want your human visitors to see them. Click 'change' to toggle between the two options.</li>
<li>You can just paste the RDFa markup straight into your document. If you've used the bookmarklet, the text you highlighted will be automatically inserted as the link text – so just copy and paste. If you haven't used the bookmarklet you can insert the link text yourself.</li>
<li>Somewhere in your document you need to tell computers what the FOAF in your RDFa markup means. You do this by inserting the text:
<code>xmlns:foaf="http://xmlns.com/foaf/0.1/"</code> inside a tag that contains your marked up text. If you can edit the raw html of your page, you can just insert it in the <code>&lt;html&gt;</code> tag itself, so it becomes <code>&lt;html xmlns:foaf="http://xmlns.com/foaf/0.1/" &gt;</code>. Otherwise you can wrap your marked up text in a <code>&lt;div&gt;</code> tag and put the extra code in there.
</li>
<li>If you're using something like Wordpress that strips out or converts any markup that it doesn't expect, you need to be able to enter the RDFa as 'raw' html. In Wordpress you can do this using the <a href="http://wordpress.org/extend/plugins/raw-html/">Raw HTML plugin</a>.</li>
<li>For more on using RDFa have a look at: <a href="http://www.w3.org/MarkUp/2009/rdfa-for-html-authors">RDFa for HTML Authors</a>.
</ul> 

















