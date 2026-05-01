---
name: junit-write-tests-from-scratch
description: Generate a Junit test class from scratch for a given class
model: qwen-3.5-122b
allowed-tools: Bash, Read, Write, Edit
---

## Task
Initialize and write the unit test class for this class $ARGUMENTS.

## Steps

1. Initialize test class according to the /tmp-junit/$ARGUMENTS-test-spec-init.md found in the repo root folder
2. For each /tmp-junit/$ARGUMENTS-test-spec-<number>.md file (found with `ls /tmp-junit/`)
   1. read the file
   2. Apply the '/junit-write-single-test-from-scratch $ARGUMENTS' skill to write the corresponding unit test
3. Check that there are as the same number of unit tests as there are /tmp-junit/$ARGUMENTS-test-spec-<number>.md files. If not check implement the missing test.
4. Run /compact command to free context
4. Use '/junit-fix-failing-tests $ARGUMENTS' skill to ensure all tests pass
4. Use '/junit-verify-code-coverage $ARGUMENTS' skill to ensure there's at least 90% code coverage

## Hard rules
- Follow instructions and given commands defined in steps to the letter
- Only write code to $ARGUMENTSTest class
- The method of the testing class MUST ALWAYS be called in the "when"
- The tests must be COMPILABLE (without deleting existing tests or assertions)
- All tests must PASS (without deleting existing tests or assertions)
- For every test specifification /tmp-junit/$ARGUMENTS-test-spec-<number>.md file the corresponding unit test is implemented (ex: if there are 6 files there must be 6 unit tests)