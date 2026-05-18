# Prompt: Start Goal Loop

Use this prompt when the target repository already contains the control files and the agent should begin or continue implementation.

```text
Start the North Star driven implementation loop for this repository.

Read these files first:

- docs/northstar.md
- docs/architecture.md
- docs/implementation-plan.md
- docs/operations.md
- docs/safety.md
- docs/completion-criteria.md
- goal.md
- next_goal.md
- WORK_LOG.md

Then:

1. Inspect git status.
2. Confirm whether next_goal.md is still the correct next checkpoint.
3. Implement the checkpoint described in next_goal.md.
4. Verify the work with the most relevant available checks.
5. Append a detailed entry to WORK_LOG.md.
6. Update next_goal.md to the next concrete checkpoint.
7. Commit the checkpoint.
8. Continue the loop unless docs/completion-criteria.md is satisfied or I explicitly ask you to stop.

Rules:

- docs/*.md is the documented North Star.
- goal.md is the long-running convergence policy.
- next_goal.md is only the mutable execution pointer for the next checkpoint.
- WORK_LOG.md is persistent execution memory.
- Git commits are checkpoints.
- Completing one cycle is not goal completion.
- Completing next_goal.md is not goal completion.
- The goal is complete only when docs/completion-criteria.md is satisfied.
- Preserve existing user work.
- Do not introduce unrelated refactors or ungrounded product assumptions.
```
