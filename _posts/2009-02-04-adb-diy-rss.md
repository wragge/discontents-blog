---
ID: 653
post_title: ADB DIY RSS
author: Tim Sherratt
post_date: 2009-02-04 16:34:24
post_excerpt: ""
layout: post
permalink: http://discontents.com.au/adb-diy-rss/
published: true
tmac_last_id:
  - "640027563591532544"
---
So I was thinking, wouldn't it be nice if the <em>Australian Dictionary of Biography</em>'s '<a href="http://www.adb.online.anu.edu.au/scripts/adbp-births-deaths.php">born on this day</a>' feature could be made available as an RSS feed. Every morning you'd get a new list of biographies delivered direct to your feed reader. And so...

[sounds of xpath wrangling and PHP coding]

<a href="http://discontents.com.au/shed/adb/born-rss.php">here it is</a>.

It's pretty simple – it harvests all the links of people born on the current day, then loops through the links to gather the first paragraph of each biography. Then it's just a matter of writing everything to an RSS file.<!--more-->

In case you missed it, I also created a <a href="http://discontents.com.au/shed/adb/portraits/adb-portraits-1.rss">Media RSS feed</a> for portrait images used in the ADB. This enables them to be <a href="http://discontents.com.au/shed/adb/portraits/adb-portrait-browser.html">viewed in CoolIris</a>.

Code follows...
<pre>[code language="php"]
<?php
function getPage($url, $ch) {
	curl_setopt($ch, CURLOPT_URL,$url);
	$html= curl_exec($ch);
	if (!$html) {
		echo "cURL error number:" .curl_errno($ch);
		echo "cURL error:" . curl_error($ch);
		exit;
	}
	return $html;
}
$url = "http://www.adb.online.anu.edu.au/scripts/adbp-births-deaths.php";
$userAgent = 'Googlebot/2.1 (http://www.googlebot.com/bot.html)';

$ch = curl_init();
curl_setopt($ch, CURLOPT_USERAGENT, $userAgent);
curl_setopt($ch, CURLOPT_FAILONERROR, true);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);
curl_setopt($ch, CURLOPT_AUTOREFERER, true);
curl_setopt($ch, CURLOPT_RETURNTRANSFER,true);
curl_setopt($ch, CURLOPT_TIMEOUT, 10);
$html = getPage($url, $ch);

$dom = new DOMDocument();
@$dom->loadHTML($html);

$xpath = new DOMXPath($dom);
$hrefs = $xpath->evaluate("//ul[@class='pb-results'][1]/li/a");
$titles = $xpath->evaluate("//ul[@class='pb-results'][1]/li/a/text()");

echo "<?xml version='1.0'?>n";
echo "<rss version='2.0'>n";
echo "<channel>n";
echo "<title>ADB Online - Born on this day</title>n";
echo "<link>http://www.adb.online.anu.edu.au/scripts/adbp-births-deaths.php</link>n";
echo "<description>A list of all those people in the Australian Dictionary of Biography who were born on this day.</description>n";
for ($i = 0; $i < $hrefs->length; $i++) {
	$href = $hrefs->item($i);
	$title = $href->nodeValue;
	$bio = "";
	$url = "http://www.adb.online.anu.edu.au" . substr($href->getAttribute('href'),2);
	$html = getPage($url, $ch);
	$dom = new DOMDocument();
	@$dom->loadHTML($html);
	$xpath = new DOMXPath($dom);
	$paras = $xpath->evaluate("//div[@id='content']/p[1]/text()");
	foreach ($paras as $para) {
		$bio .= $para->nodeValue;
	}
	$bio .= "...";
	$bio = htmlspecialchars($bio, ENT_QUOTES);
	$bio = str_replace('n', '', $bio);
	echo "<item>n";
	echo "<title>$title</title>n";
	echo "<link>$url</link>n";
	echo "<description>$bio</description>n";
	echo "</item>n";
}
echo "</channel>n";
?>
[/code]</pre>