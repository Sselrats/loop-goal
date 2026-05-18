# Safety Rules

These rules apply when using `loop-goal` to initialize or continue a target repository.

## Source Of Truth

The attached North Star document and the target repository's `docs/*.md` files are the source of truth for project intent.

If there is a conflict:

1. Follow explicit current user instruction.
2. Then follow the target repository's documented North Star.
3. Then follow this reference repository's loop rules.
4. Then use conservative engineering judgment.

Record unresolved conflicts in `WORK_LOG.md`.

## No Product Assumptions

Do not assume:

- The product category.
- The user interface style.
- The implementation language.
- The framework.
- The database.
- The deployment platform.
- The authentication model.
- The monetization model.
- The team size.

Only introduce these choices when supported by the North Star document, existing repository context, or explicit user instruction.

## Preserve User Work

Before editing:

- Inspect existing files.
- Inspect git status.
- Identify user changes.

Do not overwrite or revert user work unless the user explicitly requests it.

## Scope Control

Each cycle should be tied to `next_goal.md`.

Allowed:

- Changes required for the checkpoint.
- Tests or docs required to verify the checkpoint.
- Small supporting changes that make the checkpoint coherent.

Avoid:

- Unrelated refactors.
- Opportunistic framework changes.
- Broad rewrites.
- Cosmetic churn.
- Work that belongs to a later checkpoint.

## Evidence Before Claims

Do not claim completion without evidence.

For each checkpoint, record:

- What changed.
- What verification ran.
- What verification did not run and why.
- What remains.

For final completion, compare the repository directly against `docs/completion-criteria.md`.

## Checkpoint Integrity

After each successful cycle:

1. Update `WORK_LOG.md`.
2. Update `next_goal.md`.
3. Commit the checkpoint.
4. Continue if the long-running goal is not complete.

If a cycle fails:

- Leave the repository in the most recoverable state possible.
- Record the failure and reason in `WORK_LOG.md`.
- Update `next_goal.md` if the next action changed.

## Recovery Safety

When resuming after a stop:

- Read `WORK_LOG.md` before changing files.
- Inspect `git status`.
- Identify partially completed work.
- Continue from evidence, not assumption.
- Record the recovery decision.

## Completion Safety

The goal is complete only when the documented North Star Completion Criteria are satisfied.

Do not mark the goal complete because:

- The repository was initialized.
- One cycle completed.
- `next_goal.md` was completed.
- A milestone was reached.
- Tests passed for a subset of the project.

Completion requires direct evidence against the full completion criteria.

## Human Escalation

Ask the user before proceeding when:

- Required product intent is missing and a reasonable assumption would create significant product direction.
- There is a conflict between the North Star and current user instruction.
- Completing the checkpoint requires destructive changes.
- Sensitive data, security posture, legal obligations, or irreversible deployment choices are unclear.
