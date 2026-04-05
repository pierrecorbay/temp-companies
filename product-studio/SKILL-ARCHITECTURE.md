# Skill Architecture

This document is Product Studio's capability contract.

It keeps the local skill surface, prompt rules, handoff shape, and shared memory small and tied to the actual delivery pipeline in `COMPANY.md`.

## Locked Capability Decisions

- Keep all 23 vendored gstack workflow skills as local package assets under `skills/`.
- The approved skill surface is 25 skills. `autoplan` was added for CEO/CTO fast-path combined review. `find-docs` was added for CTO/Product Engineer live library documentation. `researcher` was added for Product Engineer measurable-metric optimization work.
- Treat `paperclip` as a runtime platform skill rather than part of the 22-skill Product Studio workflow count.
- Add only three local capability assets in this round: `SKILL-ARCHITECTURE.md`, `templates/HANDOFF.md`, and `templates/AGENT-PROMPT-CHECKLIST.md`.
- Keep startup guidance root-only. `BOOTSTRAP.md` stays the canonical startup artifact; do not add `templates/BOOTSTRAP.md` in this round.
- Keep shared workflow memory lean: only `memory/session-history.md` and `memory/decisions.md` are approved.
- Keep one primary Paperclip assignee per issue. For the paired build stage, the assignee is `Product Engineer`; `Senior Designer` must still be named as the required paired frontend owner, and `CTO` remains the coordinating owner.

## Skill Surface Decision

All workflow skills stay local.

| Skill | Decision | Primary Owner | Approved Users | Workflow Step | Why It Exists |
| --- | --- | --- | --- | --- | --- |
| `autoplan` | Keep local | `CEO` | `CEO`, `CTO` | Plan fast-track | Runs CEO, design, and eng reviews in one automated pass. CEO uses it before committing to the full pipeline; CTO uses it for multi-lens validation before opening the paired build stage. |
| `find-docs` | Keep local | `CTO` | `CTO`, `Product Engineer` | Library documentation lookup | Retrieves up-to-date API docs via Context7 CLI before architecture decisions or library-specific implementation. Prevents deprecated-API bugs. |
| `researcher` | Keep local | `Product Engineer` | `Product Engineer` | Optimization experimentation | Autonomous experiment loop for measurable-metric optimization (LCP, bundle size, query time). Not for feature-building. |
| `office-hours` | Keep local | `CEO` | `CEO` | Brief framing | Forces product thinking before the company commits to a build. |
| `plan-ceo-review` | Keep local | `CEO` | `CEO` | Executive review | Gives the CEO a structured quality bar for scope and ambition decisions. |
| `design-consultation` | Keep local | `Senior Designer` | `Senior Designer` | Experience spec | Anchors flows, interaction states, and design-system direction. |
| `plan-design-review` | Keep local | `Senior Designer` | `Senior Designer` | Experience-spec review | Prevents weak or underspecified UX handoffs from reaching planning. |
| `design-review` | Keep local | `Senior Designer` | `Senior Designer`, `QA Engineer` | Experience QA | Keeps visual and interaction quality explicit before and after release. |
| `browse` | Keep local | `QA Engineer` | `QA Engineer`, `Senior Designer` | Research and live verification | Supports live-product inspection, reproduction, and browser-based QA work. |
| `plan-eng-review` | Keep local | `CTO` | `CTO` | Technical planning | Forces architecture, risk, and test expectations to become explicit before build starts. |
| `cso` | Keep local | `CTO` | `CTO` | Security planning | Keeps trust boundaries and security risks visible in the execution plan. |
| `retro` | Keep local | `CTO` | `CTO` | Delivery learning | Preserves the engineering-retrospective mode without expanding the runtime surface. |
| `investigate` | Keep local | `Product Engineer` | `Product Engineer`, `Staff Engineer` | Implementation and review debugging | Prevents speculative fixes and supports root-cause analysis when delivery gets stuck. |
| `codex` | Keep local | `Staff Engineer` | `Staff Engineer`, `Product Engineer` | Second-opinion engineering checks | Adds a bounded challenger mode for risky implementation or review calls. |
| `guard` | Keep local | `Product Engineer` | `Product Engineer` | Implementation safety | Keeps product implementation focused and reduces destructive or scope-widening edits. |
| `review` | Keep local | `Staff Engineer` | `Staff Engineer` | Structural review | Powers the explicit approve-or-fix gate before release. |
| `ship` | Keep local | `Release Engineer` | `Release Engineer` | Release prep | Supports the controlled landing workflow once structural review passes. |
| `land-and-deploy` | Keep local | `Release Engineer` | `Release Engineer` | Deployment | Turns the approved branch into an actual shipped target. |
| `document-release` | Keep local | `Release Engineer` | `Release Engineer` | Release documentation | Keeps release-facing docs aligned with what shipped. |
| `setup-deploy` | Keep local | `Release Engineer` | `Release Engineer` | Deployment setup | Covers one-time deployment setup without inventing a new role. |
| `qa` | Keep local | `QA Engineer` | `QA Engineer` | Verification | Provides the primary pass/fail QA mode for shipped work. |
| `qa-only` | Keep local | `QA Engineer` | `QA Engineer` | Report-only verification | Allows non-mutating QA passes when the goal is evidence, not fixing. |
| `benchmark` | Keep local | `QA Engineer` | `QA Engineer` | Performance verification | Makes performance regressions part of the QA gate rather than a silent follow-up. |
| `canary` | Keep local | `QA Engineer` | `QA Engineer` | Post-release monitoring | Keeps live regression checks tied to the QA/release end of the pipeline. |
| `setup-browser-cookies` | Keep local | `QA Engineer` | `QA Engineer` | Authenticated QA setup | Supports realistic browser verification when auth or saved state matters. |

## Local Capability Assets

| Asset | Owner | Used By | Why It Exists |
| --- | --- | --- | --- |
| `SKILL-ARCHITECTURE.md` | `Skills Architect` | `CTO`, `Staff Engineer`, reviewers | Maps the 22-skill surface to real workflow steps and prevents silent sprawl. |
| `templates/HANDOFF.md` | `Skills Architect` | All roles | Gives Product Studio one canonical handoff shape, including the paired build exception. |
| `templates/AGENT-PROMPT-CHECKLIST.md` | `Skills Architect` | `Skills Architect`, `Staff Engineer` | Keeps prompt edits aligned with the active skill surface and paired-build workflow. |
| `memory/session-history.md` | All roles | All roles | Preserves issue-chain context so the team does not re-litigate the same call every heartbeat. |
| `memory/decisions.md` | `CTO` | `Senior Designer`, `Product Engineer`, `Staff Engineer`, `QA Engineer` | Stores durable product, design, and technical decisions that later stages must preserve. |

## Local Rules Beyond Skills

The vendored gstack skills do not know Product Studio's workflow-specific rules. These rules are local and must stay local:

- the paired build stage needs one assignee plus two named owners
- fallback coverage must stay routing-only
- only two shared memory files are approved
- startup guidance stays in root `BOOTSTRAP.md`, not a mirrored template
- starter work must live under `templates/projects/**` and `templates/tasks/**`
- role prompts must stay short, stage-specific, and tied to the actual artifact the next stage needs
- CEO Paperclip coordination rules belong in `agents/ceo/HEARTBEAT.md`, not in a company-wide governance template or a skill-surface expansion

## Handoff Rules

Use [templates/HANDOFF.md](templates/HANDOFF.md).

Required rules:

- Every handoff names the concrete artifact being handed off.
- Every handoff names the next owner explicitly.
- The only approved multi-owner exception is the `CTO` to paired-build handoff.
- For that paired-build handoff:
  - assign the issue to `Product Engineer`
  - name `Senior Designer` as the required paired frontend/design-system owner
  - name `CTO` as coordinating owner only
  - name the shared review target that `Staff Engineer` will receive
- Every handoff includes `Skills used:` so later reviewers can tell whether the role stayed within the approved surface.
- If the blocker is scope or ambition, route to `CEO`. If the blocker is execution or split ownership, route to `CTO`.

## Prompt Rules

- Keep one upstream trigger, one owned artifact, and one default downstream handoff per prompt.
- Keep fallback coverage in its own line or section; it is not shared ownership.
- `Senior Designer` must explicitly cover both experience-spec work and frontend/design-system implementation during the paired build stage.
- `CTO` must explicitly open the paired build stage and name the frontend/backend ownership split.
- `Product Engineer` must treat the `Senior Designer` contract as a required input, not optional context.
- `Staff Engineer` must issue an approve-or-fix verdict, not a vague review summary.
- `Release Engineer` must hand `QA Engineer` an exact environment and risk context.
- `QA Engineer` must return a pass/fail report with evidence to `CTO`.

## Deferred Or Rejected Surface

| Item | Decision | Why |
| --- | --- | --- |
| `templates/BOOTSTRAP.md` | Defer | Product Studio keeps one canonical startup artifact at repo root in this round. |
| Extra shared-memory files such as `memory/corrections.md` or `memory/autonomy-log.md` | Reject | The approved delta only needs session continuity and durable decisions. |
| Additional workflow skills beyond the approved 23 | Reject unless explicitly approved | The workflow problem is handoff clarity, not missing execution modes. |
| A Product Studio `PROJECT-INVENTORY.md` | Reject | Issue intake stays in Paperclip and does not need a mirrored package doc. |

## Anti-Drift Rules

- If a prompt change adds a skill, update this file first or in the same patch.
- If a handoff comment makes the paired build stage sound like vague collaboration, tighten `templates/HANDOFF.md` in the same patch.
- If a prompt starts referencing memory, it may name only `memory/session-history.md`, `memory/decisions.md`, and `memory/PROJECT-INVENTORY.md`.
- If startup guidance changes, update root `BOOTSTRAP.md`; do not invent `templates/BOOTSTRAP.md` unless a later issue explicitly approves it.
- If starter work is moved or renamed, keep `templates/projects/**` and `templates/tasks/**` aligned with `README.md`, `CONTRIBUTING.md`, and `BOOTSTRAP.md`.
