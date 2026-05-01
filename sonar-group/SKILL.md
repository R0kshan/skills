<<<<<<< HEAD
---
name: sonar-group
description: Group raw SonarQube issues by file and write issue_group_N.md files and issue_manifest.md. Run after sonar-list.
allowed-tools: Read, Write
model: qwen-3.5-122b
---

## Steps

1. Read `tmp-sonar/sonar_raw_issues.json` — if missing, run `/sonar-list` first
2. Group issues by file path, ascending line order
3. If a file has more than 10 issues, split into groups: 3a, 3b, etc.
4. Write one `tmp-sonar/issue_group_<ClassName>.md` per group using this exact template:
   Use exactly "issue_group_<ClassName>.md template"
5. Write issue manifest following the "issue_manifest.md template"

## issue_group_<ClassName>.md template 
```
# Issue Group <ClassName>: <relative/path/to/ClassName.java>

## Target Class
`<relative/path/to/ClassName.java>`

## Issues

| # | Rule | Line | Message |
|---|------|------|---------|
| 1 | java:SXXXX | <line> | "<message>" |
| 2 | java:SXXXX | <line> | "<message>" |
```

## issue_manifest.md template

```
# SonarQube Issue Manifest

- **Project**: <groupId>:<artifactId>
- **Branch**: <branch-name>
- **Total issues**: <total count>
- **Total groups**: <number of group files>

## Groups

| Group File | Target Java File | Issue Count | Status
|------------|-----------------|-------------|
| issue_group_1.md | relative/path/to/FileA.java | 4 | Pending 
| issue_group_2.md | relative/path/to/FileB.java | 7 | Pending
| issue_group_3a.md | relative/path/to/FileC.java | 10 | Pending
| issue_group_3b.md | relative/path/to/FileC.java | 3 | Pending
```

## Hard rules
- Do not attempt to fix issues
=======
---
name: sonar-group
description: Group raw SonarQube issues by file and write issue_group_N.md files and issue_manifest.md. Run after sonar-list.
disable-model-invocation: true
allowed-tools: Read, Write
model: qwen2.5-coder:7b
---

## Task
Read `sonar_raw_issues.json` and produce group files + manifest.

## Steps

1. Read `sonar_raw_issues.json` — halt if missing, tell user to run `/sonar-list` first
2. Group issues by file path, ascending line order
3. If a file has more than 10 issues, split into groups: 3a, 3b, etc.
4. Write one `issue_group_<N>.md` per group using this exact template:
   Use exactly this template:

```
# Issue Group <N>: <relative/path/to/File.java>

## Target File
`<relative/path/to/File.java>`

## Issues

| # | Rule | Line | Message |
|---|------|------|---------|
| 1 | java:SXXXX | <line> | "<message>" |
| 2 | java:SXXXX | <line> | "<message>" |
```

5. Write `issue_manifest.md`:

```
# SonarQube Issue Manifest

- **Project**: <groupId>:<artifactId>
- **Branch**: <branch-name>
- **Total issues**: <total count>
- **Total groups**: <number of group files>

## Groups

| Group File | Target Java File | Issue Count | Status
|------------|-----------------|-------------|
| issue_group_1.md | relative/path/to/FileA.java | 4 | Pending 
| issue_group_2.md | relative/path/to/FileB.java | 7 | Pending
| issue_group_3a.md | relative/path/to/FileC.java | 10 | Pending
| issue_group_3b.md | relative/path/to/FileC.java | 3 | Pending
```

## Hard rules
- No confirmation prompts
- No Java source files opened
- Raw SonarQube data only in group files
- Do not attempt to analyze or fix issues
>>>>>>> afb8bd0b203a3cbb22c8c71dc85c2f6d31b26638
