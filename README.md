![Modern Cross-Browser Testing Workshop](images/modern-cbt-banner.png)

# Modern Cross-Browser Testing with Selenium WebDriver in Java

This repository contains the example code for the
[Modern Cross-Browser Testing](https://applitools.com/crossbrowser-testing-workshop/) workshop
led by [Pandy Knight](https://twitter.com/AutomationPanda)
and hosted by [Applitools](https://applitools.com/).

Full instructions for the workshop are provided in [`WORKSHOP.md`](WORKSHOP.md).


## Abstract

As organizations double down on digital,
the concept of quality has evolved from "does it work" to "is it the best experience"
— but the race to deliver innovation to market faster than the competition is causing challenges for software teams.

More frequent releases multiplied by an explosion of device/browser combinations and increased application complexity
has exponentially increased the number of screens that need to be validated each cycle –
an industry average of 81,480 screens to 681,296 for the top 33% –
and traditional test automation can’t keep up.

In this 1-hour workshop,
Pandy Knight, the [Automation Panda](https://automationpanda.com/),
will explain how to create ultrafast automated cross-browser tests
using Applitools Eyes with Selenium WebDriver in Java,
and how to integrate them into CI/CD to provide feedback on quality across all browser/device combinations in seconds.


**Highlights:**

* The importance and evolution of cross browser testing
* Critical requirements for a scalable cross browser testing initiative and pros/cons of different approaches
* Implementing a modern cross browser solution using Applitools Eyes with Selenium WebDriver in Java
* Accelerating test automation with integration into CI/CD


## Outline

1. Traditional cross-browser testing
   1. Writing a typical login test
   2. Running the test locally
   3. Updating the test to handle multiple browsers
   4. Scaling out cross-browser testing yourself
   5. Scaling out cross-browser testing as a service
2. Modern cross-browser testing
   1. Reconsidering what should be tested
   2. Introducing Applitools Ultrafast Grid
   3. Rewriting login as a visual test
   4. Running visual tests across multiple browsers
   5. Integrating modern cross-browser testing with CI/CD


## Prerequisites

To complete this workshop, you will need:

1. An Applitools account
   (register [here](https://auth.applitools.com/users/register) for free)
2. [Java Development Kit](https://www.oracle.com/java/technologies/downloads/) (JDK) 17 
3. A Java IDE like [IntelliJ IDEA](https://www.jetbrains.com/idea/)
4. [Google Chrome](https://www.google.com/chrome/)
   * The up-to-date version of the browser
   * The matching version of [ChromeDriver](https://chromedriver.chromium.org/) installed on system path
5. [Mozilla Firefox](https://www.mozilla.org/en-US/firefox/new/)
   * The up-to-date version of the browser
   * The matching version of [geckodriver](https://github.com/mozilla/geckodriver/releases) installed on the system path


## Architecture

This project is a small Java test automation project
containing [JUnit 5](https://junit.org/junit5/) test cases
for an [Applitools demo site](https://demo.applitools.com).
It uses [Selenium WebDriver](https://www.selenium.dev/documentation/webdriver/) for browser interactions
and [Apache Maven](https://search.maven.org/) for dependency management.
Each test case covers the same login behavior, but they do so in different ways:

1. `TraditionalTest` covers login using traditional assertions on a local machine.
2. `UltrafastVisualTest` covers login using Visual AI with [Applitools Eyes](https://applitools.com/products-eyes/)
   and [Ultrafast Grid](https://applitools.com/product-ultrafast-test-cloud/).


## Running tests

The easiest way to run the tests is one at a time through an IDE.
Alternatively, you can run the tests from the command line with Maven using the `mvn test` command.

`TraditionalTest` runs WebDriver sessions on the local machine.
Each test launch can target either Google Chrome or Mozilla Firefox.
Set the `BROWSER` environment variable to `chrome` or `firefox` to choose the browser.

`UltrafastVisualTest` runs one WebDriver session on the local machine with Applitools Eyes.
Then, it sends snapshots of pages to Applitools Ultrafast Grid to visually test across seven unique configurations.
To connect to the Applitools cloud,
you must set the `APPLITOOLS_API_KEY` environment variable to your Applitools API key.

Both tests can cover the "original" state of the demo site as well as a visually "changed" state.
Set the `DEMO_SITE` environment variable to `original` or `changed` to pick the target site.
`TraditionalTest` should pass for both versions of the site.
`UltrafastVisualTest` should detect visual differences.
Run it first with `DEMO_SITE=original` to set a baseline,
and then run it with `DEMO_SITE=changed` to reveal the differences.
