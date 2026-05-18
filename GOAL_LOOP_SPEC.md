# Goal Loop Specification

The goal loop is a disciplined implementation process for converging a target repository toward a documented North Star.

The loop is designed for long-running work that may span many agent sessions. It relies on durable documentation, a mutable next checkpoint, persistent execution memory, and git commits as checkpoints.

## Definitions

### North Star

The documented target state of the project, stored in `docs/*.md` in the target repository.

The North Star is not a vague aspiration. It must contain enough concrete direction for agents to make implementation decisions, evaluate progress, and know when the goal is complete.

### Long-Running Goal

The convergence policy stored in `goal.md`.

It explains how agents should keep moving from the current repository state toward the North Star. It does not get replaced after every checkpoint.

### Next Goal

The mutable execution pointer stored in `next_goal.md`.

It describes the next checkpoint only. It is intentionally smaller than the full goal.

### Work Log

Persistent execution memory stored in `WORK_LOG.md`.

It records what happened, what was verified, what was deferred, what assumptions were made, and what should happen next.

### Checkpoint

A git commit that captures a coherent unit of progress.

Commits are not completion claims unless they explicitly satisfy the documented Completion Criteria.

## Invariants

- `docs/*.md` defines the North Star.
- `goal.md` defines the long-running convergence policy.
- `next_goal.md` points to the next checkpoint only.
- `WORK_LOG.md` is append-oriented execution memory.
- Git commits are checkpoints.
- Completing one cycle does not complete the goal.
- Completing `next_goal.md` does not complete the goal.
- Completion requires satisfying `docs/completion-criteria.md`.

## Standard Cycle

Each implementation cycle should follow this sequence:

1. Read the control files.
   - Read `docs/*.md`.
   - Read `goal.md`.
   - Read `next_goal.md`.
   - Read recent `WORK_LOG.md` entries.
   - Inspect git status.

2. Confirm the checkpoint.
   - Verify that `next_goal.md` is still relevant.
   - If repository state has changed, adjust the checkpoint before implementation and record why.

3. Implement the checkpoint.
   - Keep scope tied to `next_goal.md`.
   - Preserve existing user work.
   - Avoid unrelated refactors.
   - Add or update tests and documentation when required by the checkpoint.

4. Verify the checkpoint.
   - Run the most relevant checks available.
   - If checks cannot run, record why.
   - Inspect the resulting diff.

5. Update execution memory.
   - Append to `WORK_LOG.md`.
   - Include files changed, verification performed, decisions made, assumptions, blockers, and follow-up work.

6. Update `next_goal.md`.
   - Select the next checkpoint based on the North Star and current repository state.
   - Keep it concrete and verifiable.
   - Do not use it to rewrite the long-running goal.

7. Commit.
   - Commit the coherent checkpoint.
   - The commit message should describe the actual checkpoint.

8. Continue or stop intentionally.
   - Continue if the environment and user request support continued work.
   - Stop only after leaving `WORK_LOG.md` and `next_goal.md` in a recoverable state.

## Completion Rule

The long-running goal is complete only when all Completion Criteria in `docs/completion-criteria.md` are satisfied.

Before claiming completion, the agent must:

- Review every file in `docs/*.md`.
- Confirm all required implementation work is present.
- Confirm required verification evidence exists.
- Confirm known blockers are closed or explicitly accepted by the user.
- Record the completion assessment in `WORK_LOG.md`.
- Make a final checkpoint commit.

## Recovery Rule

When resuming after interruption:

1. Read `WORK_LOG.md`.
2. Inspect `git status`.
3. Inspect recent commits.
4. Compare repository state to `next_goal.md`.
5. Continue the current checkpoint if it is partially complete.
6. Rewrite `next_goal.md` only if it is stale, incorrect, or already satisfied.
7. Record the recovery assessment in `WORK_LOG.md`.

## Audit Rule

At any time, an agent may audit progress by comparing the repository against `docs/completion-criteria.md`.

An audit should produce:

- Satisfied criteria.
- Partially satisfied criteria.
- Unsatisfied criteria.
- Evidence for each classification.
- Recommended next checkpoint.

An audit is not itself completion unless all completion criteria are satisfied and verified.
