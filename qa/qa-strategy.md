# QA Strategy (BDD)

#### Page Navigation

* [Objectives](#Objectives)
* [BDD](#BDD)
    * [Features/Scenarios](#Features-Scenarios)
    * [Building a language](#Building-a-language)
* [Testing approach](#testing-approach)
    * [Functional testing tiers](#Functional-Testing-tiers)
        * [Unit](#unit)
        * [Module](#module)
        * [API](#api)
        * [UI](#ui)
    * [Smoke test](#smoke-test)
* [Non-functional testing](#nfr)
    * [Load testing](#load)
    * [Web accessibility](#wcag)
    * [Security testing](#security)
    * [Browser compatibility](#Browser-compatibility)
        * [Browser support](#Browser-support)
* [Exploratory testing](#Exploratory-Testing)
* [Test environment](#Test-environment)
* [Test Scope](#Test-Scope)
* [Appendix One - Gherkin scenario syntax](#gherkin-scenario-syntax)


## Objectives


The key objectives are as follows:

* Determine the significance, or critical nature, of the application system to the business.

* Determine the types of tests required, at different stages of development cycle, adopting a BDD (Behaviour Driven Development) approach.

* Identify the need for migrated data from legacy systems or other sources.

* Determine the need for a systems integration test by identifying key system interfaces.

* Identify non-functional requirements, such as performance, web accessibility and browser compatibility.

* Defining environment requirements


## BDD (Behaviour Driven Development)

BDD is not so much about "how do I code this?", as "how do I test this?", i.e. before starting to engineer a function, you first think how you would check it works - and that is based on client criteria, the features.  BDD approach entails breaking the User Story into tangible scenarios, creating a Feature.  Sometimes it is necessary to break out a story into several features, and this provides a way of delivering code faster, but identifying functionality that can be delivered sooner. The advantage of scenario format is it is readable and therefore easier to maintain by any of a project team. 

By using an abstracted executable natural programming language (e.g. Gherkin), the scenarios which are also the (automated) acceptance tests. If the spec changes, then so does the test, and flagged up as a fail in the CI Build process. A very self-maintaining system is setp and maintained.

The scenarios do not replace development tasks, but they do give development a clearer path to to translate features into code. BDD effectively addresses the problems with traceability from user story to code, by shortening the path, and introducing control to development and testing signoff process.  BDD can operate within any project methodology, with Scrum and/or Kanban the most commonly applied.


### Features/Scenarios

Development is driven by features and the scenarios.  A user story commonly maps to one feature - if a user story is complex, it can have more than one feature to brak down the user story into in better sized parts, but sometimes more. 

A feature can be very simple, but a pragmatic approach is a user story style heading,followed by 1 or many scenarios (depending on story scope) to break down the feature into alternate flows. These are usually defined by the Product Owner and/or Business Analyst, by consensus with development ipnut.  While it is easy to specify a line such as "I log in as 'xyz' with password 'zyx'", this would entail several backend and frontend tasks to fully complete the feature.  Therefore it is essential that scenarios are defined by the team by consensus, and that scenario context in continual QA – treating your DSL as code, will help prevent DSL library bloat.

Development and QA will review scenarios for completeness, and check matches agreed specification format (Gherkin is the common base BDD specification language, but it's roots are in DSL). UI Developers will need to reference scenarios, as they will include html element name definitions

A user story is considered as "delivered", when all agreed scenarios within user story are complete.  This does not mean, however that user stories are closed, as Agile promotoes idea of continuous improvement, so user stories mature and develop as the project progresses.


### Issue Workflow

An issue can be a user story, a feature, a bug, an improvement or a task - and any other issue type you choose to use.  Following that viewpoint, then an all issues need the same approach when it comes to issue workflow.

1. Issue Defined
2. Issue reviewed/scheduled
3. Test Automation task created (if relevant)
4. Developer tasks/sub-tasks created (front-end and back-end)

#### Note: ALL issues of any type should link to a User Story issue, either by creating a sub-task under story, or linking

Any changes to user story issues should be added to the Gherkin directly, to esnure all are working towards same user story goal (i.e. minimise risk of scope creep or scope inaccuracies).

Bugs should be recorded against a user story, to ensure firstly that bug is relevant in terms of project scope, and also 

### Building a language

Beginning to specify in an agreed format, means effectively developing a language (commonly called a domain-specific language rr DSL), and it should be maintained as such. This means it is imperative to get scenarios clear and comprehensive, and reviewed regularly, as features should not be counted as "Done", until all scenario tests pass. 

## Testing Approach

The testing approach will be driven by the BDD (Behaviour Driven Development), which determines test criteria and scope. 

In BDD there is essentially no difference between aim of development and testing, 
which is a completed user story. Development is driven by scenarios defined by the team, 
and mocks/stubs used in tests, where no UI or integration point exists.  With use of headless browser test software, it will be possible to test the functionality in end-to-end fashion, without full UI, as long as http requests and/or RESTful api services are available.. 


When a QA goes to test a new feature, they will do three things:

* Set up some state, data etc. which the application can work with

* Add test code to enable gherkin scenarios to run as tests

* Assert/Verify outcome.


### Functional Testing tiers

There are 4 tiers of tests for features files (though not all are relevant) – they are Unit, Module, API and UI.

All relevant test code must be completed for a feature, to enable a BDD fail.

#### Unit tests

TBD

#### Module tests

TBD

#### API tests

Functional testing of underlying services, which is not dependant on a completed UI, but scenarios can usually be covered is RESTful services are being used.

Test client(s): Guzzle


#### UI Testing

The UI testing forms the skateholder-focused acceptance tests, so as such is designed with user journeys in mind (i.e. end to end functional test), but still focused on covering overall feature.  The testing will become more important as UI develops, as it becomes the most pragmatic way to demonstrate and sign off features.

Test client(s): Goutte, PhantomJS, Firefox, Internet Explorer


### Smoke Test

The smoke test comprises of both select historical scenario tests, and current ones (i.e. from the current Sprint).  This test set can be run at any time, but usually against master branch or qualified CI Build. A smoke test will be done on Master code branch regualrly, and on branches on demand – ie. Test automation should be integrated into the CI build process.


## Non-functional testing

### Load Test

Load testing can be performed at intervals, at low level using tools such as Apache Jmeter, which provide fast load testing based on http or api or other web-based protocols.  If a more extensive browser-driven load test is required, then a hub/nodes environment wit multiple machines would be necessary.  However most load issues manfifest at a low level, so by adopting a regular lower-level load test to  mitigate pontential issues further into development.


### Security Testing

Periodic checks should be performed using tool such as OWSAP Zed Attack Proxy, to identify common javascript and session security holes.

TBD


### Web Accessibility

A good impact of a structured test automation appraoch, is test code depends on front-end coding standards. The majority of WCAG issues are around front-end coding standards, but also recommended is:-

* Observing ood coding standards in HTML and CSS, most major WCAG issues can be avoided. 
* Time should be allocated for formal evaluation to ensure Level A standards across the site.
* Regular checks by the team using browser emulation or CLI tools to validate code.
* UI Designers should refer to scenarios for naming convention of html elements

### Browser Compatibility

Observing good coding standards negates many common browser compatibility issues, but required browser checks can be integrated as part of regular smoke test

#### Browser Support

TBD

## Exploratory Testing

To follow good Agile practice, exploratory testing will be performed, to explore other user paths (outside of strict scenario paths).  This will be decided by measure of risk that a feature entails, usually at integration points, and the real benefit of Exploratory testing is identifying valid scenarios, that were not at first apparent. Product Owners and stakeholders should be encourage to exploratory test, but feedback to should evaluated before introducing into development lifecycle.


## Test Environment

TBD

### Test Automation Framework
Behat Gherkin editor and base Test Fraemwork
Mink (interface too many browser client drivers)


## Test Scope

Defined by Sprint-included features

TBD


## Appendix One - Definition of Done

TBD


## Appendix Two - Gherkin Scenario Syntax

        Feature: The Gherkin

        @phantomjs @goutte
        Scenario: The Gherkin Headless UI
        Given I am on "/"
        And I fill in "Behat" for "s"
        And I press "Search"
        Then count of "27" instances of "Behat" exists on search results page

        @api @goutte @guzzle
        Scenario: The Gherkin API test
        Given I GET request "/api/get_recent_posts"
        Then the response status is 200
        And the status property equals "ok"

        @firefox @ie
        Scenario: The Gherkin Browser UI
        Given I am on "/"
        And I fill in "Behat" for "s"
        And I press "Search"
        Then count of "27" instances of "Behat" exists on search results page

        @firefox @ie @phantomjs @goutte
        Scenario: The Gherkin Form Filling
        Given I am on "/form-test/"
        And I fill in "text" with "some text"
        And I check "checkbox"
        And I select "Option 3" from "select"
        And I check the "radio2" radio button
        And I fill in "textarea" with "some text in text area"
        And I check "checkbox1"
        And I check "checkbox2"
        And I check "checkbox3"
        When I press "Save"
        And I wait for page to update
        Then I should see "Thankyou, we will respond soon"
