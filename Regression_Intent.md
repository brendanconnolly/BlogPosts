## Intent over Implementation

### Regression is an intention-centric <wording?> endeavor. 

Consider your product has over time added 3 different yet inter-related options. Depending on the permutation specific behavior is expected, however not all permutations are valid. In a later release the UI is updated so instead of the old 3 options, the user is presented with a choice of valid states but behind the scenes, the same 3 options are configured. 

How does this effect testing?

Feature of that change verifies that the UI changes set the 3 options correctly. Going forward regression testing of the existing functionality 

Whether tracked in test cases or automated tests, regression testing of any behavior dependant on those feature remain unchanged. Worst case only minor changes to the preconditions to the tests change.

The intent of the test remains unchanged, how the test was setup is an artifact of the implementation and has no bearing on future testing. 

The same process applies to your product if you add a mobile app or migrate from a desktop to web based experience. By having core of your regression testing  centered around what an end user intends to do rather than explicitly how or where things are done testers can more deeply 

### Regression is like the mission statement of your product. 



