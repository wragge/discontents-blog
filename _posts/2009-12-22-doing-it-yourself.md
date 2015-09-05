---
ID: 738
post_title: Doing it yourself
author: Tim Sherratt
post_date: 2009-12-22 21:21:31
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/doing-it-yourself/
published: true
tmac_last_id:
  - "640027560470941698"
---
I was doing some research using the National Archives of Australia's [RecordSearch][1] database the other day and became frustrated that there is no way of seeing how many pages are in a digitised file without clicking on the 'Display digital copy' link. So [I fixed it][2]. As a userscript it's hardly worthy of a blog post. All it does it find out how many pages are in the file and insert the number in the link text. It's very simple. But I think it's also a useful illustration of the changing balance of power between archives and their users. William E Landis argued that archivists were 'guilty as a profession of fetishising the outputs of our descriptive systems'. ((William E. Landis, ‘Nuts and bolts – Implementing descriptive standards to enable virtual collections’, *Journal of Archival Organization*, vol. 1, no. 1, 2002, p. 90.)) The design of finding aids have often been determined not by the needs of users but by a desire to faithfully represent the underlying archival architecture. But now users don't have to just take what they're given. Technologies such as [Greasemonkey][3] are useful for sketching out alternatives. For organisations with IT systems that inhibit experimentation, Greasemonkey (or [Mozilla's Jetpack][4]) provides a way of playing with interfaces without touching any of the underlying code. My rewrite of the way RecordSearch [displays digitised files][5] is an example of this. But no one interface is ever going to meet the needs of all archive users. Fortunately, there are a growing number of ways in which archives can work in partnership with their users to help *them* create the interfaces they want and need. Archives are starting to expose their data directly using APIs and linked open data. This gives users the power to create whole new applications. But I still think there'll be a place for the little tweak – a simple hack that meets some small but specific need. I can imagine communities of interest building and sharing a range of tools, hacks, applications and interfaces specifically tailored to their research habits. So if you don't like it, fix it.

 [1]: http://naa.gov.au/collection/recordsearch/index.aspx
 [2]: http://userscripts.org/scripts/show/64722
 [3]: https://addons.mozilla.org/en-US/firefox/addon/748
 [4]: https://jetpack.mozillalabs.com/
 [5]: http://discontents.com.au/shoebox/archives-shoebox/archives-in-3d