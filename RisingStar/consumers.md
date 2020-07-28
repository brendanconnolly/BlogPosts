# Creators / Executors / Consumers

Depending on the consumer test automation takes on different characteristics

Define the roles


where is the black box in each of these scenarios? 

glass box => transparency in value. Unit tests have transparent value to immediate consumers as well as meaning to downstream consumers.

black box = murkier value. e2e tests less likely to have immediate value, hard to reason about value of a test in future. Confusion of purpose.  Downstream consumers also less clear value and purpose. 


tester as creator/consumer makes puts black box over whole process. This is probably why when a person leaves automation is abandoned or replaced/rewritten. Value isn't clear, logic is wrapped up inside a persons head, computer, unique needs

automation team as creator puts a blackbox around the tests. Test case are provided -> automation team creates tests -> consumers have little context for what tests do or how they do it. 

shared/collective ownership, multi-consumer/multi purpose and clear value add to consumers what makes unit tests work.

## notes
state diagram 
- authoring process
    - testers as creator
    - automation eng as creator
active vs. passive consumption
- developers and tooling are active consumers. Active consumption drives/creates new value, new artifacts. Actual tests have value not just their results. active consumption is inside the creative feedback loop, tests drive development

- e2e consumers are generally passive consumers. The report, or indirect/aggregate measurements  %automted %passing etc. e2e tests are a means to those ends. e2e tests are outside the creative feedback loop the tests are a guardrail, Precautionary vs. proactionary

unit tests are direct consumers of application code
e2e tests are indirect consumers of app code. They have no direct relationship to the underlying code. Instead they are m
They are tightly couple to the environment they are run within as such they are subject to the variability the entire system.

unit coupling = application code
e2e coupling= System Variability+Presentation+Behavior+Code

api testing carves out the presentation and reduces behavior to a series of defined states. 
Test Environment & Test Data Mgmt attempt to isolate the biggest source of e2e variability/reliability.

## e2e
tester/tester/tester
tester/schedule/mgmt - tester
tester/ci-cd/dev
automation eng/schedule/ tester - mgmt
automation eng/ci-cd/tester - dev -mgmt

## api/integration
does this matter
## unit




## Unit tests
 
written by person with vested interest in outcome
multiple levels of feedback loop driven by same tests. 

### Creator
Developer (Written by subject matter expert)

### Executors 
Developer(s)
Pipeline

### Consumers
Initial Author (immediate benefit)
Fellow Developers (current and future / spanning skill levels)
Future/New Developers
Continuous Integration/Deployment
Management 
Metrics
Tools/Reporting

## template
### Scenario
#### Creator
#### Executor
#### Consumer
(identify & breakut what/how consuming, the expectations embedded and reactions to passing and failing results)
#### Positive Outcomes
#### Negative Outcomes/ Risks

## E2E tests
### Scenario: Tester writes the tests

#### Creator
Tester
### Executor
Tester
Scheduled 
Continuous Testing
#### Consumers
Tester (author)
Fellow Testers (possibly)
Management (results in aggregate)

#### Characteristics 
- Tester who authored tests is likely the only direct consumer of the tests. 
- From management perspective the individual test results matter less than the pass/fail rate and general percent automated

#### Requirements To Succeed 

### Scenario: Separate group writes the tests
#### Creator
Automation Engineer
#### Executor
Scheduled / CI CD 
#### Consumer 
Consumer assumptions and Consumer expectations
(identify what/how consuming and expectations)
Management
Development
Tester

#### Positive Outcomes
Reliability may be higher
Maintenance Costs may be lower
Frequent execution may keep tests healthier (living tests)
#### Negative Outcomes/ Risks
Tester has lower visibility into test contents (passing or failing)
Tests are a black box to consumers
Throw it over the fence automation, finger pointing
beuracracy/politics may be higher






