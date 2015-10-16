---
ID: 2638
post_title: The Perfect Face
author: Tim Sherratt
post_date: 2015-10-13 18:32:41
post_excerpt: ""
layout:
  - default
permalink: >
  http://discontents.com.au/the-perfect-face/
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
internet_archive:
  - ""
doi:
  - ""
github:
  - ""
builder_switch_frontend:
  - "0"
tmac_last_id:
  - ""
---
<em>Presented at the National Digital Forum, 13 October 2015, Wellington.</em>

<a href="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.010.jpg"><img class="aligncenter wp-image-2645 size-large" src="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.010-1024x576.jpg" alt="Detecting a basic face." width="1024" height="576" /></a>

<a href="https://www.23andme.com">23andMe</a> is a US-based company that will, for a fee, analyse your genetic ancestry. Provide some saliva and they'll send you a summary that compares your DNA with 31 identified populations across the world. It seems that this sort of genetic analysis is the next big thing in family history. You may have noticed that Ancestry offers a similar service.

23andMe, however, also provides an Application Programming Interface, or API, so developers can create third party apps that do cool things with your DNA. Don't worry -- you <em>do</em> have to provide permission. Facebook won't automatically start recommending friends based on your genes. Well... not yet.

But it didn't take long for the ethical boundaries of this sort of service to be tested. One developer created a <a href="https://github.com/offapi/rbac-23andme-oauth2">Genetic Access Control</a> authentication system. Using it, online sites or services could restrict access to people who had a specific genetic make-up.

The developer's API access <a href="http://www.wired.co.uk/news/archive/2015-07/22/23andme-api-blocks-based-on-race-gender">was quickly revoked</a> with 23andMe noting that their terms of use prohibit applications that 'contain, display or promote hate'.

&nbsp;

<hr />

&nbsp;

Four years ago I stood on this stage <a href="http://discontents.com.au/its-all-about-the-stuff-collections-interfaces-power-and-people/">describing a project</a> I was working on with <a href="http://chineseaustralia.org/about/">Kate Bagnall</a> called <a href="http://invisibleaustralians.org">Invisible Australians</a>. We were (and are) trying to encourage use of the National Archives of Australia's collection of records that document the workings of the White Australia Policy in confronting detail.

<a href="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.005.jpg"><img class="aligncenter wp-image-2641 size-large" src="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.005-1024x576.jpg" alt="Images of CEDTs from NAA: ST84/1, 1904/131-140" width="1024" height="576" /></a>

As an experiment I'd downloaded thousands of images from the Archives' collection database. Most were certificates used in the control of 'non-white' immigration -- visually compelling documents that include both portrait photographs and handprints.

I ran a facial detection script over the images to extract the portraits and created an online resource we called <a href="http://invisibleaustralians.org/faces/">The Real Face of White Australia</a>. For a weekend project it's had a significant impact around the digital humanities world.

Some people criticised us because they thought we were selecting records based on race. This was just a misunderstanding of the records and the technology we were using. Even if I'd wanted to, I wouldn't have had a clue back then about how to categorise portraits by race.

Now I do.

I can sign up for an account with a service like Face++ and use their API to analyse an image of a person's face to <a href="http://www.faceplusplus.com/tech_gender/">determine both race and gender</a>.

<a href="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.008.jpg"><img class="aligncenter wp-image-2642 size-large" src="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.008-1024x576.jpg" alt="An example of race detection using the Face++ demo" width="1024" height="576" /></a>

&nbsp;

<hr />

&nbsp;

After a bit of a break because of -- you know -- LIFE, Kate and I are getting back to Invisible Australians. In 2011 I had about 12,000 images from one series in the National Archives. I've now harvested almost 160,000 images from 22 series.

But the intervening years have also brought changes in the Australian government's treatment of asylum seekers, greater power for security agencies, and the normalisation of electronic surveillance.

When the White Australia Policy was implemented, portrait photographs and fingerprints were the latest in crime-fighting technology. Just over a month ago the <a href="http://www.ministerjustice.gov.au/Mediareleases/Pages/2015/ThirdQuarter/9-September-2015-New-$18-5-million-biometrics-tool-to-put-a-face-to-crime.aspx">Australian government announced</a> its 'newest national security weapon' -- a national facial recognition system to be known henceforth as 'The Capability'. This system would assist authorities in 'putting a name to the face of terror suspects, murderers, and armed robbers'.

Tools that help identify faces can offer powerful new means of discovery and analysis within the holdings of our cultural institutions. But can those of use who work with these tools avoid engaging with broader systems of surveillance, categorisation and control? For Kate and me the parallels are too strong -- history is not just about the past.

&nbsp;

<hr />

&nbsp;

I'm talking today about two related technologies -- facial detection and facial recognition.

Facial detection simply tells you if there's a face in an image. It's the technology that draws boxes around faces when you're taking photos and it's pretty efficient and well established. This is the technology I used to create our wall of faces.

Basic detection is now being supplemented by algorithms that examine the shape of facial features and the characteristics of things like skin to estimate gender, age and race. They can also tell you whether the person is wearing glasses and the quality of their smile.

<a href="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.011.jpg"><img class="aligncenter wp-image-2646 size-large" src="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.011-1024x576.jpg" alt="An 82.9% value smile according to the Face++ API demo" width="1024" height="576" /></a>

<a href="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.012.jpg"><img class="aligncenter wp-image-2647 size-large" src="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.012-1024x576.jpg" alt="An 1.87% value smile according to the Face++ API demo" width="1024" height="576" /></a>

Facial recognition, on the other hand, first detects faces within an image and then searches for those faces within an existing set of previously identified images. The Capability, for example, plans to take an image and look for matches across a series of interlinked databases, such as passports and driving licences. It's also what Facebook does when it tags people in photos you share.

Facial recognition is a lot trickier than detection, but last year <a href="https://research.facebook.com/publications/480567225376225/deepface-closing-the-gap-to-human-level-performance-in-face-verification/">FaceBook announced</a> that its DeepFace system had reached a level of accuracy similar to humans. Not to be outdone, Google claimed its FaceNet technology had pushed the bar even higher, reporting an accuracy of over 99%. How this translates to real-world applications such as The Capability is not clear, but we can assume that security agencies are heading down the same path.

&nbsp;

<hr />

&nbsp;

Machines have struggled to match humans in finding and recognising faces because faces are so important in simply being human. Faces connect us to our social world.

But, as cultural institutions know, faces can also connect us through time. Looking into the eyes of a person, no matter how far removed through history or culture, affects us. We do not merely read, we feel. This, I think, is where The Real Face of White Australia gains its emotional power.

Last year in another experiment I started extracting faces from Trove's millions of digitised newspaper articles. The images are of a much lower quality than photographs of course, but still... there's that feeling of connection.

<a href="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.014.jpg"><img class="aligncenter wp-image-2648 size-large" src="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.014-1024x576.jpg" alt="Samples of the faces extracted from Trove newspapers" width="1024" height="576" /></a>

Facial detection is one example of a broader class of computer vision operations known as feature detection. You can train your computer to find all manner of patterns and shapes in your images. This includes cats and bananas, as well the components of a face -- eyes, noses and mouths.

So of course I wondered, what would a newspaper discovery interface based on eyes look like?

<a href="http://eyespast.herokuapp.com/">Eyes on the past</a> has been variously described as both beautiful and creepy -- something of which I'm rather proud. It was another weekend project -- an experimental intervention rather than a practical tool. By clicking on eyes and faces you can find your way to newspaper articles, but that's not really the point.

I was hoping to say something about the fragility of our connections to the past -- we glimpse past lives through tiny cracks in the walls of time. These moments may be fleeting, but they can also be full of meaning.

So I kept harvesting faces. I've now got about 6000 from the 1880s through to 1913. If you'd like to play, the complete set is available for <a href="http://dx.doi.org/10.6084/m9.figshare.1461670">download from Figshare</a>.

I also built <a href="http://faceapi.herokuapp.com">my own face API</a> to encourage further experimentation. While services like Face++ have APIs that take your face and pull it apart, mine just gives you random faces from the past. That's all.

Most recently, I used my collection of faces to create a Twitter bot called the <a href="https://wragge.github.io/face-depot/">Vintage Face Depot</a>. Tweet a picture of yourself to the bot and it will send you back a new version of yourself, in which your face is overlaid with a random visage from my extensive range of vintage faces.

<a href="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.019.jpg"><img class="aligncenter wp-image-2649 size-large" src="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.019-1024x576.jpg" alt="Examples of the Vintage Face Depot's work" width="1024" height="576" /></a>

Tweaking the transparency means the faces start to blend -- you are neither yourself, nor them, but someone new. Each face replacement also comes gift wrapped with a link to the original newspaper article.

The Vintage Face Depot tells you nothing about yourself. I built it at about the same time as Microsoft launched their <a href="http://how-old.net">How-Old bot</a> that uses machine learning to estimate your age. Face Depot does nothing clever, and yet sometimes the results are uncanny, even unsettling. Microsoft might be able to tell you how old you are, but Face Depot asks <em>who</em> you are and pushes you in the direction of a past life, linked merely through chance.

Of course the next obvious step is to feed to the results of Vintage Face Depot to the How-Old bot.

<a href="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.020.jpg"><img class="aligncenter wp-image-2650 size-large" src="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.020-1024x576.jpg" alt="Results of feeding Vintage Face depot output to the How Old bot" width="1024" height="576" /></a>

Or to Face++'s API.

<a href="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.021.jpg"><img class="aligncenter wp-image-2651 size-large" src="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.021-1024x576.jpg" alt="Results of feeding Vintage Face Depot output to Face++ API" width="1024" height="576" /></a>

In a similar vein, the developer Kirk Kaiser has been <a href="https://github.com/burningion/deepgraffiti">pitting neural network against neural network</a> -- <a href="http://www.popsci.com.au/tech/computing/defeat-facebooks-deepface-with-googles-deepdream,407435">altering images of himself</a> using Google's DeepDream and uploading them to Facebook for DeepFace to analyse and tag.

Digital artists like Adam Harvey have reverse-engineered facial detection algorithms to devise <a href="http://cvdazzle.com">anti-surveillance fashion styles</a>. He shows how you can use make up to disrupt key regions, such as where your nose and eyes intersect, and render your face invisible. From face to 'anti-face'.

While none of these interventions provide a detailed critique of state surveillance, they do highlight the constructed nature of these technologies. By fucking with their parameters we understand better how they work.

But what's the role of cultural heritage organisations in all of this?

&nbsp;

<hr />

&nbsp;

Libraries are already <a href="https://libraryfreedomproject.org">leading the way</a> in supporting online privacy. But leaving aside the whole 'living in a surveillance state' thing for a moment, these technologies don't just find faces, they reduce us to a set of external characteristics. We become what they can measure.

Researchers are currently investigating how facial detection systems can be used to identify depression. The aims are worthy of course, but it's not hard to imagine how, like 23andMe, such systems could be used to discriminate rather than support. Other studies have explored whether human observers can tell if you're gay or prone to infidelity by looking at your face. Anyone remember phrenology?

With measurement comes the power to categorise and control. These are technologies that enable us to be judged at a distance -- to be identified as threat or a sales opportunity just by the way we look.

Facial recognition takes this further -- not only can we be reduced to a set of externally-verifiable measurements, but these measurements are assumed to constitute our identity.

Ok, so running Face++'s API across photographic collections to identify pictures of women seems like it could be a useful thing to do. But we also know that the male/female binary is hopelessly inadequate in describing who we are. Identifiers are not the same as identities.

Cultural heritage data is gloriously messy. Even as we try and wrangle it to fit our systems we recognise its resistance as something profoundly human. Against the power of surveillance -- both for security and sales -- we have the opportunity, the obligation, to celebrate this complexity. To deny the meaning of measurement.

You cannot know me from my face.

My identity cannot be captured in your database.

Let's use facial detection to enrich our metadata, but let's also work with artists, developers, and activists to challenge the technology's embedded assumptions about the 'perfect face'.

Four years ago I showed you our wall of faces. A few weeks ago I took those 7000 photos and ran them through a program that averaged the facial features.

I expected to be critical. I expected to be annoyed. But instead of seeing some algorithmically-generated nonsense, I just saw a person.

<a href="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.025.jpg"><img class="aligncenter wp-image-2652 size-large" src="http://discontents.com.au/wp-content/uploads/2015/10/perfect-face.025-1024x576.jpg" alt="Face created by averaging portraits in The Real Face of White Australia" width="1024" height="576" /></a>

There's power in that.