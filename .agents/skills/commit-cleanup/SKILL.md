---
name: commit-cleanup
description: Perform final code, documentation, and memory cleanup sweep before committing changes to version control. Trigger with "/commit-cleanup".
argument-hint: "[optional notes or scope]"
---

# Purpose

The `/commit-cleanup` skill performs a low-risk pre-commit sweep for **{{PROJECT_NAME}}**. It ensures debug logging, dead code, and formatting inconsistencies are resolved, and updates session memory state before committing code to git.

---

## Step 1 — Code Hygiene Sweep

Inspect modified files (`git status` / `git diff`) and perform cleanup:
- **Remove Debug Logging:** Delete temporary `console.log`, `print()`, debugger breakpoints, or test print statements.
- **Remove Dead Code:** Delete commented-out code blocks, unused imports, and unused local variables.
- **Format & Lint:** Fix formatting inconsistencies and compiler/linter warnings.

---

## Step 2 — Memory & Verification

- **Verify Implementation:** Run test suites or build scripts to confirm clean compilation and zero test failures.
- **Update Memory State:** Run the `/handoff` skill to update `.agents/memory/AI_HANDOFF.md`.
- **Log Architectural Decisions:** Record new canonical decisions in `.agents/memory/PROJECT_CONTEXT.md` if milestones were achieved.

---

## Step 3 — Commit Readiness Report

Output a structured report:

```markdown
### Pre-Commit Cleanup Summary
- [ ] Code Hygiene: Debug logs, dead code, and unused imports removed.
- [ ] Verification: Build/tests passed.
- [ ] Memory Sync: `.agents/memory/` files updated.

### Suggested Commit Message
`feat/fix/chore: concise conventional commit title`
```
