# Paperclip Forge

Paperclip Forge is an [Agent Company](https://agentcompanies.io/specification) for designing, auditing, building, and upgrading Paperclip-native companies. It is optimized for one specific class of work: turning company ideas, repo audits, and best-practice research into a coherent Paperclip package with clear reporting lines, reusable skills, mandatory files, and hard quality gates.

This package is built for [Paperclip](https://github.com/paperclipai/paperclip) and draws its operating model from:

- [paperclipai/companies](https://github.com/paperclipai/companies)
- [Paperclip Beyond Defaults](https://autoedu.ai/resources/paperclip-customization-guide)
- [paperclip-company-playbook](https://github.com/aronprins/paperclip-company-playbook)

## Workflow

Paperclip Forge runs a pipeline, not an open-ended swarm:

1. The CEO decides whether to create a new company, upgrade an existing one, or reject unnecessary complexity.
2. The Chief of Staff produces the intake brief, project inventory, and source synthesis.
3. The Workflow Designer defines the org chart, mandatory files, gates, heartbeat, and handoff logic.
4. The Skills Architect defines the skill map, prompt conventions, templates, and anti-drift rules.
5. The Staff Engineer implements the package and performs the producer-side self-check.
6. The Quality Auditor checks for structural issues and incomplete governance.
7. The Code Reviewer blocks or approves the final package before CEO signoff.

## Org Chart

| Agent | Title | Reports To | Primary Skills |
| --- | --- | --- | --- |
| CEO | Chief Executive Officer | - | `autoplan`, `plan-ceo-review` |
| Chief of Staff | Chief of Staff | CEO | `browse`, `create-plans`, `context-handoff` |
| Workflow Designer | Workflow Designer | Chief of Staff | `create-plans`, `plan-eng-review`, `context-handoff`, `meta-prompting` |
| Skills Architect | Skills Architect | Workflow Designer | `create-agent-skills`, `create-meta-prompts`, `create-subagents`, `meta-prompting` |
| Staff Engineer | Staff Engineer | Workflow Designer | `company-creator`, `investigate`, `ship`, `document-release` |
| Quality Auditor | Quality Auditor | CEO | `review`, `qa`, `qa-only` |
| Code Reviewer | Senior Code Reviewer | CEO | `pragmatic-code-review` |

## Agent Roles

- **CEO** is the final quality gate. This role does not relay unchecked work.
- **Chief of Staff** turns a request, repo, and references into a clean starting brief.
- **Workflow Designer** defines how work moves through the company and what must exist before delivery.
- **Skills Architect** shapes the capability layer: skill references, prompts, templates, and handoffs.
- **Staff Engineer** writes or patches the actual package.
- **Quality Auditor** looks for systemic problems, not style nits.
- **Code Reviewer** runs the final blocking review before delivery.

Reporting structure:

- The CEO manages the Chief of Staff, Quality Auditor, and Code Reviewer.
- The Chief of Staff manages the Workflow Designer.
- The Workflow Designer manages the Skills Architect and Staff Engineer.

## Package Contents

- `COMPANY.md` for the company manifest and operating model
- `PROJECT-INVENTORY.md` and `CONTRIBUTING.md` for anti-drift governance
- `agents/*` for role instructions and heartbeat files
- `projects/initial-company-build/PROJECT.md` for the starter project
- `tasks/create-new-company/TASK.md` and `tasks/upgrade-existing-company/TASK.md` for the two default engagement modes
- `skills/*` as referenced skill stubs pinned to the Paperclip companies catalog

## Getting Started

Import the package with Paperclip:

```bash
paperclipai company import --from /Users/pierrecorbay/Paperclip/companies/paperclip-forge
```

Then open one of the starter tasks or assign a new company engagement to the CEO.
