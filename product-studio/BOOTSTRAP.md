# Product Studio Bootstrap

Start here when Product Studio is newly imported or has just been upgraded.

## Read Order

1. Read `SOUL.md` for the company identity, non-negotiables, and scope discipline rules.
2. Read `STACK.md` for the canonical tech stack, layer decisions, and agent guidance on library APIs. Read this before assigning any build work.
3. Read `COMPANY.md` for the canonical workflow, fallback coverage, file classes, and gates.
4. Read `README.md` for the package overview, role inventory, and starter surface.
5. Read `SKILL-ARCHITECTURE.md` for the local capability rules, paired-build ownership split, and canonical handoff shape.
6. Read `CONTRIBUTING.md` before changing structure, prompts, or runtime docs.
7. Read the active role contract as a bundle: `agents/<role>/AGENTS.md`, `agents/<role>/HEARTBEAT.md`, and `agents/<role>/TOOLS.md`.

## Delivery Pipeline

Product Studio runs one gated seven-role pipeline:

1. `CEO` writes the product brief.
2. `Senior Designer` writes the experience spec.
3. `CTO` writes the technical execution plan and opens the paired build stage.
4. `Senior Designer` implements the frontend, UI-behavior, and design-system slice while `Product Engineer` implements the backend, app-logic, and integration slice on one shared review target. The Paperclip assignee stays `Product Engineer`.
5. `Staff Engineer` issues the structural review verdict on the shared build artifact.
6. `Release Engineer` ships the reviewed work.
7. `QA Engineer` verifies the shipped result and reports back to `CTO`.

Do not skip gates. If a stage fails, route backward to the role that can fix the blocker.

## Step 0 — One-Time Project Setup (run before the first product sprint)

Before starting any product work, the CEO assigns these two setup tasks to establish the production baseline:

1. **Deploy config** — assign `templates/projects/project-setup/tasks/deploy-config/TASK.md` to the **Release Engineer** to run `/setup-deploy` and lock the deploy platform, health-check endpoints, and environment URLs.
2. **Benchmark baseline** — assign `templates/projects/project-setup/tasks/baseline-benchmark/TASK.md` to the **QA Engineer** to run `/benchmark` and capture the initial performance baseline.

Do not start the first product sprint until both tasks are complete. QA cannot detect regressions without a baseline.

## Required Surface Before Assigning Work

Confirm these files exist and agree before you start:

- `SOUL.md`
- `COMPANY.md`
- `README.md`
- `SKILL-ARCHITECTURE.md`
- `CONTRIBUTING.md`
- `.paperclip.yaml`
- `memory/session-history.md`
- `memory/decisions.md`
- `memory/PROJECT-INVENTORY.md`
- `templates/HANDOFF.md`
- `templates/AGENT-PROMPT-CHECKLIST.md`
- `templates/FRONTEND-CONTRACT.md`
- `agents/<role>/AGENTS.md`
- `agents/<role>/HEARTBEAT.md`
- `agents/<role>/TOOLS.md`

## Starting Work

- Start from `templates/projects/new-product-launch/PROJECT.md` for a new product or major feature through the full pipeline.
- Start from `templates/projects/bug-fix/PROJECT.md` for bug triage through fix, review, and verification.
- Start from `templates/projects/design-iteration/PROJECT.md` for design-only changes that don't need the full pipeline.
- Start from `templates/projects/project-setup/PROJECT.md` for the one-time deploy config and benchmark baseline (Step 0 above).
- Start from `templates/tasks/weekly-portfolio-review/TASK.md` for the recurring CEO cadence.
- Start from `templates/tasks/weekly-retro/TASK.md` for the CTO's weekly engineering retrospective.
- Use `teams/engineering/TEAM.md` when you need the engineering org context.
- Use `templates/HANDOFF.md` for issue comments, `templates/FRONTEND-CONTRACT.md` before opening the paired build stage, and `templates/AGENT-PROMPT-CHECKLIST.md` before rewriting any role prompt.

If you add a new file class or change startup expectations, update `COMPANY.md`, `README.md`, and `CONTRIBUTING.md` together.
