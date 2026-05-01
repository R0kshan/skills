---
name: junit-write-tests-from-scratch
description: Generate a Junit test class from scratch for a given class
model: qwen-3.5-122b
allowed-tools: Bash, Read, Write, Edit
---

## Task
Initialize and write the unit test specified in  $ARGUMENTS.

## Steps

1. Read the tmp-junit/$ARGUMENTS-test-spec-$ARGUMENTS.md 
2. If the $ARGUMENTS test class does not exist, read the /tmp-junit/$ARGUMENTS-test-spec-init.md to create the test class accordingly
3. Check that it is compilable with the following maven command : `mvn test -s ${MAVEN_SETTINGS} -Dtest=$ARGUMENTS` with $MAVEN_SETTINGS defined in environnement variable
4. If the class is not compilable, correct it and repeat step 3. Else proceed to step 5.
5. Write all the test identified in tmp-junit/$ARGUMENTS/test-spec-$ARGUMENTS.md

## Hard rules
- Only write code to $ARGUMENTSTest class
- The tests must be COMPILABLE
- All tests must PASS (but do not CHEAT or reduce test quality to get a passing unit test)
- Use Mocking and Stubs (using classes available from maven dependencies)
- Apply unit testing good practices
- The tested class or it's methods must NEVER be mocked or replaced by a helper
- Follow the AAA Pattern (Arrange, Act, Assert)
    - Arrange: Set up the test environment and inputs.
    - Act: Execute the function or method being tested.
    - Assert: Verify the expected outcome.
- Code and comments must be written in FRENCH
- The tests musn't generate Sonar warnings