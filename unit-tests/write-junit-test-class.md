# Complete missing Junit tests in an existing JUnit test class

## Purpose
Read and analyse the class $ARGUMENTS as well as the corresponding test class

---

## Steps

### 1. Understand the project structure
Before writing any test, get a global picture of the workspace.

### 2. Understand the class that needs to be tested
Before writing any test, get a good understand of the class $ARGUMENTS that needs to be tested.

### 3. Understand the existing test class and identify missing tests
Before writing any test, understand the existing test class. Before moving on to the next step : 
- identify missing tests to ensure full coverage
- review existing tests and identify any required refactoring needed on existing tests

### 4. Write the unit tests
Write all test cases identified during step 3 as well as apply refactoring is needed to existing tests.

#### Hard rules
- Tests must be written with clear distinct blocks GIVEN, WHEN, THEN
- JUnit test names must be insightful and follow the given_when_then naming convention to elaborate on the purpose of the test
- Tests should be simple and DAMP, not DRY