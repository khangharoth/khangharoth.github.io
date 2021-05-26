TDD Part 2 : TDD Anit-Patterns

Almost all teams who goes through the TDD jounry have to wresstle with below pitfalls or anit-pattern.


So what are htese Tests Anti-Pattern

**The Liar** : 
Passes all tests but doesn’t assert anything useful.
Goal here is high coverage.
Whole the focus is to be able to navigate most of the code without failing, It doesn’t really test the intended target and hence doesn’t give us any feedback.
 
- Cause : Goal is coverage.
Goodhart's law is very relevant here as the coverage stops being good measure.

- Problems :	
Extra code with no value.
Adds to build time
Cost of maintenance esp in times of refactoring.
Gives false sense of security.

- Solution: 
Delete the test . It's not really giving any benefit and has all the costs.


**Excessive Setup**: 
Requires a lot of work set up in order to even begin the testing. Sometimes several hundred lines of codes are used to set up the environment for one test, with several objects involved. This makes it difficult to really ascertain if it is tested due to the “noise” of all of the setup going on.

- Cause : 
The code under the test has a lot of collaborators.It does’t have a clear purpose and violates the single responsibility rule.
Test is written after the code is written. 

- Problems :	
Poor modularity & Poor separation of concern of underlying cod makes tests harder to write. 
Not very clear on what’s the core purpose of the test .
Test and code are highly coupled.
Tests get in the way of refactoring even when the functionality is not changed.
Updating the test suite takes more time than actual change in code.

- Solution : Refactoring the underlying code to improve the separation of the concern. Code needs to be expressed as a better abstraction.Practising tests first helps to uncover the issues early.


**The Giant** : 
A unit test is that, although it is validly testing the object under test, can span thousands of lines and contain many many test cases. This can be an indicator that the system under tests is a God Object

- Cause : Test is written after the code is written.

- Problems :	
Difficult to get the intent of the test.
Test just grew organically without the emphasis on refactoring steps.
Don’t really serve as good documentation of the functionality as not very readable.
Code and Tests are highly coupled and hence fragile.
Test suite which is hard to maintain.

- Solution :
Decompose the test to multiple tests, that is   aimed at specific functionality of code.
Make one assertion per test.


**The Mockery**: 
Test contains so many mocks, stubs, and fakes, that the system under test isn’t even being tested at all, instead data returned from mocks is what is being tested.

- Cause :  Too many collaborators in the code under testing and isolating them results in forgetting the goal of the test.Writing tests first can highlight the growing number of collaborators which are needed to be mocked/stubbed and hence give design level inputs to carve out abstractions.Also result of copy pasting existing test and modifying superficially to add new assertion.


- Problems :	
It does nothing as the thing under test mocks.
Uses so many mocks that actual production code isn’t tested.

- Solution : Review design of the code.
Improve abstraction and separation of the concerns.


**The Inspector**:
Unit test that violates encapsulation, in an effort to achieve 100% code coverage, but knows so much about what is going on in the object. Any attempt to refactor will break the existing test and would require any change to be reflected in the unit test.

- Cause :  Desire to have 100% code coverage .
Writing a code before you write a test.
Improper use of dependency Injection.

- Problems :	
Fragile Tests , internal changes in implementation break the tests.
Inflexible and hard to maintain test suite.
functions/methods are for just tests and are not used anywhere in production code.

- Solution : Never compromise on encapsulation for testing.


**The Dependents** :
An instance where one unit test creates data, that is persisted somewhere, and another test reuses the data for its own devious purposes. If the “generator” is run afterward, or not at all, the test using that data will fail outright.

- Cause :  Desire to reuse the data/code to reduce the set up or the  build time.

- Problems :	
Randomness in the build depending on order of test runs.

- Solution : Isolation in unit tests. Use techniques like data generators to power multiple tests.
            

**The Nitpicker**: 
A unit test, which compares a complete output when it should be only interested in small parts of it.

- Cause : Not having a clear goal of testing, for the code under the test and focus is more on making tests pass. Typical example of missing refactoring step in red-green-refactor cycle.

- Problems :	
Fragile and brittle test suite.
Test has to be continually kept in line with otherwise unimportant details. 
Endemic in web application testing.

- Solution : Focus on the goal of the test and assert only that much

**The Local Hero**: A test case that is dependent on something specific to the development environment, based on which it was written, in order to run. 

- Cause : Not having a proper CI process in place from the start.
          Build is not self-contained and to run on a machine, a pre-set step is required i.e Need a local db in known state before the test run.


- Problems :	
Test passes on the developer machine or development boxe, but fails when attempted to run elsewhere.
Web tests which don't work on CI boxes in headless mode.
Difficult to keep the pre set up step consistent across various machines with different OS and capabilities around project lifecycle.

- Solution : Making sure that end-to-end CI pipeline is in place from the first test.
Build is self contained and can run in  just one step i.e Using techniques like In-memory DB,
JMS, Kafka implementation, to ensure that test can be run end to end without any external dependency. 


**Second Class Citizens** : tests code not given the same rigor and importance as production code in reviews , refactoring etc.

- Cause : Not applying the same rigor as production code, like not having checkstyle , static analysis for test code.

- Problems :	
Tests containing a lot of duplicated code, making it hard to maintain tests.
isn't well refactored as production code.

- Solution : Apply the same rigor as the production code.


**The Silent Catcher** :  A test that passes if an exception is thrown, even if the exception that actually occurs is one, that is different from the one the developer intended.

[Test] [ExpectedException(typeof(Exception))] 
public void ItShouldThrowDivideByZeroException() { 
// some code that throws another exception yet passes the test 
}

- Cause : 

- Problems :	



- Solution : 

**The Secret Catcher** : A test that at first glance appears to be doing no testing due to the absence of assertions, but as they say, “the devil’s in the details.” The test is really relying on an exception to be thrown when a mishap occurs, and is expecting the testing framework to capture the exception and report it back to the user as a failure.

- Cause : Not being explicit with the intent.Typical lack of experience is the reason for this.

- Problems :	
Not very readable and hence results in maintainability issues.
Creating a FUD at the time of refactoring is not very clear when this test fails.



- Solution : Express clear intent in the test case . Having explicit assertions specifying when this test should fail.



**The Dodger** : A unit test which has lots of tests for minor (and presumably easy to test) side effects, but never tests the core desired behavior. Sometimes you may find this in database access related tests, where a method is called, then the test selects from the database and runs assertions against the result.

- Cause : Test written after the code and tries to test easy assertions.

- Problems :	
Test doesn’t explain what the code under consideration should do.
Focus on the implementation details rather than the functionality.
Tests get in the way of refactoring as minor changes results in test failures.

- Solution : Write the test first which is basically aimed at functionality and then have the code which will implement this.
