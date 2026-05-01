---
name: junit-verify-code-coverage
description: Use mvn command verify code coverage using Jacoco
model: qwen-3.5-122b
allowed-tools: Bash, Read, Write, Edit
---

## Steps
1. Run tests + generate coverage report for $ARGUMENTS class using command : mvn test -s ${MAVEN_SETTINGS} jacoco:report -Dtest=$ARGUMENTS
2. Create the file /tmp-coverage-$ARGUMENTS.md in the repo root
3. Run cat target/site/jacoco/jacoco.csv
4. Write the results of the jacoco report in /tmp-coverage-$ARGUMENTS.md using the following example  : 

"
# Code Coverage Report
**Class under test:** `com.example.MySourceClass`  
**Test class:** `MyTestClass`  
**Date:** 2024-01-15  
**Branch:** main

---

## Summary

| Metric         | Covered | Missed | Total | Coverage |
|----------------|---------|--------|-------|----------|
| Lines          | 42      | 8      | 50    | 84%      |
| Branches       | 18      | 6      | 24    | 75%      |
| Methods        | 10      | 1      | 11    | 91%      |
| Classes        | 1       | 0      | 1     | 100%     |
| Instructions   | 210     | 30     | 240   | 87%      |
| Complexity     | 12      | 3      | 15    | 80%      |

---

## Coverage Status

> 🟢 Lines: 84% | 🟡 Branches: 75% | 🟢 Methods: 91%

---
"

## Hard rules 
- Do NOT look for $ARGUMENT location
- Use the exact mvn command indicated in the steps do NOT run any other command 



