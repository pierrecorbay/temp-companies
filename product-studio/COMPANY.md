---
name: Product Studio
description: Lean engineering company powered by gstack workflow skills - distinct cognitive modes for product vision, design critique, technical planning, frontend/backend implementation, structural review, release, and QA
slug: product-studio
schema: agentcompanies/v1
version: 1.0.0
license: MIT
authors:
  - name: Pierre Corbay
  - name: Garry Tan
goals:
  - Ship software through explicit cognitive modes - founder taste, design critique, engineering rigor, paired implementation, structural review, release discipline, and systematic QA
  - Move ideas through a specialist pipeline where each stage produces the artifact the next stage needs
  - Preserve gstack's lean operator shape while adding enough workflow structure to reduce ambiguous handoffs and hidden ownership
---

Product Studio is a lean engineering company built around Garry Tan's gstack workflow skills. It operates as a gated pipeline with one intentional collaborative point: the build stage pairs `Senior Designer` and `Product Engineer` under `CTO` coordination so frontend and backend ownership stay explicit without adding a new role.

The company is intentionally narrow. It does not add extra governance roles or duplicate issue tracking in package docs. It does add the minimum workflow structure needed to keep ownership, startup, and review legible across repeated runs.

## Org Chart

`CEO -> Senior Designer -> CTO -> Product Engineer -> Staff Engineer -> Release Engineer -> QA Engineer`

Reporting structure:

- `CEO` manages `Senior Designer` and `CTO`
- `CTO` manages `Product Engineer`, `Staff Engineer`, `Release Engineer`, and `QA Engineer`

## Workflow Pattern

- Primary pattern: `pipeline`
- Why: Product Studio still benefits from deliberate cognitive mode changes more than from a standing collaborative team. Product framing, design, technical planning, review, release, and QA remain distinct stages.
- Pipeline shape:
  1. `CEO` frames the product brief
  2. `Senior Designer` turns the brief into an experience spec and names the frontend/design-system bar
  3. `CTO` converts the brief plus experience spec into the technical execution plan and opens the paired build stage
  4. `Senior Designer` implements frontend/UI/design-system slices while `Product Engineer` implements backend/app/integration slices on one shared review target
  5. `Staff Engineer` performs the structural review gate
  6. `Release Engineer` lands and ships the approved work
  7. `QA Engineer` verifies the shipped result and reports pass or fail back to `CTO`
- Re-entry rule: if design ambiguity appears after build starts, route back to `CTO`; if the ambiguity is product scope rather than execution detail, `CTO` escalates to `CEO`
- Completion rule: shipped work is not complete until `QA Engineer` issues a pass/fail report and `CTO` routes any follow-up explicitly

## Approved Fallback Coverage

Fallbacks preserve routing continuity only. They do not create shared ownership and they do not waive required gates.

| Role | Primary Owner | Approved Fallback | Fallback Limit |
| --- | --- | --- | --- |
| CEO | `CEO` | `Founder` (human) | If the CEO is blocked or unavailable, escalate to the human founder. No agent can substitute for CEO scope authority. |
| Senior Designer | `Senior Designer` | `CTO` | `CTO` may narrow or reroute frontend/design-system work, but may not replace missing UX decisions with ad hoc implementation guesses |
| CTO | `CTO` | `CEO` | `CEO` may reset priorities or clarify scope, but may not waive review, release, or QA gates |
| Product Engineer | `Product Engineer` | `CTO` | `CTO` may narrow or reroute implementation work, but may not replace code delivery with plan prose |
| Staff Engineer | `Staff Engineer` | `CTO` | `CTO` may hold or reroute review work, but may not treat a missing review verdict as passed |
| Release Engineer | `Release Engineer` | `CTO` | `CTO` may hold shipment or reassign operational work, but may not mark release work complete without a release artifact |
| QA Engineer | `QA Engineer` | `CTO` | `CTO` may hold or reroute follow-up, but may not convert missing QA evidence into a pass |

## Idle-Is-Success Rule

An empty backlog is a success state, not a problem. Agents must not self-generate tasks, projects, or busywork to fill idle time. New tasks and projects originate from the CEO — and only after the CEO's Pre-Creation Gate passes. If no gate-passing work exists, the correct action is to wait. Filling a healthy backlog with low-value work is a governance failure.

## Canonical Package Surface

Product Studio keeps the mandatory package surface lean, but the surface is now explicit.

Mandatory file classes:

- Root operating docs: `COMPANY.md`, `README.md`, `BOOTSTRAP.md`, `CONTRIBUTING.md`, `SKILL-ARCHITECTURE.md`, `.paperclip.yaml`, `SOUL.md`
- Role runtime contract: `agents/<role>/AGENTS.md`, `agents/<role>/HEARTBEAT.md`, `agents/<role>/TOOLS.md`
- Shared workflow memory: `memory/session-history.md`, `memory/decisions.md`, `memory/PROJECT-INVENTORY.md`
- Workflow templates: `templates/HANDOFF.md`, `templates/AGENT-PROMPT-CHECKLIST.md`
- Starter surfaces: `templates/projects/**`, `templates/tasks/**`, `teams/**`
- Capability surface: `skills/**`

File-class controls:

| File Class | Controls |
| --- | --- |
| `SOUL.md` | Company identity: what Product Studio is, what it is not, product and design non-negotiables, scope discipline rules, identity check |
| `COMPANY.md` | Org chart, workflow pattern, fallback coverage, mandatory file classes, handoff gates, and company-wide definition of done |
| `README.md` | Public package overview, role inventory, workflow summary, and starter-surface explanation |
| `BOOTSTRAP.md` | First-run startup protocol for an imported or newly upgraded Product Studio package |
| `CONTRIBUTING.md` | Change rules, file-class expectations, and package-maintenance guidance |
| `SKILL-ARCHITECTURE.md` | Top-level map of the 22-skill surface, role ownership, and where each skill enters the workflow |
| `.paperclip.yaml` | Runtime cadence, agent registration, branding, capabilities, adapter settings, permissions, and sidebar ordering |
| `agents/<role>/AGENTS.md` | Role contract: trigger, output, handoff, fallback, and anti-pattern rules |
| `agents/<role>/HEARTBEAT.md` | Lightweight repeated checklist for the role's recurring execution loop |
| `agents/<role>/TOOLS.md` | Approved skills and tools for the role's normal work |
| `memory/session-history.md` | Cross-run summary of issue decisions, outcomes, and lessons worth recalling |
| `memory/decisions.md` | Durable product, design, and technical decisions that later stages must preserve |
| `memory/PROJECT-INVENTORY.md` | Index of all active, paused, and shipped projects; CEO reads first at every heartbeat before creating new work |
| `templates/HANDOFF.md` | Canonical handoff shape for Product Studio issue comments and local packets |
| `templates/AGENT-PROMPT-CHECKLIST.md` | Canonical checklist for keeping role prompts aligned with the active workflow surface |
| `templates/projects/**`, `templates/tasks/**` | Reusable starter project and task scaffolds |
| `teams/**` | Live team and org scaffolding |
| `skills/**` | Vendored or referenced workflow skills that define each specialist mode |

Optional support assets:

- `references/**`
- `images/**`
- `*-HANDOFF.md`
- `templates/BOOTSTRAP.md` only if the package later needs a generator-owned source distinct from the runtime root bootstrap

## Role Contracts

Every role must have an upstream trigger, a concrete output, an explicit handoff, and a blocking gate that prevents ambiguous completion.

| Role | Upstream Trigger | Concrete Output | Explicit Handoff | Blocking Gate |
| --- | --- | --- | --- | --- |
| `CEO` | New request, scope dispute, or launch-direction question | Product brief with user, scope, non-goals, success bar, key risks, activation metric, distribution vector, retention mechanic, and delight moment | `Senior Designer` | Design does not start until the brief states what matters, what does not, and how the product will grow and retain B2C users |
| `Senior Designer` | Approved product brief, then `CTO`-opened frontend build scope | Experience spec plus owned frontend/design-system implementation slice | `CTO` for planning, then `Staff Engineer` through the shared build artifact | Technical planning and review both block until UI behavior and owned frontend scope are explicit and reviewable |
| `CTO` | Product brief plus experience spec | Technical execution plan with architecture, phase split, frontend/backend boundaries, integration points, and test bar | Paired build stage: `Senior Designer` plus `Product Engineer` | Build does not start until execution boundaries and review expectations are explicit |
| `Product Engineer` | Locked technical execution plan plus frontend contract from the paired build stage | Backend/application implementation slice with tests, integration notes, and known risks | `Staff Engineer` through the shared build artifact | Review does not start until backend/integration work is locally verified and attached to the shared review target |
| `Staff Engineer` | Shared reviewable artifact from the paired build stage | Approve-or-fix review verdict with concrete structural findings or residual risk | `Release Engineer` on approval, or back to the paired build stage on failure | No release handoff without an explicit review verdict |
| `Release Engineer` | Approved structural review verdict | Shipped change plus release context for QA | `QA Engineer` | QA does not start until the target environment, expected behavior, and risk areas are named |
| `QA Engineer` | Release handoff with environment context | Pass/fail verification report with evidence and residual risks | `CTO` | Work does not close until `CTO` receives a clear QA verdict and routes follow-up explicitly |

## Heartbeat Expectations

Each role gets a lightweight heartbeat contract. Heartbeats are for repeated execution checks, not policy duplication.

| Role | Required Heartbeat Checks |
| --- | --- |
| `CEO` | Confirm the active brief is still the right problem, the right scope, and the right next owner |
| `Senior Designer` | Confirm the brief is current, keep the experience spec aligned with implementation, and update the owned frontend/design-system slice when the paired build stage is active |
| `CTO` | Confirm the brief and experience spec still align, keep the execution plan current, and keep frontend/backend ownership boundaries explicit |
| `Product Engineer` | Confirm implementation still matches the approved plan, integrate against the frontend contract, capture local verification notes, and surface blockers early |
| `Staff Engineer` | Confirm the shared build artifact matches the plan, issue an approve-or-fix verdict, and name release blockers concretely |
| `Release Engineer` | Confirm the review gate passed, complete the release steps, and give QA exact verification context |
| `QA Engineer` | Confirm the target environment and expected behavior, run the required verification mode, and emit evidence-backed pass/fail results |

CEO-specific coordination delta for this package:

- the CEO heartbeat should explicitly require `inbox-lite` for assignment checks, `heartbeat-context` before replaying full issue history, incremental comment reads when warm, `X-Paperclip-Run-Id` on mutating issue calls, and an API-backed handoff comment that names `Skills used:`
- this issue does not approve copying Forge's full CEO governance checklist or adding Product Studio memory-governance steps beyond the package's existing lean memory surface

## Quality Gates And Handoffs

Delivery gates:

1. Brief gate: `CEO` publishes the product brief.
2. Experience gate: `Senior Designer` publishes the experience spec and frontend acceptance bar.
3. Technical gate: `CTO` publishes the execution plan with explicit frontend/backend ownership.
4. Paired build gate: `Senior Designer` and `Product Engineer` produce one shared reviewable artifact with both owned slices and local verification notes.
5. Structural review gate: `Staff Engineer` issues an explicit approve-or-fix verdict.
6. Release gate: `Release Engineer` ships the reviewed work and hands QA the exact release context.
7. QA gate: `QA Engineer` issues a pass/fail report with evidence.
8. Closeout gate: `CTO` closes the issue or routes regressions back to the correct specialist. `CEO` re-enters only when scope or launch ambition must change.

Handoff rules:

- every handoff names the next owner or the paired build stage explicitly
- every handoff links or names the concrete artifact being handed off
- the paired build stage must end in one shared review target, not separate frontend and backend submissions
- a role is not done with prose alone when the next role needs a file, branch, environment, review verdict, or verification report
- if a gate fails, route backward to the role that can fix it instead of skipping forward

## Bootstrap Placement

Product Studio uses one canonical startup artifact: repo-root `BOOTSTRAP.md`.

`BOOTSTRAP.md` must cover:

- what a newly imported company should read first
- the delivery pipeline in order
- which root docs, template files, memory files, and role contracts must exist before assigning work
- how to start from `templates/projects/**` or `templates/tasks/**` without guessing

Do not mirror bootstrap into `templates/` in this round unless the package later needs a generator-owned source distinct from the runtime-facing root document.

## Document Reference Conventions

Document classes stay simple and file-class based:

- root docs are canonical operating rules and may be referenced directly by filename
- `agents/` files are runtime contracts for a specific role
- `memory/` files are shared continuity artifacts and must stay concise, append-only, and cross-role
- `templates/HANDOFF.md` and `templates/AGENT-PROMPT-CHECKLIST.md` are canonical local workflow templates
- `templates/projects/**` and `templates/tasks/**` are reusable starter content, not live issue-state mirrors
- `teams/**` describes the live org scaffold
- `skills/**` are capability assets; they support execution but do not override workflow ownership in `COMPANY.md`
- `references/**` are optional research anchors and do not override canonical docs
- `*-HANDOFF.md` files are transient packets tied to one stage handoff and must name the upstream stage plus downstream owner in the document body
- adding a new file class without documenting its purpose in `COMPANY.md` or `CONTRIBUTING.md` is invalid structural work

## Definition of Done: Experience Spec Locked

The experience spec is locked — and the CTO may open the technical planning stage — only when ALL of the following are explicitly documented:

1. **Primary flows** — happy path with all branching points named
2. **Error states** — one per meaningful failure mode
3. **Empty states** — first-run, zero-data, and post-delete
4. **Loading / transition states** — for every async operation
5. **Interaction states** — hover, focus, active, disabled for every interactive element
6. **Design-system direction** — which existing components apply, which new ones are introduced, token references
7. **Platform matrix** — breakpoints, platforms, and any native vs. web distinctions
8. **Acceptance bar** — what must be true for the CTO to call the frontend slice done
9. **Onboarding flow** — the complete new-user journey from cold start: entry point, first-run empty state, first action prompt, and the activation moment that delivers the first unit of value. This is a distinct flow from the primary feature flow and is required for every B2C release.

If any of these nine items is missing, the spec is not locked. The CTO does not start planning. The paired build stage does not open.

## Definition Of Done Framework

A role is done only when all of the following are true:

- the upstream trigger actually occurred
- the role updated or produced the concrete artifact its stage owns
- the next owner or paired build stage is explicit
- the stage's blocking gate is satisfied or the work is routed backward with a concrete blocker
- any residual risk the next role must watch is stated directly in the handoff
- the role did not silently replace a required artifact with summary prose

Completion is invalid if the next stage still has to guess the problem, the expected behavior, the frontend/backend split, the review verdict, the release target, or the verification result.
