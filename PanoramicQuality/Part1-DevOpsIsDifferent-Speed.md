## DevOps is Different

## It's Not About the Pipeline

Continuous Integration and Continuous Deployment are important in dev ops, but once your pipeline is established and verified it just becomes part of the scenery. It's a feature that probably shipped months or even years ago. At most some type of regression testing of it may come up but its not really something at the forefront of a testers mind in dev ops.

What fundamentally changes testing is dev ops is the rate of change. Projects using waterfall often have a release cycles measured in months (some even years). Agile and scrum revolutionized so much in software by being able to ship at the end of each sprint. This generated a release cadence measured in weeks. Dev ops often has automated deployments scheduled multiple times per day. This means the rate of change to production code can be *orders of magnitude* faster in dev ops than even agile. 

## Speed

The recent past has shown that agile fundamentally changed testing. While a whole host of factors went into it, at some level the sheer need for *speed* eroded many of the divides of old. The hard truth is generally teams can't ship software every week or two with siloed information and highly bureaucratic processes. Testers and testing didn't really have any viable option but [shift left]().

If you accept that the pace change from waterfall to agile incited a wild fire of process and professional change in testing, then dev ops presents a similar scale need for change. The bi-weekly (or longer) sprint based release cadence still afforded testers days of testing.

## Risk / Release Inversion 

The biggest risk in delaying release used to be around dealing with customer commitments or expectations. Ship something (anything) now and deal with the fall out, or hold the release and brace for some uncomfortable conversations with customers or managers. The usual software story goes: There was a schedule or plan => stuff happens => delays occur => release dates stay the same => time shaved from Testing / QA cycles. 

In situations like that part of being a tester, sometimes mean having to be brave enough to say this something isn't ready for production and stand firm in your convictions about quality. Then you get the joy of commiserating with fellow testers about how you organization isn't really committed to quality. It's not a super healthy place to be, if only we had more time for testing...

It seems a straightforward trade, **give time**  and **get quality**.  This fact just does not hold true in dev ops.

There used to be safety in waiting to push to production. Code was generally safer sitting in your office than sitting in production. Time in testing in this sense is risk reducing. Dev ops inverts this relationship, and ramps the risk up to 11 while it sits due to the frequency of deployments. 

A typical testing approach in dev ops can quickly end up between a rock and a hard place. The pace of production change creates situations where there is more risk and uncertainty in code going stale, in falling behind master. Rework shifts away from bug fixes, to instead the repeated merging of master into a branch and resolving conflicts or other side effects. Code can be bug free while in testing, but if it takes too long can end up with bugs by the time it deploys.

## The Verification Trap

How do you test effectively when code around you is changing hourly?


Now we have 

## Stability through Frequency 
We Know
other environments aren't production, or even production like
