# Prompt: Audit Progress

Use this prompt to evaluate progress against the documented North Star without assuming the goal is complete.

```text
Audit this repository against its documented North Star.

Read:

- docs/northstar.md
- docs/architecture.md
- docs/implementation-plan.md
- docs/operations.md
- docs/safety.md
- docs/completion-criteria.md
- goal.md
- next_goal.md
- WORK_LOG.md

Inspect repository state and relevant implementation files.

Produce an audit with:

1. Completion criteria that are satisfied, with evidence.
2. Completion criteria that are partially satisfied, with evidence and gaps.
3. Completion criteria that are unsatisfied, with required work.
4. Any mismatch between docs/*.md, goal.md, next_goal.md, WORK_LOG.md, and implementation state.
5. Recommended next checkpoint for next_goal.md.

Rules:

- Do not treat this audit as completion unless every item in docs/completion-criteria.md is satisfied.
- Do not rewrite the project direction unless the documentation conflicts with itself or the user requests it.
- Preserve user work.
- If you make changes, update WORK_LOG.md, update next_goal.md if needed, and commit the checkpoint.
```
