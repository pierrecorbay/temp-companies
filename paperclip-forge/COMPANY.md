---
name: Paperclip Forge
description: Paperclip-native company that designs, audits, builds, and upgrades agent companies with explicit workflow design, referenced skills, and quality gates
slug: paperclip-forge
schema: agentcompanies/v1
version: 1.0.0
license: MIT
authors:
  - name: Pierre Corbay
goals:
  - Design structurally sound, minimally complex Paperclip-native companies
  - Upgrade existing company packages without introducing drift or weak governance
  - Enforce explicit verification so no unchecked work reaches the founder
  - Turn external best practices into reusable company structures, prompts, heartbeats, and review gates
tags:
  - paperclip
  - agent-companies
  - workflow-design
  - governance
---

Paperclip Forge is a compact meta-company for creating and improving Paperclip-native agent companies.

It operates with a **Flattened Pipeline** structure and explicit API-driven handoffs to ensure quality without unnecessary latency. To avoid the overhead of a deep 7-step waterfall for every task, we use two explicit workflows:

### 1. The Structural Path (Full Pipeline)
For creating new companies, major upgrades, or structural changes:
`CEO -> Chief of Staff -> Workflow Designer -> Skills Architect -> Staff Engineer -> Quality Auditor -> Code Reviewer -> CEO`

1. **CEO** acts as the front door. Decides whether the engagement is "create a new company", "upgrade an existing company", or "stop".
2. **Chief of Staff** reads the brief, source repo, and external references, then writes the project inventory and transformation brief.
3. **Workflow Designer** defines the org chart, reporting lines, mandatory files, explicit handoffs, heartbeats, and definition-of-done rules.
4. **Skills Architect** decides which skills to reference, which conventions to impose, and which prompts, templates, or subagents must exist.
5. **Staff Engineer** scaffolds or patches the package, writes the manifests, and performs the producer-side self-check.
6. **Quality Auditor** audits the organization for contradictions, overlaps, missing gates, weak definitions of done, and drift risk.
7. **Code Reviewer** performs the final blocking review before CEO sign-off.

### 2. The Fast-Path (Trivial Updates)
For trivial bug fixes, prompt tweaks, or simple code adjustments where structural design is not needed:
`CEO -> Staff Engineer -> Code Reviewer -> CEO`

- The CEO assigns directly to the Staff Engineer.
- The Staff Engineer implements the change and hands off directly to the Code Reviewer.
- The Code Reviewer verifies the change and hands off to the CEO.

## Reporting Structure

- **CEO** manages the Chief of Staff, Quality Auditor, and Code Reviewer.
- **Chief of Staff** manages the Workflow Designer.
- **Workflow Designer** manages the Skills Architect and Staff Engineer.

## Operating Standards

- **API-Driven Handoffs:** Handoffs must use explicit Paperclip API calls (`POST /api/issues/{issueId}/checkout`, `PATCH /api/issues/{issueId}` with `assigneeAgentId`) instead of just verbal instructions.
- Three-layer verification is mandatory for structural changes: the producing agent self-checks first, then Quality Auditor validates structure, then Code Reviewer validates final blocking correctness before delivery to CEO. Two-layer verification is used for the fast-path.
- `PROJECT-INVENTORY.md` is mandatory before creating or upgrading a company (Structural Path).
- `SKILL-ARCHITECTURE.md` and the files in `templates/` define the local capability and handoff rules that referenced skills must follow.
- Idle is success. If there is no useful work to do, stop instead of manufacturing activity.
- Every agent must produce a concrete, checkable output and hand it off explicitly.
- Every correction should tighten the system: update instructions, log the change, and reduce future drift.
