---
ID: 2833
post_title: Caring about access
author: Tim Sherratt
post_date: 2016-11-12 11:08:13
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/caring-about-access/
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
<em>Contribution to a panel discussion on 'Access and Innovation' at Digital Directions 2016, Canberra, 10 November 2016. </em>
<em>View the <a href="https://wragge.github.io/digitaldirections/#/">slides</a>.</em>

Please cite as: Tim Sherratt, ‘Caring about access', presented at the Digital Directions, 2016. &lt;<a href="https://dx.doi.org/10.6084/m9.figshare.4229402.v1">https://dx.doi.org/10.6084/m9.figshare.4229402.v1</a>&gt;

<hr />

You might have seen that the Department of Prime Minister and Cabinet has opened discussion on an Open Government National Action Plan. Last week I was watching the Twitter stream from a briefing event in Melbourne, when I saw <a href="https://twitter.com/Asher_Wolf/status/793978773846659072">this tweet</a> from Asher Wolf quoting the PM&amp;C spokesperson:
<blockquote>. @pmc_gov_au: we don’t want ppl to search for flaws or try to crack gvt datasets. #OGPAU</blockquote>
Now I’m not sure of the context of this statement, but it is a reminder that we can’t take the meaning of words like ‘open’ or ‘access’ for granted.

They are what we make of them.

I’m a historian and hacker. I don’t steal credit card details, I use digital tools to open cultural heritage collections – to see them differently, to <em>feel</em> differently.

Earlier this year I wrote a script to harvest many gigabytes of parliamentary proceedings – Hansard – from the ParlInfo database maintained by the Department of Parliamentary Services. I <a href="https://github.com/wragge/hansard-xml">shared the files</a>, covering the period from 1901 to 1980, through my GitHub repository. My plan was simply to make this rich source of political history easily available to anyone who wanted to explore new forms of digital analysis.

In the end I created my own version of <a href="http://historichansard.net">Historic Hansard</a>, one that privileges the experience of reading rather than searching. I also added a few nifty features such as indexes of legislation and people, and integration with text analysis and annotation tools.

But in the process of harvesting the data I noticed that around <a href="https://timsherratt.org/research-notebook/notes/investigating-the-hansard-black-hole/">100 sitting days were missing</a> from ParlInfo. The files were empty – unable to be searched. Given an average of about 50 sitting days a year, that’s about two years worth that were simply invisible.

Thanks to the Parliamentary Library these problems have now been fixed. But this experience highlighted two issues. First, search interfaces lie. We have to develop our critical capacities to be more aware of what we are not being shown and why. And second, this problem only became visible because I was hacking their database, because I went beyond what was offered by their website, because I wanted more. Unlike the PM&amp;C spokesperson I think one of strongest reasons for opening data is to encourage people to find its flaws. This is particularly the case for cultural heritage data where the processes of selection, representation, normalisation, control, and preservation all have an impact of the types of stories we can tell about ourselves.

Access is not something that cultural institutions bestow on a grateful public. It’s a struggle for understanding and meaning. Expect to be criticised, expect problems to be found, expect your prejudices to be exposed. That’s the point.

If cultural institutions want to celebrate their website hits, celebrity visits, or their latest glossy magazines – well that’s just fabulous. But I’d like them to celebrate every flaw that’s found in their data, every gap identified in their collection – that’s engagement, that’s access. We need to get beyond defensive posturing and embrace the risky, exciting possibilities that come from critical engagement with collection data – recognising hacking as a way of knowing.

In this new post-truth world it’s going to be more important than ever to challenge what is given, what is ‘natural’, what is ‘inevitable’. Our cultural heritage will be a crucially important resource to be mobilised in defence of complexity, nuance, and doubt – the rich and glorious reality of simply being human.

A few years ago Merete Sanderhoff, from the National Gallery of Denmark, compiled a collection of essays on opening cultural heritage collections for reuse online. It was called <a href="http://www.sharingiscaring.smk.dk/en/about-smk/smks-publications/sharing-is-caring/"><em>Sharing is Caring</em></a>. I think it’s worth reflecting on the dual meanings of ‘caring’ – both looking after, and giving a shit. Sharing helps us foster communities and preserve collections. But it also <em>matters</em>, it has an impact, it can change the world.

Bethany Nowviskie, the Director of the Digital Library Federation, recently gave a talk on <a href="http://nowviskie.org/2016/speculative-collections/">‘speculative collections’</a> asking how we shift the temporal orientation of our libraries and archives away from a closed and linear past towards an exploration of what might be.

Seeing differently. Feeling differently.

This is a visualisation created by Geoff Hinchcliffe <a href="http://gravitron.com.au/fundtrove/">showing more than 12,000 tweets</a> since February this year using the hashtag #fundTrove. Trove has radically changed our access to the past. It’s not perfect, it’s not everything, but it changes lives. And yet the government seems to think it can be left to wither, and nobody will really care. I care. Do you? Then what do we do about it?

I also care deeply about the collections of the National Archives – a love expressed through many painful hours spent hacking RecordSearch, their online database. Last year I harvested details of more than 12,000 publicly available ASIO files – you can grab the results from my <a href="https://github.com/wragge/asio-files">GitHub site</a> – and downloaded about 300,000 page images. These are mostly surveillance files, documenting the lives of writers, academics, unionists, Indigenous activists and others – identified as potential threats to the nation.

This year I wrote a script to search those images for redactions – sections of text blacked out for security reasons. If you’d like to explore the 239,000 redactions I’ve extracted, <a href="http://owebrowse.herokuapp.com/redactions/">you can</a> – marvel at their blackness, their very lack of information. But here the redactions are not dead ends, they’re starting points, ways of exploring the workings of ASIO. As the power and reach of state surveillance continues to expand, we can find creative ways to reverse the panoptic gaze.

We don’t have to accept what we’re given. We can take collections and <a href="http://discontents.com.au/turning-the-inside-out/">turn them inside out</a>.

The National Archives also preserves remnants of Australia’s racist past. There are many thousands of records documenting the workings of the White Australia Policy. They include special certificates, with portrait photos and handprints, which were needed if you were deemed non-white, travelled overseas, and simply wanted to come home.

About five years ago I harvested about 12,000 images of these certificates from RecordSearch and ran them through a facial detection script. In a little over a weekend I’d created the <a href="http://invisibleaustralians.org/faces/">Real Face of White Australia</a> – a seemingly endless scrolling wall of more than 7,000 faces. It’s compelling. It’s uncomfortable. But this is who we are.

As I saw the One Nation senators cracking open the champagne outside Parliament House yesterday, I thought again of how important its is the tell these stories, to share these collections. To give a shit.

Innovation can be measured in more than shiny apps, or cool new visualisations. By struggling with access to our past we can imagine new futures.