## Project Selected: <Flask>

## I. Introduction

- In this analysis assignment I looked into the testing used in the open source project Flask, I looked through the
  tests with the goal of finding the various types of testing approaches used in the project.

## II. Types of Testing in the Project

### A. Unit Testing

- Unit testing is used extensively throughout this project to verify that the components of the Flask project work
  correctly. Unit tests are able to isolate specific parts of the project are working correctly without having to verify
  that the whole project is working. The Flask app itself is subject to Unit testing. The tests are used to verify that
  the endpoints are working correctly and that the outputs match the expected outcome. The Unit tests are run using
  Pytest which is a python testing framework.

### B. Integration Testing

- Integration testing is used in the Flask project to verify that Flask can work with outside resources as it is
  expected to. The tests that work with the Flask app where Flask uses the werkzeug package would need to use
  integration testing to verify that it works correctly. There are also other apis and packages that Flask uses that
  would need to be tested as well. Integration tests are also run using Pytest.

### C. UI (User Interface) Testing

- In general the Flask framework is more geared toward the development of the backend for web pages, but UI testing is
  still used to verify that web pages with UI elements are correctly rendered and are usable. Much of the UI testing
  seems to be handled int the test/test_views.py file. The tests are verify the functionality of the system, although
  the functionality is checked with many of the other tests int the project test suite. It does not seem to test
  responsiveness outside of making sure that various parts of the system do send a response whenever the endpoints are
  called. As with the previous types of tests listed above the UI tests are run using Pytest. 

### D. Other Types of Testing (if applicable)

- Not Applicable
