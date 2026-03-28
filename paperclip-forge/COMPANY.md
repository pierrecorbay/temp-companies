---
name: Paperclip Forge
description: Paperclip-native company that designs, audits, builds, and upgrades agent companies with explicit workflow design, referenced skills, and quality gates
slug: paperclip-forge
schema: agentcompanies/v1
version: 0.1.0
license: MIT
authors:
  - name: Pierre Corbay
goals:
  - Design new Paperclip-native companies that are structurally sound and minimally complex
  - Upgrade existing company packages without introducing drift, redundancy, or weak governance
  - Enforce two-layer verification so no unchecked work reaches the founder
  - Turn external best practices into reusable company structures, prompts, heartbeats, and review gates
tags:
  - paperclip
  - agent-companies
  - workflow-design
  - governance
---

Paperclip Forge is a compact meta-company for creating and improving Paperclip-native agent companies.

It operates as a strict pipeline with explicit quality gates:

1. **CEO** decides whether the engagement is "create a new company", "upgrade an existing company", or "stop because the complexity is not justified".
2. **Chief of Staff** reads the brief, source repo, and external references, then writes the project inventory and transformation brief.
3. **Workflow Designer** defines the org chart, reporting lines, mandatory files, handoffs, heartbeats, and definition-of-done rules.
4. **Skills Architect** decides which skills to reference, which conventions to impose, and which prompts, templates, or subagents must exist.
5. **Staff Engineer** scaffolds or patches the package, writes the manifests, and performs the producer-side self-check.
6. **Quality Auditor** audits the organization for contradictions, overlaps, missing gates, weak definitions of done, and drift risk.
7. **Code Reviewer** performs the final blocking review on the package changes before the CEO signs off.

## Operating Standards

- Two-layer verification is mandatory: the producing agent self-checks first, then the CEO validates before delivery.
- `PROJECT-INVENTORY.md` is mandatory before creating or upgrading a company.
- Idle is success. If there is no useful work to do, stop instead of manufacturing activity.
- Every agent must produce a concrete, checkable output and hand it off explicitly.
- Every correction should tighten the system: update instructions, log the change, and reduce future drift.

## Source Inputs

Paperclip Forge is informed by the Paperclip companies catalog, the AutoEDU Paperclip customization guide, and the Paperclip company playbook by Aron Prins.
