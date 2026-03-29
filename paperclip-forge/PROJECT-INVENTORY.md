# Project Inventory: Paperclip Forge Self-Upgrade

## Engagement Mode

- `upgrade-existing-company`
  - **Reason**: Modifying and stabilizing the current `paperclip-forge-company-template` package rather than building from zero.

## Existing Inputs

- **User brief**: Audit current Paperclip Forge package and produce self-upgrade brief.
- **Existing company repo**: Local `paperclip-forge-company-template` directory.
- **Source companies used as patterns**: Internal Paperclip Forge definitions, existing `.paperclip.yaml`, `COMPANY.md`, and agent/skill stubs.
- **External guides and playbooks**: Paperclip companies catalog, AutoEDU customization guide, Paperclip playbook by Aron Prins, found in `references/core-ressources.md`

## Inventory Checklist

### What already exists?
- **Core Manifests**: `COMPANY.md`, `README.md`, `.paperclip.yaml`, `PROJECT-INVENTORY.md`, `SKILL-ARCHITECTURE.md`, `CONTRIBUTING.md`.
- **Agents**: `ceo`, `chief-of-staff`, `workflow-designer`, `skills-architect`, `staff-engineer`, `quality-auditor`, `code-reviewer` (7 total).
- **Skills Surface**: Exactly 22 referenced skills inside `skills/` directly mapping to `SKILL-ARCHITECTURE.md`.
- **Templates**: `templates/HANDOFF.md`, `templates/AGENT-PROMPT-CHECKLIST.md`.

### What is missing, weak, redundant, or unclear?
1. **Workflow Rigidity Risk**: The structural path is intentionally strict; teams must keep using the documented fast-path for trivial updates to avoid unnecessary 7-step routing.

## Change Log

For every correction, record:

- What changed
- Why it changed
- Which instruction or template was tightened
- How future drift will be detected
