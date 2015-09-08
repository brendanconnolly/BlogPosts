I first heard of Weekend Testing several years ago, I meant to get involved then but just never made the time. Enter the [CAST 2015](https://www.youtube.com/playlist?list=PLQB4l9iafcel0y8h5HrfChOg4HxjLOX31) live stream and the [keynote](http://youtu.be/vOfjkkblFoA) by
[Ajay Balamurugadas](http://enjoytesting.blogspot.com/) where there was a call to action to engage and contribute to the community. I hadn't realized there was such a strong community of testers, and I wanted to be a part of it. I wanted to learn and grow, and a community of testers sounded so exciting.

The topic for the session was [Mobile Test Design for Non-Functional Tests](http://weekendtesting.com/?p=4156). If I wasn't excited before the topic sounded great. I work on a small team, and we do not have any mobile applications. I wouldn't have any real opportunity for directed hands on testing without something like Weekend Testing. 

It was with a mix of excitement and nervousness that I joined the skype session...  

After introductions we began with:
### What do you notice thats different when app is mobile that a Tester would care about

On my iphone 5 the first thing I was confronted with when launching the app was a prompt asking for access to my location at all times even when the app was not running. I am sure there is a function the app claims to provide that justifies this need but it felt invasive and like a thinly veiled attempt to gather data from users to be sold. This made me consider both privacy issues in the mobile space and the value add an app needs to present to make a user willing to trade some of their personal data for the benefits the app provides. 

As the testing group continued to discuss the app we found that the app wanted users to create an account and sign in. It was perplexing, why would a weather app need users to create an account? What additional benefits could there really be? It made me consider the importance of convenience. For general purpose apps ease of use and convience factors must at a minimum match the value a user expects to gain from it. Its an inverse relationship, the more trivial the domain is percieved to be the less frustration a user is willing to accept before they either quit the app or remove it to try another. 
     
This lead into a useability discussion which was framed nicely by [Jean Ann](https://twitter.com/JA_Harrison) 
### Easy to Use, Easy to Learn, Matches Expectations
Basic functionaity in the app was fairly intuitive. You could add locations and get the cirrent weather. Although, the icon for adding a location to monitor weather was a small "+" at the top right corner of the screen. It was also very close to the icon for joining the apps rewards club. I'm not sure what rewards a weather app would offer, but it did seem intentionally close to the add location icon/ It felt like it was there to increase the likelihood of a user pressing it. However, the more the group explored the more we found localization issues. 

Some features such a location identifaction by zip or postal code only worked for locations in the United States. Postal codes are not unique to the United States, and there was no messaging to indicate this restriction. Many of the deeper weather statistics and information such as airport conditions or pollen index were also United States only. While the app offered displaying the temperature and measurements in multiple units, the app seemed constrained in international locations. I struggled to identify the target audience of the app. It provided so much data it could easily over power an average user, so it seemed to target power users or travelers but theat would imply better international support. There were no filtering options to limit what was displayed and the weather data was intermixed with ads. This portion of the session was a bit of a struggle in the skype discussion. It was very easy to get caught up in the excitement of sharing ideas and issues we were seeing. Messages were flying, it was valueable discussion but we did drift into a bit of a mini bug hunt. 

###And then there were Ads
I hadn't considered ad's as testing issue before. I guess my first thoughts are to functional requirements of software. This really highlighted a major benefit of Weekend Testing, collaboration. Its great to share an idea then have other testers help you clarify your thoughts and observations. I made a comment that I thought the ratio of ad space to content space was an issue. Jean Ann follwed my comment with validation that it was a good insight. As a tester I've seen various types of responses to product observations and suggestions. It felt great to have peers I've never met before be supportive. 

### Impact on Device
The session required testers to have the batteries on their devices at about 15% when we began. This highlighted another thing I had not really questioned when considering testing mobile apps, app driven battery drain. It may seem like a common concern but I think meaningful insight came out of it. The concept of the hardware being a state for the app to consider was very interesting to me. I also hadn't considered cumulative state, such as device under heavy load generating heat, then placing the unit on the charger while still using the device. Testing the overlaps in device state seem like fertile grounds for a tester. 

We discussed if it was in scope for an app to consider the current remaining charge or heat level and adjust its behavior. I got a little hung up on the idea that this was a OS level concern but on further reflection, I think there is more to it. I still believe that mobile platforms need to mature and that the complexity of mobile testing and its concern with device specific behaviors is a symptom of the immaturity of the mobile space. However, I see that does not change the current state of mobile testing, and that native applications still need to tests to ensure they are handling OS level messaging and not causing adverse effects.

### Comparison and Evaluation
We were concerned with the amount of data the app was consuming and its affect on the devices battery. I thought it would be worthwhile to have a "control" app (like the built-in weather app in IOS) to benchmark against the Weather Channel app. [Michael Bolton](http://www.developsense.com/) followed up with a clarification that I think offered a higher value. 
> Instead of thinking "benchmarking", you might like to think more generally:  choosing a comparable product to evaluate various functions, features, and quality > attributes
This process would provide more meaningful insight into how the application under test stacks up to its competition. THe benchmarking I suggested would take similar time but offer only a portion of the insight. I also appreciate choosing better words to describe our activities as testers. The more effectively we can discuss and convey our ideas, the easier it is to ascribe value to them. 

### We're Testing Relationships
Michael also offered another nice quoteable that I think summarizes the goal of our session particularly well: 
>We're not "testing the software".  We're testing relationships between software, hardware, people, and the interactions between all of those things.
>I've filed that one away in my mind, I think it frames testing well and reminds me not to get caught up in purely functional testing.

### Take Aways 
It may seem like I've been name dropping a bit, and I was. I wanted to try and give credit but I also wanted to highlight the fact that Weekend Testing offers you an opportunity to work with some big names in the community. I heard over and over again in the CAST discussions about how welcoming the community is. I wasn't sure how true that was until this session. No one makes you feel small or silly and plain and simple its energizing, to work with passionate people.
 
One of the hardest parts of this testing session, was the sheer volume of information that the app presents the user with. Ideas were flying, but it could get hard to keep up with the flurry of messages over Skype. Its also a relatively short 2 hour session. I think its a good length of time, longer would only make it harder for people to commit to, but once we all got going time went so fast. I felt like I was just getting into the groove then we had to start wrapping up. I think I got a taste of what can make a good conference or workshop so exciting. 

Overall, it was a great experience and opportunity. You get a chance to test drive ideas, or experiment in domains or technologies that your current position may not allow you to. I know I'll be back, I hope if you've stuck with me this far that I'll see you at a session too.
