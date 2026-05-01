<<<<<<< HEAD
---
name: sonar-manifest-update
description: Update issue_manifest.md to mark a group as done. Pass group filename as argument. Example: /sonar-manifest-update issue_group_1.md
allowed-tools: Read, Write, Edit
model: qwen-3.5-122b
---

## Task
Mark `$ARGUMENTS` as ✅ Done in `tmp-sonar/issue_manifest.md`.

## Steps
1. Read `tmp-sonar/issue_manifest.md` in this workspace
2. Find the row where Group File = `$ARGUMENTS`
3. Update its Status column to `✅ Done`
=======
---
name: sonar-manifest-update
description: Update issue_manifest.md to mark a group as done. Pass group filename as argument. Example: /sonar-manifest-update issue_group_1.md
disable-model-invocation: true
allowed-tools: Read, Write
model: qwen2.5-coder:7b
---

## Task
Mark `$ARGUMENTS` as ✅ Done in `issue_manifest.md`.

## Steps
1. Read `issue_manifest.md`
2. Find the row where Group File = `$ARGUMENTS`
3. Update its Status column to `✅ Done`
>>>>>>> afb8bd0b203a3cbb22c8c71dc85c2f6d31b26638
4. Write the file back