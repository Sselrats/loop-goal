# File Contracts

This document defines the responsibilities and mutation rules for the files used by the goal loop in a target repository.

## `README.md`

The target repository `README.md` is the entry point for humans and agents.

Purpose:

- Explain what the project is, based on the attached North Star document.
- Explain where the North Star documents live.
- Explain how to start or continue the goal loop.
- Explain where progress is recorded.
- Explain how completion is judged.

Mutation rule:

- Update when the documented project identity, operating instructions, progress tracking location, or completion process changes.

## `docs/*.md`

The `docs` directory is the documented North Star.

These files should be durable, deliberate, and grounded in the user's attached North Star document. They may evolve, but changes should be treated as changes to the target state rather than casual notes.

### `docs/northstar.md`

Purpose:

- Define the mission and desired end state.
- Identify users, stakeholders, outcomes, constraints, and non-goals.
- Preserve the intent that implementation work must serve.

Mutation rule:

- Update when the user's North Star changes, when ambiguity is resolved, or when a documented assumption is corrected.

### `docs/architecture.md`

Purpose:

- Record architecture decisions and architecture constraints.
- Capture tradeoffs, dependencies, integration boundaries, and open architecture questions.
- Avoid forcing a stack unless the North Star or user instruction requires it.

Mutation rule:

- Update when implementation establishes or changes architecture decisions.

### `docs/implementation-plan.md`

Purpose:

- Decompose the North Star into phases, milestones, and dependency-aware work.
- Explain sequencing.
- Identify validation expected at each stage.

Mutation rule:

- Update when the plan changes due to completed work, new evidence, or user direction.

### `docs/operations.md`

Purpose:

- Capture how the project should be run, tested, deployed, maintained, monitored, or supported.
- Preserve unknowns when operational details are not yet decided.

Mutation rule:

- Update when operational commands, environments, deployment decisions, or support expectations become known.

### `docs/safety.md`

Purpose:

- Capture target-project safety constraints.
- Include data handling, security, privacy, reliability, human review, or policy constraints if relevant.
- State what the agent must not do.

Mutation rule:

- Update when risks, constraints, or mitigations become clearer.

### `docs/completion-criteria.md`

Purpose:

- Define what must be true before the long-running goal can be declared complete.
- Provide objective or evidence-based criteria wherever possible.
- Distinguish required completion from optional future work.

Mutation rule:

- Update only when the user's definition of done changes or when ambiguous criteria are clarified.

## `goal.md`

`goal.md` is the long-running convergence policy.

Purpose:

- Explain how agents should move the repository toward the documented North Star.
- Preserve the rule that completion requires satisfying `docs/completion-criteria.md`.
- Describe the loop discipline for implementation, verification, logging, committing, and continuing.

Mutation rule:

- Keep stable.
- Update only when the loop policy itself needs correction or when the North Star changes in a way that affects convergence policy.

`goal.md` must not be used as a scratchpad or a per-cycle task list.

## `next_goal.md`

`next_goal.md` is the mutable execution pointer for the next checkpoint.

Purpose:

- Define the next concrete, verifiable unit of work.
- Explain why that checkpoint is next.
- List expected changes and verification.
- State what is out of scope for the checkpoint.

Mutation rule:

- Update after each successful cycle.
- Update during recovery if stale, already satisfied, or inconsistent with repository state.
- Keep focused on one checkpoint.

Completing `next_goal.md` is not goal completion.

## `WORK_LOG.md`

`WORK_LOG.md` is persistent execution memory.

Purpose:

- Record the history of implementation cycles.
- Preserve decisions, assumptions, verification, blockers, and next steps.
- Help a future agent recover without guessing.

Mutation rule:

- Append a new entry after meaningful work.
- Include enough evidence for another agent to understand what changed and why.
- Corrections are allowed, but do not erase important historical context.

## Git Commits

Git commits are checkpoints.

Each checkpoint commit should:

- Represent a coherent unit of progress.
- Include updates to implementation files and control files when applicable.
- Avoid unrelated changes.
- Leave the repository in a recoverable state.

Commits do not imply completion unless the Completion Criteria are satisfied and the commit explicitly records that completion.
