---
layout: post
title: "Automated Testing"
date: 2012-10-12 19:01
comments: true
categories: QA Development TDD
---

I was introduced to Unit Testing back in 2007 on my first agile gig. At that point
Unit tests were defined to me as 'tests that proved individual units of code'. Database connections were a smell, but not forbidden; mocks, stubs were actively encouraged. The closer we got to 100% coverage the better, but we did at least have the sense to not test the language, so no constructor or property testing. 

Functional tests were then defined to me as 'tests the prove that individual units work together'. 
This usually meant writing unit tests, but with spring providing you with real objects rather than mocks and it was generally accepted that a real database / service would be used. This was often an after thought, as we already had close to 100% unit coverage. There purpose was to catch bugs that only occurred in the interaction of objects that would otherwise have only been tested in isolation. The functional suite was a little light, predominantly because it was never really clear if functional tests were really just unit tests. 

Integration tests were then described as 'proving that the whole thing works together', and were originally HTTPUnit tests, until we 'advanced' towards selenium. They were slow and unreliable. The build would break for environmental reasons so often that it was a surprise when they broke for real.

Despite this I was sold, at least I was sold on Unit testing. It just made my code better and gave me a way of thinking about the problem before I thought about the solution, but there were a few problems.

* Slow tests: Unit tests got slow fast. This boiled down to
	* Database calls: you can perform 100 unit tests in the time it takes to make one database call
	* Over mocking / stubbing: reflection is 10-100 times slower than a normal function call and as test code is only run once the most VMs won't optimize it away.
* Writing test code often takes a lot longer than writing the production code.
* Over testing: 
	* having to change tests in the unit, functional and integration tests
	* having to change five unit tests for one change. 


Five years on and my styles have changed. This is how I see automated testing now.

<!-- more -->

Source control describes the 'who', 'when' and 'why'. This works better the smaller the commit. If you can link your commit to bug / story tracking software all the better. Blame should allow you figure out why a piece of code looks the way it does. 

_Functional tests describe the 'what'._ 

They are the first tests that you write, and describe the API. A measure of a good functional test is that it doesn't change when you re-factor your code. They should only change when you enhance your code by adding or removing functionality. Real objects should be used whenever possible, but calls to databases and services should be avoided. Mocking and stubbing of external libraries, services and databases is encouraged only if they make the test faster and more reliable. These tests should be really, really fast. 

This concept is stolen directly from the work of Dan North and Behavioral Driven Design although I have more frequently seen that applied to integration tests rather than functional tests and that almost never works.

_Unit tests describe the 'how'._

The public methods that you are testing via functional tests should be light, with the computation happening in well named protected methods that are called from the public method within reason. These methods need unit testing as they describe 'how' you are implementing your API. Expect to write many unit tests in an effort to get your functional tests to pass.

Unit tests have similar life cycles to the code they test. You should expect a great deal of churn as your code evolves. With each change requiring a change to a unit test. If you can change the code without affecting a unit test you should be asking yourself if you are missing a unit test, or if your unit test was really a functional test. 

If you did no other automated testing than this, you would be in really good shape. Follow this plan and you will have a test suite that executes hundreds of tests per second and each of those tests can be run in parallel. You will also have a nicely documented piece of software, with each line of code's purpose explained by a mixture of source control, functional and unit testing. 

But you still need to do manual testing. In fact, from this point on, the testing should be orchestrated by someone other than the developer on the story and you will always need manual testing. 

Integration tests are where functional tests meet reality. You use a real database, you might even hit real services, provided that you have as much control over those services as you do your database. The application is poked in the same way a user would poke it.

Two things separate my views on integration tests from the integration of old. 

Firstly, I believe Selenium is the tool of last resort. If you use functional and unit tests as I've described for both your server and client side logic you already have a pretty comprehensive test suite. All that is left to test is that you get the right data back for the right inputs when everything is wired together. That can be achieved with something as simple as HTTPUnit or even just poking controllers from your XUnit tool. You do loose the ability to click the button or check that a pop-up pops, but you get a test suite that is hundreds of times faster, significantly simpler to maintain and reliable. 

Selenium is a miracle of modern engineering, built by some of the most talented and passionate developers in the world, but they are totally beholden to the teams that build browsers who, whilst selenium might be on their priority list, it is towards the bottom. The result is that browser automation tests crash. They crash because browsers don't like being poked by anything other than a human at human speeds. If you absolutely have to test that your pop-up pops every build, automatically, Selenium is the best tool, it just may be more expensive than you realized. 

Secondly, I think that they need to be owned by some one who is directly responsible for efficiency of the team, not the functionality / efficiency of the application. Team / Tech / QA leads or the PM are all good candidates, business owners and the development team are not. There needs to be a budget for integration tests and that budget needs to be tracked by the project as a whole. If an integration tests breaks for a legitimate business reason developers first should inform QA that they need to manually test that part of the code now and then deactivate that test. 

It is then the responsibility of whomever owns the integration build to get time allocated to fix it. 

Making integration tests track-able outside of the normal story cost forces the owners to focus on keeping them as cheap and efficient as possible and stops the anti-pattern of having an 'acceptance' test for each story. The reason for this is that integration tests take minutes to run, and are rarely embarrassingly parallel. Adding minutes to the build has a direct effect on velocity and whilst integration tests can save a significant amount of QA churn, they are not a silver bullet. There needs to be evidence that the integration suite is actually improving velocity before each and every minute is added.
