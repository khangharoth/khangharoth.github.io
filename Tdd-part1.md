## TDD Part 1 : The Unfulfilled promise

Why is TDD still mandated and not practised in most of the teams/organizations ground up?

A typical experience is that teams practise this for some time (six months to a year) and then give up on it. This shouldn't be happening, as the whole premise was that once the team starts doing TDD, they will see the benefits and would never go back.

What’s the reason for this peculiar phenomenon? In my experience, it's down to the benefits which were promised but never materialized for the individuals or teams.


Again, why are the developers/teams not getting the promised benefits that are so widely discussed and agreed upon?

Let’s look for more detail. One of the biggest challenges faced by the team is the inability to maintain the test suite over the life cycle of the project. In the beginning, with few tests and a small code base, tdd seems to be working and teams thought they were on the right track. Over time some common issues occur which makes the whole premise of the said benefits questionable.

So what are these problems?

- **Difficult to understand the intent**: Yes, the tests failed, but it’s really hard to understand the intent of those tests and hence no real value add in case of failures. What’s under test is not easy to understand and it defeats the whole purpose of having tests in the first place.
- **Increase in build time**: Applications grow and so did the number of tests and pretty soon the build takes more than 10 min (a high threshold for the good test suite) and this time starts adding for every check-in and slows the overall process down. Key reasons for the increase in build time are

  - Attachment to the existing Tests: Developers see the tests as some sort of investment and hence never deletes old/obsolete/repeated test cases.
  - Slow Test: Test taking a sec to run looks fast but are indeed very slow . 1000 such test would take close to 16 min to run.
  - Not able to run in Parallel: In lage projects with more than 20K+ tests, team will have to make investments to run the whole test suite in paralle.
  
- **Randomness in tests**: Test fails randomly i.e on rerun the build passes and the team members gets into the habit of running the build again. Rather than fixing the underlying issues, randomness adds over time and the test suite becomes more like a coin toss, rather than a tool to give feedback.

- **Long time to fix build failures**: Due to the randomness, team members are not sure if the build is failing because of a new change, or it's down to randomness and this leads to red builds for long before a team members take a look.

- **Checkin on Red builds**: As red build becomes the norm so is check-in on already failing build and from there it's all downhill.

- **Tests interfering with the refactoring**: Tests written after the code is written, typically exhibit this problem, where the coupling between the test and code is very high.
  - Inadvertently the test is testing the implmentation and not the functionality and this leads to tight coupling between test and the underlying code.
  - Tests, where mocking is heavily used, can become very brittle. Normal refactoring to change the shape of code can lead to test failures . 
  
- **Over Testing**: Testing is done in layers, where the outer layer test tries to test the whole internal implementation ex: DAO Test, Services Test, Functional Test & then End to End Test. This results in a common internal codebase (DAO layer) being covered by many-many tests and hence any change there can result in lots of failing tests. Ideally, any part of code should be covered by two tests, one is unit and another End-to-End and hence any change should only result in two failing tests.
- **Individuals not committed to TDD philosophy**: TDD is a team sport and hence everyone in the team needs to adhere to the philosophy of writing tests first and then continuous refactoring. Even one member, not following these guidelines can create the above-mentioned problems for the entire team.
