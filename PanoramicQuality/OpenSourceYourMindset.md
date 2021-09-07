![dev getting lightbulb](http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-lightbulb.png)

*This post originally appeared on TestingInDevops.org, unfortunately the Mabl team has decided to no longer continue to support that site. Rather than lose the content, I re-post it here for your reading enjoyment.*

---

As development has shifted from waterfall to agile and now DevOps, at each stage you see developers taking on more responsibility and accountability.

**Waterfall** was isolationist, building silos around different groups in software development. Developers owned the act of coding and in the stereotypical developer way, had little to no interest what happened before or after they coded. Other roles on teams in many ways acted as insulators to keep external forces away from developers.

**Agile** was developers pulling that insulation away, shifting themselves left and taking more ownership of the product creation process. Developers found they required a real time feedback loop to build the right things and successfully react to change.

**DevOps** is essentially the same process on the right side of the spectrum. Development takes more ownership of deployment, monitoring and supporting the applications health. It&#8217;s just too slow and cumbersome to react to the requirements of maintaining applications by filtering feedback through separate teams at scale.

The benefits of integration outweigh the cost of the additional responsibility.

<h2>Code Continuous</h2>

To cope with the additional responsibilities, developers have turned to their trusty friend <em>code</em>.

With agile we see rise of tooling developed for <em>Continuous Integration</em> to alleviate the pain and reduce the risk in iterative development.

<div class="wp-block-image"><figure class="alignright is-resized"><img  data-permalink="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-ring.jpg" data-orig-file="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-ring.jpg" data-orig-size="1280,1214" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;CanoScan 9000F Mark II&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="ring-2399855_1280" data-image-description data-medium-file="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-ring.jpg" data-large-file="https://web.archive.org/web/20190609162441/https://i2.wp.com/testingindevops.org/wp-content/uploads/2019/05/ring-2399855_1280.jpg?fit=840%2C797&amp;ssl=1" src="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-ring.jpg" alt="mobius loop" class="wp-image-242 jetpack-lazy-image" width="163" height="155" /></noscript></figure></div>

In DevOps we see the rise of code and tools supporting <em>Continuous Deployment</em>. Even when many teams already had product installers, or automated deployments what was missing was the integration of that information.

If developers are owning more of the product as well as release and deployments,then testing naturally gets swept up in the process. In fact we see this pattern emerging with the concept of <em>Continuous Testing</em>. Code is being written, tools created to help solve the issue of integrating test execution and reporting into teams release pipeline. The feedback loop is extended to provide rapid information to make it easier and faster for development to be responsive to change.

<h2>Continuous Testing</h2>

Automated testing is a loaded term. In developer circles it almost exclusively means unit and possibly integration tests. In QA it almost almost exclusively means end to end (e2e) tests, and is often synonymous with <em>Selenium</em>.

On teams where both sets of tests exist, their worlds may seldom interact. Developers may be aware of the <em>e2e</em> tests but they probably aren&#8217;t writing them and even less likely running them.

<div class="wp-block-image"><figure class="alignleft is-resized"><img  data-orig-file="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-ContinuousTesting.jpg" data-orig-size="1640,1000" data-image-title="ContinuousTesting" data-image-description data-medium-file="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-ContinuousTesting.jpg"  src="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-ContinuousTesting.jpg" alt="Illustration from “Continuous testing in DevOps”, Dan Ashby, https://danashby.co.uk/2016/10/19/continuous-testing-in-devops/" class="wp-image-243 jetpack-lazy-image" width="315" height="191" ><noscript><img data-attachment-id="243" data-permalink="https://web.archive.org/web/20190609162441/https://testingindevops.org/open-sourcing-your-mindset-by-brendan-connolly/continuoustesting/" data-orig-file="https://web.archive.org/web/20190609162441/https://i0.wp.com/testingindevops.org/wp-content/uploads/2019/05/ContinuousTesting.jpg?fit=1640%2C1000&amp;ssl=1" data-orig-size="1640,1000" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;Ashby,Dan&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;1476396107&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="ContinuousTesting" data-image-description="" data-medium-file="https://web.archive.org/web/20190609162441/https://i0.wp.com/testingindevops.org/wp-content/uploads/2019/05/ContinuousTesting.jpg?fit=300%2C183&amp;ssl=1" data-large-file="https://web.archive.org/web/20190609162441/https://i0.wp.com/testingindevops.org/wp-content/uploads/2019/05/ContinuousTesting.jpg?fit=840%2C512&amp;ssl=1" src="https://web.archive.org/web/20190609162441im_/https://i0.wp.com/testingindevops.org/wp-content/uploads/2019/05/ContinuousTesting.jpg?fit=840%2C512&amp;ssl=1" alt="Illustration from “Continuous testing in DevOps”, Dan Ashby, https://danashby.co.uk/2016/10/19/continuous-testing-in-devops/" class="wp-image-243" width="315" height="191"/></noscript><figcaption><em>Illustration from&nbsp;“Continuous testing in DevOps”, Dan Ashby,&nbsp;<a href="https://web.archive.org/web/20190609162441/https://danashby.co.uk/2016/10/19/continuous-testing-in-devops/">https://danashby.co.uk/2016/10/19/continuous-testing-in-devops/</a></em></figcaption></figure></div>

Continuous Testing has nothing to do with the testing that most QA team members are most familiar with, exploratory testing. The purpose of the code and tooling that comprises a pipeline isn&#8217;t for there to be some manual intervention required part of the way through it. Putting exploratory testing somewhere in the later stages for the pipeline is akin to pointing a fire hose at someone and asking them to direct the flow to the next stage.

If the <a href="https://web.archive.org/web/20190609162441/https://www.brendanconnolly.net/quality-at-the-speed-of-devops/">speed of DevOps</a> wasn&#8217;t enough, the presence of <em>continuous testing</em> only puts more pressure on testers, simply because more attention is being drawn to testing.

Automation engineers and product engineers are being drawn closer together. The importance and relevance of end to end automated tests is becoming more of a reality for product developers as they become run regularly as a post deploy verification tests.

While code is being thrown at testing with newfound passion, exploratory testers need to be prepared for their time in the spotlight. If automated tests are running all the time what tests are you doing? What makes them special? Why are they required before we can deploy?

<h2>What do you do different than Selenium?</h2>

Before you dismiss that question, pause and consider what all selenium and the tests it drives truly provide.

Selenium is cross browser, scalable, schedulable, repeatable, and can provide logs and screenshots of its tests. Can you compete with that?

Flaky,slow, and wrong sometimes, you say? And you and all other humans aren&#8217;t?

Conversations that try to explain using people instead of machines for testing software can end up justifying them under the guise of <em>there are some tests that aren&#8217;t good candidates for automation</em>.

<h3>Don&#8217;t settle for executing tests that don&#8217;t have enough ROI
to automate.</h3>

This type of conversation relies on the belief that testing is comprised to two elements: <em>test case creation</em> and <em>test execution</em>. Perhaps at its most base level testing is just that, the value proposition of the role is in the nuance that a skilled tester can provide to teams through those elements.

Testers do more than a fill a gap in automated test coverage. The problem is many testers express this nuance solely through actions.

Developers produce code, a measurable artifact from their effort. The generation of that artifact is often backed by computer science, a formalized area of study. Artifacts of effort are reassuring, people like to see the fruits of their labors. Tangible results can be measured and quantified, they might even help estimate future effort.

<div class="wp-block-image"><figure class="alignright is-resized"><img data-permalink="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-Joan_of_Arc_on_horseback.png" data-orig-file="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-Joan_of_Arc_on_horseback.png" data-orig-size="1638,2082"  data-image-title="Joan_of_Arc_on_horseback" src="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-Joan_of_Arc_on_horseback.png" alt="Joan of Arc" ><figcaption>Joan of Arc</figcaption></figure></div>

A tester&#8217;s value tends to be recognized at the same rate as relationships develop. Testers get characterized as <a href="https://web.archive.org/web/20190609162441/https://en.wikipedia.org/wiki/Folk_hero">folk heroes</a> rather than members of a skilled profession. There&#8217;s no trade, education, or craft just individuals saving the day periodically.

<h3>The Intuition trap</h3>

Even when teams do value testing, people are usually primarily concerned with the progression or regression of testing efforts. Testers comments in stand-ups can easily turn into a user story status change report:

<em>Passed this ticket, working this ticket, no
blockers</em>

If you aren&#8217;t taking the opportunity to discuss your actual actions in stand ups, then you may fall prey to the intuition trap. When you talk about your work this way, sometimes you end up actually working this way.

<h2>Open Source Your Mindset</h2>

It&#8217;s fun being a hero, but there&#8217;s no skill in being <em>Superman</em> or <em>Superwoman</em> (I was going to say Wonder Woman, but she actually trained and I think everyone recognized that. So if you are the teams Wonder Woman then kudos, you have serious skills but I digress).

When testing goes smoothly the result is <em>nothing</em>. 

Testing isn&#8217;t required for things to go right, it just might help prevent a thing going wrong.



<div class="wp-block-image"><figure class="alignleft is-resized"><img data-permalink="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-lightbulb.png" data-orig-file="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-lightbulb.png" data-orig-size="1044,898"  src="http://www.brendanconnolly.net/wp-content/uploads/2021/08/os-devops-lightbulb.png" alt class="wp-image-238 jetpack-lazy-image" width="323" height="277" ></figure></div>

Open sourcing your mindset means <em>teaching</em> others another way to look at and interact with their code, or the product. This cuts both ways though, it means being willing to accept a pull request of
outside perspective. Openly integrating new ideas into your <em>testers mindset</em>.

<h3>Replace Execution with Communication</h3>

<a href="https://web.archive.org/web/20190609162441/http://www.satisfice.com/blog/archives/1346">Testing is a performance</a>. Like acting or athletics there might be a script or game plan to start with but there is a lot going on behind the scenes, adapting to circumstance and being thought up on the fly. It&#8217;s intuition driven.

When actions, practices and motivations are not being verbalized and expressed to the team and stakeholders it puts testing on the level of superstitions and token time sacrifices to the quality gods.

Testers need to pry open this experience, expose the internals driving motivations. Breaking out of that shell grants visibility into a testers actions and motivations to provide a context for team members to attribute value.

<h3>Replace Isolation with Collaboration</h3>

It can be uncomfortable or difficult to open up and share what goes through your <em>testing mindset</em>.

The additional ownership developers have taken in DevOps has changed relationship dynamics. What was at one point a contentious us vs. them relationship is much more open. There just isn&#8217;t the time to have as much formal process driven communication. Success at scale requires collaboration, pairing and mobbing more.

When with developers, it&#8217;s an opportunity to test at their desk, against their local changes. There are risks testing here, the developers local setup is definitely different than production but so are the testing and staging environments. Let go of the taboo of  <strong><em>it works on my machine</em></strong><em> </em>and consider what can be tested here and what needs to be covered on a different stage. Take the opportunity to work together when the code is the freshest in the developers mind and where they are most comfortable.

It&#8217;s not only about working with developers. Mob testing with <em>UX</em> and <em>Product</em> alongside developers is a way to draw the entire team together. When the team is together seeing how the application is working it bypasses all the communication gates. There is no need for a separate follow-up conversations to loop someone in, that person can see and feel how things are working by being a part of the group experience.

<h3>Replace Tedium with Stratagem</h3>

Teams are more open to testing and sharing in quality than ever. Testers have been building quality mindsets for years. Developers are building tooling but teams are looking for guidance and mentorship in <em>Quality</em>.

Testing isn&#8217;t just button pressing, by showing that through communication and working together we elevate our status. Draw people together, into the quality circle, and enable the team to be more comfortable and aware of testing. We can set working agreements, talk about overarching strategy for how testing throughout the development cycle builds quality in. We can embrace automated testing as a team activity where unit, integration and end to end coverage is part of a teams strategy for mitigating risk. We can forgo complete control of testing and opt into being a voice of authority and expertise in quality.
