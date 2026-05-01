<<<<<<< HEAD
---
name: sonar-list
description: Fetch all open SonarQube issues for the current branch and project. Run this first before any fix commands.
allowed-tools: Bash(git *), Read, Write
model: qwen-3.5-122b
---

## Task
Fetch every open SonarQube issue for this project.

## Steps

1. Use SonarQube MCP to fetch ALL open issues for $ARGUMENTS
2. Write raw results to `tmp-sonar/sonar_raw_issues.json` in the repo root — no analysis, no grouping

## Hard rules
- Do not open any Java source files
- Do not group or analyze issues — raw dump only
=======
---
name: sonar-list
description: Fetch all open SonarQube issues for the current branch and project. Run this first before any fix commands.
disable-model-invocation: true
allowed-tools: Bash(git *), Read
model: qwen2.5-coder:7b
---

## Task
Fetch every open SonarQube issue for this project.

## Steps

1. Run `git branch --show-current` → store as BRANCH
2. Read `pom.xml` → extract `<groupId>` and `<artifactId>` → PROJECT_KEY = `groupId:artifactId`
3. Use SonarQube MCP to fetch ALL open issues for PROJECT_KEY + BRANCH, paging until exhausted
4. Write raw results to `sonar_raw_issues.json` in the repo root — no analysis, no grouping

## Hard rules
- Do not open any Java source files
- Do not group or analyze issues — raw dump only
>>>>>>> afb8bd0b203a3cbb22c8c71dc85c2f6d31b26638
- Page through ALL results, never stop at page 1