<<<<<<< HEAD
---
name: sonar-fix-one
description: Fix all SonarQube issues in a single group file.
allowed-tools: Bash, Read, Write, Edit
model: qwen-3.5-122b
---

Copy this checklist and check off items as you complete them:
```
Task Progress:
- [ ] Step 1: Read the sonar issues markdown report
- [ ] Step 2: Read and understand the Java file that needs fixing
- [ ] Step 3: Correct each issue identified during step 1
- [ ] Step 4: Review corrected code
- [ ] Step 5: Check that the code compiles and that no unit test fails after the correction
- [ ] Step 6: Update the sonar issue manifiest
```

**Step 1: Read the sonar issues markdown report**
Run : `cat tmp-sonar/issue_group_$ARGUMENTS.md` in the repo root folder.
Identify target Java file path and the list of issues to correct.

**Step 2: Read and understand the Java file that needs fixing**
Read the content of the java containing the sonar issues in full to gain overall understanding of its code.

**Step 3: Correct each issue identified during step 1**
For each issue, in ascending line order:
- Locate the line
- Apply the fix that satisfies the rule

**Step 4: Review corrected code**
Read the modified java file and check that all issues have been fixed

**Step 5: Check that the code compiles and that no unit test fails after the correction**
Run `mvn test -s ${MAVEN_SETTINGS} -Dtest=$ARGUMENT`
Correct any code that does not compile or that causes a unit test to fail. 

**Step 6: Update the sonar issue manifiest**
Use the skill `/sonar-manifest-update`


## Steps
1. Read `tmp-sonar/issue_group_$ARGUMENTS.md` in the repo root folder  — identify target Java file path and issue list
2. Read the target Java file — full content
3. For each issue, in ascending line order:
    - Locate the line
    - Apply the fix that satisfies the rule
    - Document before/after in the group file
4. Write the fixed Java file in a single pass — never leave it partially fixed
5. Check that the code is still compilable with `mvn compile -s ${MAVEN_SETTINGS} -Dtest=$ARGUMENT`
6. Update `tmp-sonar/issue_group_$ARGUMENTS.md` with status column (✅ Fixed or ⚠️ Skipped) and Fix Details section
7. Update the manifest using skill `/sonar-manifest-update`
8. Stop here. Do NOT move on to next group.

## Hard rules
- Never modify files outside the target Java file
- Never comment code out
- The fixed code MUST be COMPILABLE, the fix must NEVER introduce more issues
- Replace empty constructor by lombok annotation @NoArgsConstructor
- Never add log.isInfoEnabled() or log.isDebugEnabled() checks, these are outdated
- Skip any fix that requires changes across multiple files — document why
- If uncertain about a fix, skip and document — never guess
- Fix code or comment must always be in FRENCH
- The fix must introduce null pointer exception risk
=======
---
name: sonar-fix-one
description: Fix all SonarQube issues in a single group file. Pass the group filename as argument. Example: /sonar-fix-one issue_group_1.md
disable-model-invocation: true
allowed-tools: Read, Write, Edit
model: qwen2.5-coder:14b
---

## Task
Fix all issues in group file: $ARGUMENTS

## Steps

1. Read `$ARGUMENTS` — extract target Java file path and issue list
2. Read the target Java file — full content
3. For each issue, in ascending line order:
    - Locate the line
    - Apply the minimal fix that satisfies the rule
    - Document before/after in the group file
4. Write the fixed Java file in a single pass — never leave it partially fixed
5. Re-read the file and verify no syntax errors introduced
6. Update `$ARGUMENTS` with status column (✅ Fixed or ⚠️ Skipped) and Fix Details section

## Fix guidelines

| Rule | Fix |
|------|-----|
| `java:S2259` | Add null check before dereference |
| `java:S1192` | Extract repeated string to a constant |
| `java:S1135` | Remove or resolve TODO comment |
| `java:S2095` | Use try-with-resources |
| `java:S1874` | Replace deprecated API call |
| `java:S106`  | Replace System.out with logger |
| `java:S1118` | Add private constructor |
| `java:S2142` | Re-interrupt thread after InterruptedException |
| `java:S3985` | Remove unused private field |
| `java:S3776` | Skip — document why (complexity refactor out of scope) |

## Hard rules
- Never modify files outside the target Java file
- Never comment code out
- Skip any fix that requires changes across multiple files — document why
- If uncertain about a fix, skip and document — never guess
>>>>>>> afb8bd0b203a3cbb22c8c71dc85c2f6d31b26638
