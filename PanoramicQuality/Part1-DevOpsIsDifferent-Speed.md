## Quality at the Speed of DevOps

## It's Not About the Pipeline

Continuous Integration and Continuous Deployment are important in DevOps, but once your pipeline is established and verified it just becomes part of the scenery. It's a feature that probably shipped months or even years ago. At most some type of regression testing of it may come up but its not really something at the forefront of a testers mind in DevOps.

What fundamentally changes testing is DevOps is the rate of change. Projects using waterfall often have a release cycles measured in months (some even years). Agile and scrum revolutionized so much in software by being able to ship at the end of each sprint. This generated a release cadence measured in weeks. DevOps often has automated deployments scheduled multiple times per day. This means the rate of change to production code can be *orders of magnitude* faster in DevOps than even agile. 

## Speed

The recent past has shown that agile fundamentally changed testing. While a whole host of factors went into it, at some level the sheer need for *speed* eroded many of the divides of old. The hard truth is generally teams can't ship software every week or two with siloed information and highly bureaucratic processes. Testers and testing didn't really have any viable option but [shift left](https://en.wikipedia.org/wiki/Shift_left_testing).

If you accept that the pace change from waterfall to agile incited a wild fire of process and professional change in testing, then DevOps presents a similar scale need for change. The bi-weekly (or longer) sprint based release cadence still afforded testers days of testing.

## Risk / Release Inversion 

The biggest risk in delaying release used to be around dealing with customer commitments or expectations. Ship something (anything) now and deal with the fall out, or hold the release and brace for some uncomfortable conversations with customers or managers. The usual software story goes: There was a schedule or plan => stuff happens => delays occur => release dates stay the same => time shaved from Testing / QA cycles. 

In situations like that, part of being a tester means having to be brave enough to say this something isn't ready for production and stand firm in your convictions about quality. Then you get the joy of commiserating with fellow testers about how you organization isn't really committed to quality. It's not a super healthy place to be, if only we had more time for testing...

It seems a straightforward trade, **give time**  and **get quality**.  This fact just does not hold true in DevOps.

There used to be safety in waiting to push to production. Code was generally safer sitting in your office than sitting in production. Time in testing in this sense is risk reducing. DevOps inverts this relationship, and ramps the risk up to 11 while it sits due to the frequency of deployments. 

A typical testing approach in DevOps can quickly end up between a rock and a hard place. The pace of production change creates situations where there is more risk and uncertainty in code going stale, in falling behind master. Rework shifts away from bug fixes, to instead the repeated merging of master into a branch and resolving conflicts or other side effects. Code can be bug free while in testing, but if it takes too long can end up with bugs by the time it deploys.

## The Verification Trap

How do you test effectively when code around you is changing hourly?

Awareness of this constant rapid pace isn't unique to testers. Developers know the risks in code sitting, to account for this they also frequently structure their work into a stream of changes smaller changes. You may hear things like 
> I just need to get this deployed to unblock the rest of the team

This puts a lot of pressure on testers, it can be tough to judge the risk in iterative development, since there may not be a clear change that you can explicitly test. When risk is within the range of uncertain to benign, you get forced into a lot of *judgement call* testing. 

#### *Judgement Call Testing Formula*
>(*Perceived Risk* / *Pressure*) * *Developer Competence* = *Acceptable Testing Level* 

It may seem like a unique scenario, but its just one in many common DevOps situations, where the tester is faced with a compressed window of time for testing. 

When time in testing is consistently compressed it's very easy for testers to get accustomed to narrowing their focus to just making sure the change does explicitly what its supposed to. The resulting testing is a surface layer inspection, what amounts to a smoke test. You know its not ideal, you know it's *not really testing* but you aren't sure what else you can do, you find yourself caught up in the **Verification Trap**

#### Rip Current to the Right

Agile may have forced many testers to shift left, but the speed of DevOps can put so much pressure on testers that they can only scramble to keep up, forcefully pushing testers back towards the right. After all, where is the time to be involved in the planning process ofr future work if you are so busy you don't have time to look up from the current round of work. 

It's like a [rip current](https://en.wikipedia.org/wiki/Rip_current) pulling testers back towards the right in the dev lifecycle. Implicitly accepting feature growth over potential feature quality, and encouraging the notion of testers as gatekeepers.

#### Stay Calm, Go Vertical

The solution isn't to back swim against the current, the trap is already sprung and you can't break free through brute force. Teams don't respond to unrealized or potential risk, so muttering warnings about the implications on quality when there isn't a tangible issue is just going to push you farther out to sea. It sounds just like *QA Paranoia*.

##### Vertical Hands

Stay calm, get through it for the short term. You may be a lone tester but you aren't alone on your team. Raise your hand, this isn't  a tester problem, and you can't solve it alone. This is a team strategy problem. The cadence of the team is causing an imbalance, which if allowed to continue will degrade team performance and put overall software quality at risk.

This is a perfect topic for the sprint retrospective. Recognize that your team probably doesn't grasp the pressure you feel to sacrifice the quality of your work and therefore risk your credibility. Something like a [Test Strategy Retrospective](http://katrinatester.blogspot.com/2014/04/test-strategy-retrospective.html) can be really useful in nailing down what testing activities are actually being done in throughout the development cycle. Once people are on the same page, conversations can happen about a holistic test strategy going forward. 

##### Vertical Mindset

Agile enabled QA teams the opportunity to share testing across the team, DevOps basically forces your hand in relinquishing ownership of testing. As a tester this can be incredibly unsettling. It causes a bit of an identity crisis, if I am not primarily and actively testing then as a tester what is my role on the team?  

The idea of testers shifting left, or shifting right implies that there is a point in time for inserting quality. Quality isn't an attribute you just create, it's something you influence and allow space for at each step along the way towards release.  You can see similar concepts in [TQM (Total Quality Management)](https://en.wikipedia.org/wiki/Total_quality_management) made famous by Toyota, where quality is made possible through the attention of the entire organization focusing on continual improvement of process and product. Agile/ Scrum teams are just a microcosm of the organization referred to in TQM.

Dev Op's requires testers to take their mindset vertical. Focusing on how to take ownership of enabling quality across the spectrum of the development cycle. To lift their eyes up, away from individual test cases and influence the panorama of pull request to production. 





