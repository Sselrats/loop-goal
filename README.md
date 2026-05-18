# loop-goal

`loop-goal` is a bootstrap reference repository for initializing an empty target repository into a North Star driven implementation loop.

It is not an application template. It is not a framework. It is not the product being built.

This repository exists so a coding agent can read it when a user says:

> The project repository is empty.
> Initialize it by referring to https://github.com/Sselrats/loop-goal and the attached North Star document.

The target repository should receive project-specific files derived from the user's attached North Star document. The files in this repository describe the loop, file contracts, safety rules, reusable templates, and prompts needed to start and continue that work.

## What This Repository Provides

- A bootstrap procedure for empty target repositories.
- A goal loop specification for long-running implementation work.
- File contracts that define the responsibilities of `docs/*.md`, `goal.md`, `next_goal.md`, and `WORK_LOG.md`.
- Safety rules for keeping the implementation grounded in the documented North Star.
- Templates that a coding agent can copy into the target repository and adapt to the attached North Star document.
- Prompts that the user or agent can use to initialize, start, recover, or audit a goal loop.

## What This Repository Does Not Provide

- No product requirements.
- No application architecture.
- No implementation language.
- No runtime.
- No package manager.
- No framework.
- No deployment target.
- No default feature set.

Any such choices must come from the attached North Star document, the target repository context, or explicit user instruction.

## Core Semantics

In the target repository:

- `docs/*.md` is the documented North Star.
- `goal.md` is the long-running convergence policy.
- `next_goal.md` is only the mutable execution pointer for the next checkpoint.
- `WORK_LOG.md` is persistent execution memory.
- Git commits are checkpoints.
- Completing one cycle is not goal completion.
- Completing `next_goal.md` is not goal completion.
- After each successful cycle, the agent should update `WORK_LOG.md`, update `next_goal.md`, commit, and continue.
- The goal is complete only when the documented North Star Completion Criteria are satisfied.

## Expected Bootstrap Flow

When the target repository is empty, the agent should:

1. Read this repository as a reference.
2. Read the attached North Star document supplied by the user.
3. Create the target repository's `docs/*.md` files from the attached North Star document.
4. Create `goal.md`, `next_goal.md`, and `WORK_LOG.md` in the target repository.
5. Preserve the separation between documented intent, long-running policy, next execution checkpoint, and execution memory.
6. Make the first checkpoint commit.
7. Continue the implementation loop until the North Star Completion Criteria are satisfied.

## Repository Contents

- `BOOTSTRAP.md`: Procedure for initializing an empty target repository.
- `GOAL_LOOP_SPEC.md`: Detailed rules for the implementation loop.
- `FILE_CONTRACTS.md`: File responsibilities and mutation rules.
- `SAFETY_RULES.md`: Guardrails for scope, evidence, commits, recovery, and completion claims.
- `templates/`: Copyable starting files for target repositories.
- `prompts/`: Directly usable prompts for bootstrap, execution, recovery, and audit.

## How To Use This Reference

Use `prompts/bootstrap_empty_repo.md` when initializing an empty target repository. The prompt assumes the user has attached a North Star document and asked the agent to refer to this repository.

Do not copy this repository as a product skeleton. Copy only the reference process and the neutral control files needed to govern the target repository.
