---
ID: 659
post_title: Cooliris-enabled scrapbook
author: Tim Sherratt
post_date: 2009-02-09 22:08:08
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/cooliris-enabled-scrapbook/
published: true
tmac_last_id:
  - "640027563591532544"
---
There's more 3D goodness for you to enjoy now that the [Mapping our Anzacs scrapbook][1] is Cooliris-enabled. If you have Cooliris installed, you'll notice that the Cooliris icon on your browser toolbar lights up when you visit the site. Just click on the icon to browse all the photos posted to the scrapbook on a glorious 3D wall. [caption id="attachment_660" align="aligncenter" width="300" caption="Scrapbook posts in 3D"][<img class="size-medium wp-image-660" title="moa-3d" src="http://discontents.com.au/wp-content/uploads/2009/02/moa-3d-300x187.jpg" alt="Scrapbook posts in 3D" width="300" height="187" />][2]\[/caption\] (If you don't have Cooliris then [go and get it][3]. It can be used both in Internet Explorer and Firefox, though you'll probably need to have admin rights to install for IE.) Having given the 3D treatment to [digitised files][4] from the National Archives of Australia and [portrait images][5] from the Australian Dictionary of Biography, it wasn't too hard to do. The scrapbook is a Tumblr site and the api makes it easy to extract all the photos. So I created a php file to gather all the details and then write them to a media-rss file. Then it was just a matter of  inserting a link to it in the scrapbook.<!--more--> Code follows: [code language="php"] 

<?php
if ($_GET['start']) {
$start = $_GET['start'];
} else {
$start = 0;
}
$url = "http://our-anzacs.tumblr.com/api/read?start=$start&num=50&type=photo&filter=text";
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_FAILONERROR, true);
curl_setopt($ch, CURLOPT_TIMEOUT, 20);
$result = curl_exec($ch);
if (!$result) {
echo "cURL error number:" .curl_errno($ch);
echo "cURL error:" . curl_error($ch);
exit;
}
curl_close($ch);
$dom = new DOMDocument();
@$dom->loadHTML($result); $xpath = new DOMXPath($dom); $attrs = $xpath->evaluate("//posts/@total[1]"); foreach ($attrs as $attr) { $total = $attr->nodeValue; } $num_pages = ceil($total/50); $start_next = $start+50; $start_previous = $start-50; echo "

<?xml version='1.0' encoding='utf-8' standalone='yes'?>n"; echo "<rss version='2.0' xmlns:media='http://search.yahoo.com/mrss/' xmlns:atom='http://www.w3.org/2005/Atom'>n"; echo "<channel>n"; echo "

<title>
  Mapping our Anzacs scrapbook
</title>n"; echo "<description>Photos posted to the Mapping our Anzacs scrapbook</description>n"; echo "

<link />
http://our-anzacs.tumblr.com</link>n"; if ($start_previous >= 0) { echo "<atom:link rel='previous' href='moa-media-rss.php?start=$start_previous' />"; } if ($start_next <= $total) { echo "<atom:link rel='next' href='moa-media-rss.php?start=$start_next' />"; } $posts = $xpath->evaluate("//post/@id"); foreach ($posts as $post) { $id = $post->nodeValue; $url = "http://our-anzacs.tumblr.com/post/$id"; $photos = $xpath->evaluate("//post[@id='$id']/photo-url[@max-width='500']/text()"); foreach ($photos as $photo) { $photo_500 = $photo->nodeValue; } $photos = $xpath->evaluate("//post[@id='$id']/photo-url[@max-width='250']/text()"); foreach ($photos as $photo) { $photo_250 = $photo->nodeValue; } $nodes = $xpath->evaluate("//post[@id='$id']/photo-caption/text()"); foreach ($nodes as $node) { $caption = $node->nodeValue; preg_match("/View details fors+([ws,-]*)/", $caption, $matches); $names = explode(", ", $matches[1]); $name = "$names[1] $names[0]"; } echo "<item>n"; echo "<guid isPermaLink='false'>$id</guid>n"; echo "
<title>
  $name
</title>n"; echo "

<link />
$url</link>n"; echo "<media:thumbnail url='$photo_250' />n"; echo "<media:content url='$photo_500' type='image/jpeg' />n"; echo "</item>n"; } echo "</channel>n"; echo "</rss>n"; ?> [/code]

 [1]: http://our-anzacs.tumblr.com
 [2]: http://discontents.com.au/wp-content/uploads/2009/02/moa-3d.jpg
 [3]: http://cooliris.com
 [4]: http://discontents.com.au/shoebox/archives-shoebox/archives-in-3d
 [5]: http://discontents.com.au/shed/experiments/cloudy-biographies-and-portrait-walls