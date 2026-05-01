---
name: junit-code-review
description: Perform a code review on an existing test class
model: qwen-3.5-122b
allowed-tools: Bash, Read, Write, Edit
---

## Task
Perform a code review on the existing test class $ARGUMENTS.

## Steps

1. Read the tested class $ARGUMENTS  ($ARGUMENTS without the 'Test' suffix) and take note of imports, classes used and responsibility of the class
2. Read the test class $ARGUMENTS
3. Read the pom.xml to identify test dependencies (search for those with <scope>test</scope>)
4. Perform a code review on test quality, ensure the test comply to the following :
- All public and protected methods are tested
- Private methods are tested  through calls from public methods
- The output of the tested methods must ALWAYS BE VERIFIED with assertions
- Use Mocking and Stubs (using classes available from maven dependencies)
- Tests are Small and Focused - each test should verify a single behavior or functionality and avoid testing multiple scenarios in one test
- Tests are Deterministic - tests should produce the same result every time they run and do not rely on external factors like network calls or system time
- Tests are Readable and Maintainable
- Tests have descriptive test names
- They are Edge Cases and Error Conditions
- The tests follow the AAA Pattern (Arrange, Act, Assert)
    - Arrange: Set up the test environment and inputs.
    - Act: Execute the function or method being tested.
    - Assert: Verify the expected outcome.
- Code and comments must be written in FRENCH (except for GIVEN WHEN THEN comments)
- The code doesn't use @Deprecated methods from dependencies
- The code uses up to date standards and good practices
5. Give constructive feedback highlighting positive point, negative, what's missing and what needs to be corrected to improve test quality
6. Offer to apply suggested corrections
7. Verify all tests pass with /junit-fix-failing-tests skill
8. Verify method, statement and branch coverage is still at least above 90% with /junit-verify-code-coverage  

## Hard rules
- The applied suggestions musn't degrade tst quality
- The applied suggestions musn't introduce sonar warnings, compilation errors
- The applied suggestions must ensure tests still pass
- NEVER modify the tested class
- The modifications mustn't introduce Sonar warnings