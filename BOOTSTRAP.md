# Bootstrap Procedure

This document explains how a coding agent should use `loop-goal` to initialize an empty target repository.

`loop-goal` is a bootstrap reference. It is not the application, framework, architecture, or product. The target repository must be shaped by the user's attached North Star document, not by assumptions from this repository.

## Trigger Scenario

The intended user request is:

> The project repository is empty.
> Initialize it by referring to https://github.com/Sselrats/loop-goal and the attached North Star document.

When this happens, the agent should treat the attached North Star document as the source of product intent and treat `loop-goal` as the source of process structure.

## Inputs

Required inputs:

- Empty or effectively empty target repository.
- Attached North Star document from the user.
- This reference repository.

Optional inputs:

- Existing user preferences.
- Existing organizational standards.
- Explicit user constraints about language, framework, hosting, security, or delivery.

Do not invent optional inputs. If a choice is not constrained by the North Star document, repository context, or user instruction, leave it undecided until implementation requires it.

## Target Repository Files To Create

Create these files in the target repository:

```text
README.md
docs/northstar.md
docs/architecture.md
docs/implementation-plan.md
docs/operations.md
docs/safety.md
docs/completion-criteria.md
goal.md
next_goal.md
WORK_LOG.md
```

Additional files may be created only when needed to represent the actual target project, support implementation, or satisfy explicit user instructions.

## Bootstrap Steps

1. Confirm the target repository state.
   - Inspect existing files.
   - If non-empty, preserve existing user work and adapt the bootstrap instead of overwriting.
   - If the repository is empty, create the control files listed above.

2. Parse the attached North Star document.
   - Extract mission, users, outcomes, constraints, non-goals, risks, milestones, operational expectations, and completion criteria.
   - Preserve uncertainty explicitly.
   - Do not add product features that are not grounded in the attached document.

3. Populate `docs/*.md`.
   - `docs/northstar.md` captures the durable product direction.
   - `docs/architecture.md` captures architecture decisions and open architecture questions.
   - `docs/implementation-plan.md` captures the planned sequence of implementation.
   - `docs/operations.md` captures run, test, deploy, maintenance, and support expectations.
   - `docs/safety.md` captures constraints and safety rules specific to the target project.
   - `docs/completion-criteria.md` captures what must be true before the long-running goal can be declared complete.

4. Populate `README.md`.
   - Explain what the project is, using the attached North Star document as the source of product intent.
   - Explain where the North Star documents live.
   - Explain how to start or continue the goal loop.
   - Explain where progress is recorded.
   - Explain how completion is judged.

5. Populate `goal.md`.
   - Convert the documented North Star into a long-running convergence policy.
   - Make clear that the goal is not complete after one cycle.
   - Make clear that `next_goal.md` is only a pointer to the next checkpoint.

6. Populate `next_goal.md`.
   - Select the first smallest verifiable implementation checkpoint.
   - Keep it small enough to complete, verify, log, and commit.
   - Tie it directly to the documented North Star.

7. Populate `WORK_LOG.md`.
   - Record bootstrap date, source inputs, initial assumptions, unresolved questions, and the first planned checkpoint.
   - Leave space for append-only execution entries.

8. Commit the bootstrap.
   - Use git as the checkpoint mechanism.
   - Commit after the target repository has coherent control files.
   - The commit should describe initialization, not product completion.

9. Stop after bootstrap unless explicitly instructed to start the goal loop.
   - During bootstrap, initialize the control structure only.
   - Do not start product implementation unless the user explicitly asks to start the goal loop.
   - After bootstrap, `next_goal.md` should contain the first smallest verifiable implementation checkpoint.
   - Actual implementation should begin through `prompts/start_goal.md` or an explicit user instruction.

## Bootstrap Output Requirements

After bootstrap, a new agent should be able to understand:

- What the project is trying to become.
- What has been decided.
- What remains uncertain.
- What the current checkpoint is.
- What evidence exists from previous work.
- How completion will be judged.

## Prohibited Bootstrap Behavior

Do not:

- Treat this repository as a product template.
- Introduce a default stack.
- Add a framework because it is familiar.
- Create sample product features not present in the North Star document.
- Mark the project complete because initialization succeeded.
- Treat `next_goal.md` as the full goal.
- Overwrite existing target repository work without explicit user approval.

## First Agent Response After Bootstrap

When bootstrap is complete, the agent should report:

- Files created.
- Assumptions carried forward.
- First checkpoint selected.
- Commit hash if committed.
- Any blockers or open questions.
