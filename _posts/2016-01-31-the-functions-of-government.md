---
ID: 2703
post_title: The functions of government
author: Tim Sherratt
post_date: 2016-01-31 22:38:38
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/the-functions-of-government/
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
What are the functions of government? You'll find one possible answer in the <a href="http://www.naa.gov.au/records-management/publications/agift.aspx">Australian Governments' Interactive Functions Thesaurus</a> (AGIFT) maintained by the <a href="http://www.naa.gov.au/">National Archives of Australia</a>. AGIFT sets out a <a href="http://agift.naa.gov.au/">standard series of terms</a> to describe common business activities across the different levels of government.

Functions are important to the National Archives -- they aid discovery, inform appraisal, and <a href="http://www.naa.gov.au/records-management/publications/afda.aspx">guide government agencies</a> in understanding what records they should keep keep. Functions also offer researchers an alternative way of exploring the Archives' rich collections -- instead of blindly searching for keywords, you can track the activities of government agencies through time.

<a href="http://recordsearch.naa.gov.au/scripts/Logon.asp?N=guest">RecordSearch</a>, the National Archives' online database, provides a simple way of browsing by function, though it's not very obvious. Click on the 'Advanced Search' tab in RecordSearch and you'll see an interactive diagram representing the way that records are described and arranged using the Commonwealth Records Series (CRS) system. I made this little widget a very long time ago, and there's <a href="http://wraggelabs.com/shed/crs/crs_diagram.html">an alternative version</a>, with links to the CRS manual, over at WraggeLabs.

[caption id="attachment_2704" align="aligncenter" width="711"]<a href="http://discontents.com.au/wp-content/uploads/2016/01/Screen-Shot-2016-01-31-at-6.30.00-PM.png" rel="attachment wp-att-2704"><img class="size-large wp-image-2704" src="http://discontents.com.au/wp-content/uploads/2016/01/Screen-Shot-2016-01-31-at-6.30.00-PM-1024x593.png" alt="The CRS System" width="711" height="412" /></a> The CRS System[/caption]

You'll notice that functions are associated with agencies -- they're a way of describing what government departments do. Click on the 'Functions' button to open up a very basic browse interface that lists preferred and alternative names for functions. There seem to be a few differences between AGIFT and the terms used in RecordSearch, I'm not sure why. The CRS Manual includes a <a href="http://recordsearch.naa.gov.au/manual/Provenance/SummaryCRSThes.htm">summary of the thesaurus</a> used in RecordSearch, and for convenience I've extracted a <a href="https://github.com/wragge/recordsearch-functions/blob/master/functions.txt">flat list</a> of all the functions.

Just click on any function in RecordSearch to find agencies associated with it. It's basic, but it does at least provide an alternative to the tyranny of the search box, so well <a href="http://www.digitalhumanities.org/dhq/vol/9/1/000205/000205.html">described by Mitchell Whitelaw</a>. If you're starting a research project and don't know what keywords are relevant, perhaps following functions will help you map the territory.

[caption id="attachment_2718" align="aligncenter" width="711"]<a href="http://discontents.com.au/wp-content/uploads/2016/01/Screen-Shot-2016-01-31-at-10.28.05-PM.png" rel="attachment wp-att-2718"><img class="wp-image-2718 size-large" src="http://discontents.com.au/wp-content/uploads/2016/01/Screen-Shot-2016-01-31-at-10.28.05-PM-1024x349.png" alt="Screen Shot 2016-01-31 at 10.28.05 PM" width="711" height="242" /></a> Functions in RecordSearch[/caption]

Functions also provide a way of exploring how the organisation of government changes to meet social and political needs. How are the government's priorities in areas such as 'migration', 'education' or 'security' reflected in the sorts of bureaucratic structures they create? To answer this type of question you really need to extract all the data related to a function for further analysis and manipulation, but that's not something you can easily do through RecordSearch's web interface. Time for some hacking...

Harvesting data from RecordSearch has been something of an obsession over the past five or six years. Over that time I've <a href="https://github.com/wragge/recordsearch_tools">developed a set of tools</a> that pull structured data out of the web interface. I've used these tools to <a href="http://discontents.com.au/the-real-face-of-white-australia/">expose records relating to the White Australia Policy</a>, to grab a copy of <a href="https://github.com/wragge/asio-files">every publicly available ASIO file</a>, and to analyse records that remain <a href="https://github.com/wragge/closed_access">closed to public access</a>. But to harvest functions I needed to extend my toolkit -- improving the handling of agency data, and adding a simple search module to find all agencies associated with a function. Once this was done I could build a harvester -- a script that just makes a series of requests to RecordSearch until all of the desired records have been retrieved, processed and stored.

All the code for my <a href="https://github.com/wragge/recordsearch_tools">toolkit</a> and <a href="https://github.com/wragge/recordsearch-functions">harvester</a> are freely available on GitHub -- please download, use and improve! I've tried to provide fairly detailed instructions with the harvester, but you will need to fiddle about on the command line.

I haven't done anything very exciting yet -- I just wanted to make sure it was all possible. So far I've harvested data about agencies related to 'MIGRATION' and its associated functions 'CITIZENSHIP', 'DEPORTATION', 'MIGRANT SERVICES', 'MULTICULTURALISM', 'PASSENGER ENTRY CONTROL', and 'REFUGEES'. You can view <a href="https://github.com/wragge/recordsearch-functions/tree/master/data">CSV-formatted summaries</a> for each function on GitHub.

The <a href="https://github.com/wragge/recordsearch-functions/blob/master/data/migration.csv">CSV file for MIGRATION</a>, for example, lists 191 associated agencies. These range from departments of state, such as the current <a href="https://github.com/wragge/recordsearch-functions/blob/master/data/migration.csv#L189">Department of Immigration and Border Protection, Central Office</a>, to smaller bodies like the <a href="https://github.com/wragge/recordsearch-functions/blob/master/data/migration.csv#L71">Committee on Overseas Professional Qualifications</a>. For each agency I've listed it's status, location, life dates, and the dates during it was associated with the migration function. This is only a summary of the data I have for each agency, which includes relationships with other agencies, as well as details of any other related functions. It would be interesting to use this to draw out possible connections between functions.

As a preliminary experiment I thought it'd be interesting to create a simple timeline displaying the different government departments associated with immigration since 1900. I was trying to avoid too much coding, so I ended up hacking Plot.ly's basic line chart. As a visualisation it's not very exciting, but as an initial poke at the data it's <a href="https://plot.ly/~wragge/384/commonwealth-agencies-department-of-state-associated-with-the-function-migration/">quite encouraging</a>.

<iframe src="https://plot.ly/~wragge/384.embed" width="900" height="800" frameborder="0" scrolling="no"></iframe>

Hover over the lines to see the agency names and date ranges. Click on one of the agency identifiers (the CA numbers) to open its page in RecordSearch.

The code to create the CSV summaries as well as simple charts like this is all included with the harvester in my <a href="https://github.com/wragge/recordsearch-functions">RecordSearch Functions</a> repository. I'll add tools and examples as work proceeds or time allows. Hope you find it useful.