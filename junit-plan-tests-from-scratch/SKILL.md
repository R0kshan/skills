---
name: junit-plan-tests-from-scratch
description: Generate a Junit test plan for the given class that has no existing test class
model: qwen-3.5-122b
allowed-tools: Bash, Read, Write
---

## Task
Generate a Junit test plan in a /tmp-junit folder in the repo root for the given class $ARGUMENTS that has no existing test class

## Steps

1. Create the /tmp-junit folder using the following bash command `mkdir -p $(pwd)/tmp-junit`
2. Read the $ARGUMENTS.java file
2. Understand the responsibility of $ARGUMENTS class
3. Read each public and protected method write the following unit test specs to /tmp-junit/$ARGUMENTS-test-spec-<number>.md in natural language :
    - happy sad tests that covers all statement, line and branch (a test per happy path)
    - sad path tests that covers all statement, line and branch (a test per sad path)
4. /tmp-junit/$ARGUMENTS-test-spec-init.md containing all necessary mocks, stubs and variables required to test the class

## Hard rules
- Do not write any code 
- Do not create or modify any java class
- Every public or protected method must be tested
- Private methods should not be tested directly
- Return or modified values must always be verified
- Apply unit testing good practices
- The tested class or it's methods must NEVER be mocked or replaced by a helper
- Each test should verify a single behavior or functionality and avoid testing multiple scenarios in one test
- Test Edge Cases and Error Conditions
- Use the following template when writing the test specification tmp-junit/$ARGUMENTS-test-spec-<number>.md  : 

"
# JUnit Test Specification for class $ARGUMENTS.java

**Test class :**  $ARGUMENTSTest.java
**Tested method :** <name of the method that is being tested>
**Method return type :** <the type of value returned by the method>
**Method modified parameters :** <parameters modified by the method>
**Possible exceptions :** <list the different exceptions that could be thrown by the method>

**Type :** <Happy or sad path> test

**Purpose:** <Purpose of the test>
**Name of the test method :** <Name of the test method using given_when_then>

**Setup (given) :**
<list values, mocks or stubs required>

**Execution (when) :**
<describe what must be done, e.g : calling the public method of the tested class> 

**Expected (then) :**
<describe the actual results (return or modified values by the method) to be verified against expected results, or exceptions thrown in case of sad path>

---
"

- use the following template when writting /tmp-junit/$ARGUMENTS-test-spec-init.md : 

"
# JUnit Test Initialization specifications for class AjouterAuthoritiesService.java

**Test class :** AjouterAuthoritiesServiceTest.java
**Type :** Initialisation
**Purpose:** Définir l'ensemble des mocks, stubs et variables nécessaires pour tester la classe AjouterAuthoritiesService

**Mocks :**
<List mocks, stubs or spies based on class properties and dependencies>

---


