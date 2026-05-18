# Prompt: Recover After Stop

Use this prompt when work stopped unexpectedly, the agent session changed, or repository state may be partially complete.

```text
Recover the North Star driven implementation loop after a stop.

Read these files first:

- WORK_LOG.md
- next_goal.md
- goal.md
- docs/completion-criteria.md
- docs/*.md

Then inspect:

- git status
- recent commits
- current repository files related to next_goal.md

Determine:

1. What checkpoint was in progress.
2. Whether the repository has uncommitted work.
3. Whether next_goal.md is pending, partially complete, complete, stale, or incorrect.
4. What verification has already happened.
5. What the next safest action is.

Then:

- Continue the current checkpoint if it is still valid.
- Update next_goal.md only if it is stale, already satisfied, or inconsistent with repository state.
- Append a recovery entry to WORK_LOG.md.
- Verify any completed work.
- Commit a coherent checkpoint when ready.
- Continue the loop unless docs/completion-criteria.md is satisfied or I explicitly ask you to stop.

Do not claim goal completion unless docs/completion-criteria.md is satisfied with evidence.
```
