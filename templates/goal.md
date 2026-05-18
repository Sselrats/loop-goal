# Goal

This repository is being implemented through a North Star driven goal loop.

The documented North Star lives in `docs/*.md`. The goal of the loop is to converge this repository toward that documented North Star until the Completion Criteria in `docs/completion-criteria.md` are satisfied.

## Control Files

- `docs/*.md`: durable North Star documentation.
- `goal.md`: this long-running convergence policy.
- `next_goal.md`: mutable pointer to the next checkpoint only.
- `WORK_LOG.md`: persistent execution memory.

## Core Rules

- Completing one cycle is not goal completion.
- Completing `next_goal.md` is not goal completion.
- Git commits are checkpoints.
- After each successful cycle, update `WORK_LOG.md`, update `next_goal.md`, commit, and continue.
- The goal is complete only when `docs/completion-criteria.md` is satisfied.

## Operating Loop

For each cycle:

1. Read `docs/*.md`, `goal.md`, `next_goal.md`, and recent `WORK_LOG.md` entries.
2. Inspect repository state and git status.
3. Implement the checkpoint described in `next_goal.md`.
4. Verify the work with the most relevant available checks.
5. Append an entry to `WORK_LOG.md`.
6. Update `next_goal.md` to the next concrete checkpoint.
7. Commit the checkpoint.
8. Continue unless the Completion Criteria are satisfied or the user instructs otherwise.

## Decision Policy

When making decisions:

- Prefer the documented North Star over convenience.
- Prefer existing repository patterns over new abstractions.
- Keep work scoped to the active checkpoint.
- Preserve user changes.
- Record assumptions and unresolved questions.
- Do not introduce a language, framework, service, or architecture unless supported by the North Star, repository context, or user instruction.

## Completion Policy

Before declaring this goal complete:

1. Review every file in `docs/*.md`.
2. Evaluate every item in `docs/completion-criteria.md`.
3. Verify the implementation with available checks.
4. Record evidence in `WORK_LOG.md`.
5. Commit the completion assessment.

If any required criterion is unsatisfied, update `next_goal.md` with the next checkpoint instead of declaring completion.
