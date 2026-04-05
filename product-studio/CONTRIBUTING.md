# Contributing

Product Studio is intentionally lean. Structural changes should preserve its gstack identity instead of importing a heavier governance layer by default.

## File Classes

- Root operating docs: `COMPANY.md`, `README.md`, `BOOTSTRAP.md`, `CONTRIBUTING.md`, `SKILL-ARCHITECTURE.md`, `.paperclip.yaml`, `SOUL.md`, `STACK.md`
- Role runtime contracts: `agents/<role>/AGENTS.md`, `agents/<role>/HEARTBEAT.md`, `agents/<role>/TOOLS.md`
- Role identity docs (optional per role): `agents/<role>/SOUL.md` — approved for `senior-designer`
- Shared workflow memory: `memory/session-history.md`, `memory/decisions.md`, `memory/PROJECT-INVENTORY.md`
- Capability assets: `skills/**`
- Canonical workflow templates: `templates/HANDOFF.md`, `templates/AGENT-PROMPT-CHECKLIST.md`, `templates/FRONTEND-CONTRACT.md`
- Starter operating scaffolds: `templates/projects/**`, `templates/tasks/**`, `teams/**`
- Optional support material: `references/**`, `images/**`, `*-HANDOFF.md`

## Role Contract Rule

Keep each role grouped as one contract bundle:

- `AGENTS.md` defines the role trigger, owned artifact, handoff, fallback coverage, and anti-patterns.
- `HEARTBEAT.md` is the short recurring checklist.
- `TOOLS.md` names the approved skills and when the role must escalate instead of improvising.

Do not update one file in the bundle while leaving the others stale.

## Structural Change Rules

- Preserve the seven-role gated pipeline.
- Preserve the paired build stage: `Senior Designer` owns frontend and design-system implementation, `Product Engineer` owns backend and integration implementation, and `Product Engineer` stays the single Paperclip assignee during that stage.
- Keep the existing 22 gstack skills unchanged unless a separate issue explicitly approves skill-surface changes.
- Keep Product Studio root-bootstrap only. Do not add a mirrored `templates/BOOTSTRAP.md` unless the package later needs a generator-owned bootstrap source.
- The approved shared memory surface is: `memory/session-history.md`, `memory/decisions.md`, and `memory/PROJECT-INVENTORY.md`. Do not add additional memory files without explicit approval.
- Keep starter work under `templates/projects/**` and `templates/tasks/**`; do not leave duplicate root copies behind after moving or renaming starter content.
- Do not turn `HEARTBEAT.md` or `TOOLS.md` into long governance documents.
- `SOUL.md` at the repo root is a mandatory identity doc. Do not remove or rename it. Role-level `SOUL.md` files are approved only for `agents/senior-designer/SOUL.md`.

## DESIGN.md Maintenance Policy

`DESIGN.md` is produced by `/design-consultation` and serves as the design system source of truth. It is not a fire-and-forget artifact — it must stay current.

- Update `DESIGN.md` (via `/design-consultation` or manually) whenever a new component category is added to the design system
- Update it whenever a design-iteration project changes design system direction (new tokens, updated components, removed patterns)
- Run a full `/design-consultation` refresh at minimum once per quarter if the product is actively evolving
- A `DESIGN.md` that does not reflect what is actually built is worse than no `DESIGN.md` — it sends future design work in the wrong direction
- The Senior Designer is the owner of `DESIGN.md`. If it diverges from the implementation, update it before the next experience spec references it.

## Memory Decay Policy

Shared memory files must stay concise to remain useful across runs.

- `memory/session-history.md` — retain the last 90 days of entries. Remove older entries on the first Monday of each month.
- `memory/decisions.md` — entries older than 6 months with no active reference are marked `[ARCHIVED]` and moved to the bottom of the file. Review and prune on the first Monday of each month.
- `memory/PROJECT-INVENTORY.md` — shipped and cancelled projects older than 6 months are collapsed into an archive section at the bottom of the file.

Do not let memory files grow indefinitely. Large memory files slow recall and dilute signal.

## Doc Sync

When structure or startup behavior changes, update the affected root docs together:

- `SOUL.md` when company identity, non-negotiables, or scope discipline rules change
- `COMPANY.md` for canonical operating rules
- `README.md` for the public package summary
- `BOOTSTRAP.md` for first-run startup guidance
- `CONTRIBUTING.md` for package-maintenance rules
- `SKILL-ARCHITECTURE.md` when the approved capability surface changes
- `STACK.md` when the preferred stack changes, a layer decision is revised, or a new library enters or exits the default set
- `.paperclip.yaml` for runtime registration and cadence
