<<<<<<< HEAD
---
name: sonar-fix-all
description: Fix all SonarQube issue groups one by one. Reads issue_manifest.md and processes each group sequentially. Run after sonar-group.
model: qwen-3.5-122b
---

## Steps

1. Read `tmp-sonar/issue_manifest.md` — halt if missing, tell user to run `/sonar-list` then `/sonar-group` first
2. For each group row where Status is Pending, in order:
   a. Invoke `/sonar-fix-one <group_file>`
   b. Invoke `/sonar-manifest-update <group_file>`
   c. Use `/compact` before moving to the next group
3. When all groups are done, report summary

## Hard rules
- One group at a time — never load two Java files simultaneously
- /compact between every group — mandatory
=======
---
name: sonar-fix-all
description: Fix all SonarQube issue groups one by one. Reads issue_manifest.md and processes each group sequentially. Run after sonar-group.
disable-model-invocation: true
model: qwen2.5-coder:14b
---

## Task
Process every group in `issue_manifest.md` sequentially.

## Steps

1. Read `issue_manifest.md` — halt if missing, tell user to run `/sonar-list` then `/sonar-group` first
2. For each group row where Status = ⏳ Pending, in order:
   a. Invoke `/sonar-fix-one <group_file>`
   b. Invoke `/sonar-manifest-update <group_file>`
   c. Use `/compact` before moving to the next group
3. When all groups are done, report summary

## Hard rules
- One group at a time — never load two Java files simultaneously
- /compact between every group — mandatory
>>>>>>> afb8bd0b203a3cbb22c8c71dc85c2f6d31b26638
- Never skip a pending group silently