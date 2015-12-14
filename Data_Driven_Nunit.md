We'll be using nunit 3 for these examples so I'll be covering the option for data driven tests and some of the changes for nunit 3.0

### Values

### Combinatorial and Pairwise

### TestCase

### TestCaseSource
now required to be static

### Setup and Teardown
teardown only called when a setup has previously been called.

changes in nunit 3
https://github.com/nunit/nunit/wiki/SetUp-and-TearDown-Changes

### Thoughts on Nunit 3
This was really more than a version bump for nunit is has been a [rewrite](). While it's officially released it seems like there is a fair amount of work to be done. Pulling in or updating the nuget package for nunit 3 requires a new test plugin for visual studio.