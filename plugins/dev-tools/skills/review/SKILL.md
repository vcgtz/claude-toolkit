---
name: review
description: Principal-engineer code review of a PR, a branch, or the current changes, run by the code-reviewer agent. Returns findings ordered by severity, with the code and why each one matters.
argument-hint: "[PR number | PR URL | branch]"
disable-model-invocation: true
context: fork
agent: dev-tools:code-reviewer
---

Do a code review of: $ARGUMENTS

How to read the target:

- A number or a GitHub PR URL: review that pull request.
- Any other text: treat it as a branch name and review it against the repo's default branch.
- Empty: review the current branch against its base branch, plus any uncommitted changes.

Follow your review steps, checklist and report format. Return only the final report.
