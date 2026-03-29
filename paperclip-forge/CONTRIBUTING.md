# Contributing To Paperclip Forge

Paperclip Forge should stay small, explicit, and verifiable.

## Non-Negotiable Rules

- Start with `PROJECT-INVENTORY.md`. Do not add or refactor company structure without first documenting what already exists.
- Keep the org graph intentional. New agents require a clear trigger, output, handoff, and definition of done.
- Prefer referenced skills over vendored skill content unless there is a strong reason to fork.
- Keep `SKILL-ARCHITECTURE.md` current when the active skill surface changes.
- Do not add complexity to "look complete". Idle is success. Busywork is failure.
- Every change that fixes drift should also tighten the instructions or templates that allowed the drift.

## Change Workflow

1. Clarify whether the engagement is a new company build or an upgrade.
2. Update `PROJECT-INVENTORY.md` with the current state and discovered sources.
3. Make workflow and skill decisions before writing files.
4. Implement or patch the package.
5. Run a producer-side self-check.
6. Run the Quality Auditor structural validation pass.
7. Run the Code Reviewer final blocking review pass.
8. Let the CEO decide whether the package is deliverable.

## Definition Of Done

A Paperclip Forge delivery is done only when:

- The org chart is coherent and every agent has a clear reporting line.
- Mandatory files exist and are internally consistent.
- Skills are either referenced cleanly or intentionally local.
- Create and upgrade workflows are both documented.
- The package has passed self-check, quality-auditor validation, code-reviewer validation, and CEO signoff.
