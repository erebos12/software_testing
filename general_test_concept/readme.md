# General Test Concept for SW development projects

> How much effort to put into automated software tests? 

> Answer: Follow the Testing Pyramid!

![Testing Pyramid](pics/testing_pyramid.png "Testing Pyrami")


## Foundation - Solid/Good Unit Tests
- Unit tests are fast and cheap compared to Service/UI tests – so do a lot of them!
- Test the behavior of the unit, not the execution of lines!
- Recommendation for better unit tests is Test-Driven-Development
    - First write the test, then the production code and then refactor
    - Better interfaces, better tested code and safer maintainability later
    - See https://www.codica.com/blog/test-driven-development-benefits/
- Test coverage should also be used i.e. at least 80% line coverage
    
    > ATTENTION: Don’t fall into the trap, "The higher the code coverage, the better the tests."! This number must be treated carefully. Test behavior, not lines of code!

    - Decide on C1 or C2 code coverage in your developer team
        - Line/Statement or Branch coverage (C1/C2)
        - “Most professional software developers use C1 and C2 coverage. C1 stands for statement coverage and C2 for branch or condition coverage. With a combination of C1 and C2, it is possible to cover most statements in a code base. Statement coverage would also cover function coverage with entry and exit, loop, path, state flow, control flow and data flow coverage. With these methods, it is possible to achieve nearly 100% code coverage in most software projects.” - see https://en.wikipedia.org/wiki/Code_coverage#

- Unit tests should be executed in CI/CD pipeline and a failed unit tests causes failure in the CI/CD pipeline as well (build failure)
    - also not achieving the test coverage percentage i.e. 80% leads to failure of CI/CD pipeline

### Maturity levels of unit testing
- Level 0:
    - no unit tests at all (RED FLAG)
    - Manual Testing after development!
- Level 1:
    - Level 0 +
    - unit tests + 
    - line code coverage percentage defined in the development team (i.e. 80%)
    - No execution of unit tests in the CI/CD pipeline
- Level 2: 
    - Level 1 +
    - Execution of unit tests in the CI/CD pipeline for every build
    - CI/CD build fails when tests are failing or code coverage percentage is not achieved
- Level 3:
    - Level 2 + 
    - apply actively Test-Driven-Development (TDD) in the development team (partially or entirely in the team)
    - In case partially: You try to establish TDD for all developer in future!
    - Not all the time you must do TDD. When you do this most of the time (80-90%), it’s great!


## Service / Integration Tests
- Testing of APIs/microservices (incl. DB)
- Testing the key functionality should be done here, NOT in UI tests
- Recommendation for better testing and better communication between Devs and Business can be achieved by Behavior Driven Development (BDD)
    - BDD enables business team and devs to create their own test language
    - By this test language, the devs can then implement the tests


## UI-Tests
- Most expensive and slowest (slow in execution and writing) tests
- Only a few (most important functions) should be tested
- Functionality under test should not change very frequently
- Use state-of-the-art test frameworks for UI testing (something like Cypress…)
- UI-tests can also be executed MANUALLY but be careful (very costly, time-consuming and unreliable)

