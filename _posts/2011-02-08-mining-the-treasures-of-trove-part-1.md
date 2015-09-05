---
ID: 1088
post_title: Mining the treasures of Trove (part 1)
author: Tim Sherratt
post_date: 2011-02-08 01:07:10
post_excerpt: ""
layout: post
permalink: >
  http://discontents.com.au/mining-the-treasures-of-trove-part-1/
published: true
tmac_last_id:
  - "640027547279855616"
---
Some time ago a well-meaning optometrist told me I had the eyes of a 60 year-old. I lay the blame for this premature ocular degeneration upon the many tiring hours I spent squinting at the screens of dodgy microfilm readers. Newspapers were a major source of my [PhD research][1], and back then that meant learning a little too much about films, spools and lenses. Not to mention the unending struggle to capture and hold the best machines. Now it's different. Instead of spending some weeks, as I did, sampling the *Australian Womens Weekly* in the hope of finding relevant articles, I can go to the National Library's [Australian Newspapers][2] database in Trove and do a [keyword search][3]. Easy. The eyesight of future historians is safe. But ready access to millions of newspaper articles across 150 years brings new challenges. Used to coaxing evidence from a meager array of sources, historians now, as [Dan Cohen notes][4], have to 'grapple with abundance'. How do we use and understand our new documentary riches? Fortunately there are a growing array of tools to help. [Zotero][5] helps us manage our sources. [Voyeur Tools][6] brings sophisticated text analysis techniques within the grasp of all. And where the tools we need do not exist, [we can make them][7]. So that's what I did. I'm interested in the way we [talk about the weather][8]. Wouldn't it be good, I was thinking a few weeks back, if I could harvest the content of newspaper articles about weather or climate and start to analyse it -- looking for patterns and shifts, mapping correlations or divergences against the actual climatic record. Well... why not? There's [currently no API][9] that allows you to access Trove in this way, though one is apparently under development. But being the impatient sod that I am, I'd already built most of the parts I needed. Some time ago I [wrote a screen scraper][10] to query the newspaper database and extract article details from the returned HTML. This scraper is used in the [History Wall][11] to display random newspaper articles. It's also sitting behind my little [Headline Roulette][12] game. I've been continuing to improve and refine the scraper and recently used it to create my own API to Trove hosted on Google's AppEngine. I'll be posting some more details about this soon. And yes, I also developed a [Zotero translator][13] for the newspapers site, which I promise to finish off! So to make a harvester, all I needed to do was run my scraper over all the results in a search and save them in some useful form. It took me less than an hour to develop a working prototype. Since then I've been adding a few bells and whistles... The other night I harvested about 1400 articles that included the phrase climate change. The harvester had saved the text content of the articles in a zip file, so I uploaded it to [Voyeur Tools][6]. Here's a simple word cloud: <p style="text-align: center;">
  <a href="http://voyeurtools.org/tool/Cirrus/?corpus=trove-climage-change&stopList=stop.en.taporware.txt"><img class="aligncenter size-medium wp-image-1092" title="climate-change-cloud" src="http://discontents.com.au/wp-content/uploads/2011/02/climate-change-cloud-300x143.png" alt="" width="300" height="143" /></a> (<a href="http://voyeurtools.org/?corpus=trove-climage-change&stopList=stop.en.taporware.txt">corpus</a>)
</p> Or what about the 'atomic age' seen through major Australian newspapers in 1945-46? 

<p style="text-align: center;">
  <a href="http://voyeurtools.org/tool/Cirrus/?corpus=1297051644653.4125&stopList=stop.en.taporware.txt"><img class="aligncenter size-medium wp-image-1131" title="atomic_age" src="http://discontents.com.au/wp-content/uploads/2011/02/atomic_age-300x147.png" alt="" width="300" height="147" /></a>(<a href="http://voyeurtools.org/tool/CorpusSummary/?corpus=1297051644653.4125">corpus</a>)
</p> Hmmm, this is fun... 

## It's harvest time But all you really want to know is how to do it, right? So after that overlong introduction, here's everything you need to know. 

#### What does the harvester do? You feed the harvester the url of a search you've constructed in Trove. The harvester then loops through all the results pages, extracting the article details. These details are saved in a CSV (comma separated values) file that you should be able to open as a spreadsheet or import into a database. The fields in the CSV file currently are: 

*   article id
*   article title
*   article url
*   newspaper
*   newspaper life dates and location
*   newspaper id
*   issue date
*   page reference
*   page url
*   number of user corrections to the OCR output
*   text of the article (including paragraph breaks) In addition to the CSV file, the harvester can create two other data files for you. The first is a zip file that contains the text of all the articles, organised by newspaper and article. The internal structure of the zip is something like this: 

<pre>[newspaper1 id]-[newspaper1 title]/
     [article1 id]-[article 1 issue date]-p[article1 page reference].txt
     [article2 id]-[article 2 issue date]-p[article2 page reference].txt
[newspaper2 id]-[newspaper2 title]/
     [article3 id]-[article 3 issue date]-p[article3 page reference].txt
     [article4 id]-[article 4 issue date]-p[article4 page reference].txt</pre> For example: 

<pre>35-The-Sydney-Morning-Herald/
     29765619-Friday-24-May-1946-p5.txt
     29763575-Friday-10-May-1946-p2.txt</pre> Why is this useful? Once you have the texts organised in this format you can start feeding them to text-analysis programs. 

[Voyeur Tools][14] makes it easy, but there are other options like [Mallet][15] or [NLTK][16]. (Read about [my first attempts at using NLTK][17] over at NMA Labs.) As well as simple word frequencies and collocations you might want to investigate the possibilities of entity extraction, topic modelling or sentiment analysis. The harvester also gives you the option of downloading a PDF version of every article. These are also saved in a zip file for convenience, with the same structure as above. Of course, if you're harvesting a large number of articles this zip file might get *very* big. 
#### Quick start (for the impatient) If you just want to dive straight in here's what you need to do: 

1.  If you don't have it already, [install Python][18] (v.2.7 is recommended, but other versions should work ok)
2.  Download my [Trove Newspapers code][19]
3.  Unzip the TroveNewspapers file and put the contents somewhere handy.
4.  Navigate to the trovenewspapers/bin directory.
5.  Open the file 'harvest.ini' with a text editor (Notepad will do).
6.  Change the default settings of 'harvest.ini' as instructed.
7.  Save 'harvest.ini'.
8.  Find and run 'do_harvest.py'.
9.  Sit back and watch as your harvest chugs away.

#### The boring details (for the cautious)

##### Install Python My scraper and harvester are written in Python, so you'll need to have it installed on your system. If you're working in Linux you should already have it. 

[Downloads are available][18] for all other platforms. For example, if you're in Windows just download and run the [Windows x86 MSI Installer][20]. 
##### Download my code Now download 

[my Trove Newspapers code][19]. It's avaiable as a zip file, so unzip it and put the contents somewhere you can find it again. The contents look something like this: 
<pre>trovenewspapers/
     data/
     harvests/
     __init.py__
     harvest.py
     retrieve.py
     utilities.py
     LICENSE.txt</pre>

<del datetime="2012-01-24T06:17:19+00:00">We'll talk about the bin directory shortly.</del> The data directory contains information about the newspaper holdings available through Trove. This is used by the scraper. If you ever want to update this data, you can use the save_titles function in utilities.py, but it's not important for the harvester. The harvests directory is empty, but if you start a harvest without specifying an output location, this is where it'll end up. [BeautifulSoup][21] is an extremely useful Python library for screen scraping. The scraper relies heavily on it, so I've included a copy in the package for your convenience. The two files that do all the work are harvest.py and retrieve.py. Open them up in an editor and have a look if you're interested. The scraper logic is all in retrieve.py, while harvest.py builds and runs the harvester. But if all you want to do is start harvesting you can ignore all this and head straight to the <del datetime="2012-01-24T06:17:19+00:00">bin</del> top-level directory. Here you'll find two files, do_harvest.py and harvest.ini. You'll also find a README file which contains another version of these instructions and some added documentation. 
##### Set your harvest options Open up harvest.ini in any old text editor. You'll see it contains some instructions and a series of configuration options with default values. If you run a harvest with out changing the defaults you'll generate a fascinating set of 28 articles that contain the phrase 'Inclement Wragge'. The options you can set are: 

1.  query -- the url of your Trove search
2.  filename -- where you want to save the CSV file
3.  include-text -- do you want to save the texts in a zip file (yes or no)?
4.  include-pdf -- do you want to save pdfs of the articles in a zip file (yes or no)?
5.  start -- the result number to start at (leave at 0 for a new harvest) At this point you need to think -- what do I actually want to harvest? Head over to the 

[advanced search page][22] for the newspapers database and start playing with the options until you get the results you want. Try to be as precise as possible -- you don't want to download lots of irrelevant articles. Once you're happy with your search, just copy the url in your browser's location box. This url contains all the search parameters the harvester needs to find and process your results. Just paste the complete url into harvest.ini next to the 'query' option. Set the filename option to tell the harvester where to save your CSV file. The harvester will use the filename you supply to build the filenames for the zip files (if you want them). If you don't include a path the files will be saved in the bin directory. If you don't set a filename, the harvester will create a default name -- trove-newspapers-[timestamp].csv. The 'include-text' and 'include-pdf' options should be pretty obvious. Set them to 'yes' if you want to save texts and pdfs, or 'no' if you don't. The 'start' option allows you to start your harvest at someplace other than the beginning of your results set. This is useful if your harvest is interrupted for any reason (more below). Just set it to the result number you want to start at. Once your options are set, just save harvest.ini. It's launch time! 
##### Start your harvest Remember the do_harvest.py file? It contains a little script that reads your configuration settings in harvest.ini and sends them off to the harvester. So to get things going all you need to do is run do_harvest.py. How you actually do this depends a bit on your operating system and its settings. If you're on Windows, then the python installation program should have told the OS to treat any file with a .py extension as a Python script. So you should just be able to double click it. On Linux, the easiest way is to open up a terminal, cd to the bin directory and type 'python do_harvest.py'. That should be it. The script will let you know what's going on, listing the articles as it processes them. Enjoy! 

##### For lovers of the command line The do_harvest script can also be run from the command line, with the various options supplied as arguments: 

*   -q (or --query) [full url of Trove newspapers search].
*   -f (or --filename) [file and path name for the CSV output].
*   -t (or --text) Create a zip file containing the text of articles.
*   -p (or --pdf) Create a zip file containing pdfs of articles.
*   -s (or --start) The result number to start at. For example: 

`
python do_harvest.py -q http://trove.nla.gov.au/newspaper/result?exactPhrase=inclement+wragge -f /home/wragge/trove-output.csv -t -p
` Command line arguments will override any of the settings in harvest.ini. If you're using Windows you'll need to make sure that the location of your Python installation is included in your Windows path variable. 
##### If something goes wrong If there are problems at the Trove end, the harvester will take a little 10 second nap before trying again. It'll do this 10 times before it finally gives up. Just before it dies, the script will write some details out to an error file ([your filename]\_error.txt), including some instructions on what to do next. This error file will include the number of the last completed record. Simply insert this as the 'start' value in harvest.ini (or include on the command line with the -s flag) and run do\_harvest.py again. The harvester will spring back into life. You'll probably have a duplicate row in your CSV file at the point where the harvest failed, but that's easy to delete. 

### What's next? Please have a go and let me know how you fare. You can add comments here, or raise issues over at 

[my Bitbucket repository][23]. I'm thinking about building a little GUI version if there's enough interest, and I have a few other improvements in mind. I'll be posting more about my adventures hacking Trove, and also about my efforts to analyse the results of my harvests (hence the part 1).

 [1]: http://discontents.com.au/shoebox/history-of-australian-science/atomic-wonderland
 [2]: http://trove.nla.gov.au/newspaper
 [3]: http://trove.nla.gov.au/newspaper/result?q=&exactPhrase=atomic+age&anyWords=&notWords=&l-textSearchScope=*ignore*|*ignore*&fromdd=&frommm=&fromyyyy=&todd=&tomm=&toyyyy=&l-title=|112&l-word=*ignore*|*ignore*&sortby=
 [4]: http://www.journalofamericanhistory.org/issues/952/interchange/index.html
 [5]: http://www.zotero.org/
 [6]: http://voyeurtools.org/
 [7]: http://niche-canada.org/programming-historian
 [8]: http://discontents.com.au/sections/shoebox/weather-research-topics
 [9]: http://trove.nla.gov.au/forum/showthread.php?81-New-section-suggestion-Hacking-Trove
 [10]: http://discontents.com.au/shed/experiments/headline-roulette
 [11]: http://labs.nma.gov.au/wall/
 [12]: http://wraggelabs.com/newsroulette/
 [13]: http://trove.nla.gov.au/forum/showthread.php?76-Zotero-translator-for-Australian-Newspapers-beta-version-for-testing
 [14]: http://voyeurtools.org
 [15]: http://mallet.cs.umass.edu/
 [16]: http://www.nltk.org/
 [17]: http://labs.nma.gov.au/blog/2010/12/word-frequencies/
 [18]: http://www.python.org/download/releases/2.7.1/
 [19]: https://github.com/wragge/Trove-newspapers
 [20]: http://www.python.org/ftp/python/2.7.1/python-2.7.1.msi
 [21]: http://www.crummy.com/software/BeautifulSoup/
 [22]: http://trove.nla.gov.au/ndp/del/search?adv=y
 [23]: https://bitbucket.org/wragge/trove-tools