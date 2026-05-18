# Prompt: Bootstrap Empty Repository

Use this prompt when the project repository is empty and the user has attached a North Star document.

```text
The project repository is empty.
Initialize it by referring to https://github.com/Sselrats/loop-goal and the attached North Star document.

Treat loop-goal as a bootstrap reference repository, not as a product template, application framework, or implementation stack.

Read the attached North Star document as the source of product intent.

Create these files in the target repository:

- README.md
- docs/northstar.md
- docs/architecture.md
- docs/implementation-plan.md
- docs/operations.md
- docs/safety.md
- docs/completion-criteria.md
- goal.md
- next_goal.md
- WORK_LOG.md

Requirements:

- Write all target repository files in English.
- Derive docs/*.md from the attached North Star document.
- Make README.md explain what the project is, where the North Star documents live, how to start or continue the goal loop, where progress is recorded, and how completion is judged.
- Make docs/*.md the documented North Star.
- Make goal.md the long-running convergence policy.
- Make next_goal.md only the mutable execution pointer for the next checkpoint.
- Make WORK_LOG.md persistent execution memory.
- Treat git commits as checkpoints.
- Do not treat one cycle as goal completion.
- Do not treat completing next_goal.md as goal completion.
- Make goal.md document that after each successful implementation cycle, the agent should update WORK_LOG.md, update next_goal.md, commit, and continue.
- The goal is complete only when docs/completion-criteria.md is satisfied.
- Do not force an implementation language, framework, database, deployment platform, or product assumption unless the North Star document or user explicitly requires it.

During bootstrap, initialize the control structure only.
Do not start product implementation unless the user explicitly asks to start the goal loop.
After bootstrap, next_goal.md should contain the first smallest verifiable implementation checkpoint.
Actual implementation should begin through prompts/start_goal.md or an explicit user instruction.

After bootstrapping:

1. Review whether the repository is self-explanatory to a future coding agent.
2. Ensure there is no project-specific assumption not grounded in the North Star document.
3. Ensure no implementation language or framework is forced.
4. Commit the bootstrap checkpoint.
5. Report created files, assumptions, first checkpoint, and commit hash.
```
