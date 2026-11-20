---
name: review
description: Principal-engineer code review of a PR, a branch, or the current changes, run by the code-reviewer agent. Shows every finding ordered by severity, with the code, why it matters, a suggested fix and a suggested PR comment.
argument-hint: "[PR number | PR URL | branch]"
disable-model-invocation: true
---

Run a code review of: $ARGUMENTS

1. Run the `dev-tools:code-reviewer` agent with the Agent tool, and give it this task:

   > Do a code review of: $ARGUMENTS
   >
   > How to read the target:
   > - A number or a GitHub PR URL: review that pull request.
   > - Any other text: treat it as a branch name and review it against the repo's default branch.
   > - Empty: review the current branch against its base branch, plus any uncommitted changes.
   >
   > Follow your review steps, checklist and report format. Return only the final report.

2. Wait for the agent's report. Do not review the code yourself.

3. **Show the agent's report to the user exactly as it is, in full.** Every finding with its code blocks,
   line numbers, suggestion and suggested PR comment. Do not summarize, shorten, reorder or rewrite it:
   the user needs the code and the PR comments. Do not add anything before the report. After it, add at
   most one line, for example that nothing was posted to GitHub.
