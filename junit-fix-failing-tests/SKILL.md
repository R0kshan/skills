---
name: junit-fix-failing-tests
description: Fix compilation errors or failing tests in a given Junit Test class
model: qwen-3.5-122b
allowed-tools: Bash, Read, Write, Edit
---

## Task
Fix failing tests for the given Junit Test class $ARGUMENTS.

## Steps

1. Read the tested class $ARGUMENTS  ($ARGUMENTS without the 'Test' suffix) and take note of imports, classes used and responsibility of the class
2. Read the test class $ARGUMENTS
2. Read the pom.xml to identify test dependencies (search for those with <scope>test</scope>)
3. Run the test class with the following command : `mvn test -s ${MAVEN_SETTINGS} -Dtest=$ARGUMENT`
4. If the class is not compilable or tests fail, correct it (without degrading test quality and intention) and repeat step 3. Else if all tests pass  stop here.

## Hard rules
- Follow instructions and use given commands to the letter
- Do not modify tested class
- The tests must be COMPILABLE
- The tests must PASS (without deleting existing test or assertions)
- Test quality and intention MUST NOT be degraded during compilation or test failure fix
- The fix musn't introduce Sonar warnings