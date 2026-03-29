# Skill Architecture

This document is the local capability contract for Paperclip Forge v1.

Referenced skills stay thin and pinned upstream. Local rules live here when the company needs a sharper constraint than the upstream skill provides.

## Design Rules

- Prefer referenced skills over local forks unless Paperclip Forge needs a company-specific rule.
- Keep each agent on the minimum skill set that directly supports its workflow step.
- Use local templates for handoffs and prompt structure; referenced skills must not redefine the company handoff format.
- Remove overlapping skills once one referenced skill plus a local convention covers the job.
- Keep the structural-path dual review gate explicit: `quality-auditor` structural audit followed by `code-reviewer` final blocking review.
- Keep the fast-path thin: only `staff-engineer` and `code-reviewer` participate unless the change becomes structural.
- Never delete anything from `~/.claude/skills`

## Skill Map

| Agent | Skills | Reason |
| --- | --- | --- |
| CEO | `autoplan`, `plan-ceo-review` | Final scope and approval decisions. |
| Chief of Staff | `browse`, `create-plans`, `context-handoff`, `researcher` | Intake, source synthesis, and clean upstream packet creation. |
| Workflow Designer | `create-plans`, `plan-eng-review`,  `context-handoff` | Org design, workflow rigor, and gate definition. |
| Skills Architect | `autoresearch`, `create-agent-skills`, `create-meta-prompts`, `create-subagents`, `researcher` | Skill decisions, prompt conventions, and capability boundaries. |
| Staff Engineer | `company-creator`, `investigate`, `document-release` | Package implementation on both the structural path and the fast-path, plus debugging and doc sync. |
| Quality Auditor | `review`, `qa`, `qa-only` | Structural audit and report-only QA validation before final review. |
| Code Reviewer | `pragmatic-code-review` | Final blocking review on both the structural path and the fast-path before CEO signoff. |

## Referenced Skill Inventory

Every referenced skill must have one primary owning role and one concrete place in the pipeline.

| Skill | Primary Owner | Workflow Step | Why It Exists |
| --- | --- | --- | --- |
| `autoplan` | CEO | Engagement start and final routing | Lets the CEO turn a user request into an explicit execution path instead of ad hoc delegation. |
| `plan-ceo-review` | CEO | Final approval | Gives the CEO a consistent decision frame for approve, return, or stop. |
| `browse` | Chief of Staff | Intake research | Supports source reading during upgrade or greenfield intake without inventing local research process. |
| `create-plans` | Chief of Staff, Workflow Designer | Intake briefing and workflow design | Covers structured planning work for the first two design stages. |
| `context-handoff` | Chief of Staff | Intake packet delivery | Helps compress source context before the workflow stage begins. |
| `autoresearch` | Chief of Staff | TBD | TBD |
| `plan-eng-review` | Workflow Designer | Operating design review | Keeps workflow decisions concrete enough for engineering implementation. |
| `autoresearch` | Skills Architect | TBD | TBD |
| `create-agent-skills` | Skills Architect | Capability design | Supports decisions about what skills exist and how they should be scoped. |
| `create-meta-prompts` | Skills Architect | Prompt convention design | Covers reusable prompt structures without needing a local prompt-generation fork. |
| `create-subagents` | Skills Architect | Capability escalation design | Used only when the workflow genuinely needs delegated sub-agent patterns. |
| `company-creator` | Staff Engineer | Structural-path and fast-path implementation | Scaffolds or patches the company package itself. |
| `investigate` | Staff Engineer | Structural-path and fast-path verification | Supports targeted debugging and structural checks during implementation. |
| `document-release` | Staff Engineer | Structural-path and fast-path doc sync | Keeps release-facing docs in sync with the implemented package. |
| `review` | Quality Auditor | Structural audit | Provides the structural package audit across files, roles, and gates. |
| `qa` | Quality Auditor | Broad quality validation | Adds systematic QA coverage for package-level risks beyond file-local review. |
| `qa-only` | Quality Auditor | Report-only audit passes | Enforces non-mutating audit behavior when an explicit report-only pass is required. |
| `pragmatic-code-review` | Code Reviewer | Final changed-file review on both workflows | Ensures file-level correctness, regression checks, and review discipline at the final gate. |

## Local Capability Assets

| Asset | Owner | Used By | Reason |
| --- | --- | --- | --- |
| `SKILL-ARCHITECTURE.md` | Skills Architect | Workflow Designer, Skills Architect, Staff Engineer, CEO | Authoritative contract for skill ownership, removals, and anti-drift rules. |
| `templates/HANDOFF.md` | Skills Architect | All agents | Forces one primary next assignee, explicit constraints, and API-based reassignment. |
| `templates/AGENT-PROMPT-CHECKLIST.md` | Skills Architect | Workflow Designer, Skills Architect, Staff Engineer | Keeps role prompts aligned to the lean pipeline before they land in `AGENTS.md`. |

## Local Prompt Conventions

Every `AGENTS.md` should keep this shape:

1. Role statement
2. Where work comes from
3. What you do
4. What you produce
5. Who you hand off to
6. What triggers you
7. Definition of done

Additional local rules:

- Each role should name one primary next assignee. Escalation paths may be listed separately, but they must not replace the primary handoff.
- "Hand off" language must be paired with the exact output being handed off.
- Definitions of done must be checkable from files, diffs, or explicit review findings.
- Skills listed in frontmatter must map to work the role performs repeatedly, not hypothetically.

## Handoff Pattern

Use the template in [templates/HANDOFF.md](/Users/pierrecorbay/Paperclip/paperclip-forge/paperclip-forge-company-template/templates/HANDOFF.md).

The structural path is:

1. CEO -> Chief of Staff
2. Chief of Staff -> Workflow Designer
3. Workflow Designer -> Skills Architect
4. Skills Architect -> Staff Engineer
5. Staff Engineer -> Quality Auditor
6. Quality Auditor -> Code Reviewer
7. Code Reviewer -> CEO

The fast-path is:

1. CEO -> Staff Engineer
2. Staff Engineer -> Code Reviewer
3. Code Reviewer -> CEO

The CEO may interrupt or reroute work, but each handoff should stay on one of these two paths instead of inventing an ad hoc route.

Every handoff must include:

- one primary downstream assignee
- links to the concrete files or issue documents that changed
- the constraint or risk the next agent must preserve
- an executed Paperclip API reassignment, not prose alone

## Local Requirements Beyond Referenced Skills

Referenced skills are not enough for three company-specific needs:

- Paperclip API handoffs must be explicit and consistent across agents.
- Agent prompts must stay structurally aligned with the lean pipeline.
- The structural-path review sequence and the fast-path skip rules must both stay explicit.

These are handled locally through:

- [templates/HANDOFF.md](/Users/pierrecorbay/Paperclip/paperclip-forge/paperclip-forge-company-template/templates/HANDOFF.md)
- [templates/AGENT-PROMPT-CHECKLIST.md](/Users/pierrecorbay/Paperclip/paperclip-forge/paperclip-forge-company-template/templates/AGENT-PROMPT-CHECKLIST.md)
- this `SKILL-ARCHITECTURE.md`

Ownership stays with the Skills Architect unless the workflow itself changes. Workflow-level changes go back to the Workflow Designer before the Staff Engineer implements them.

## Anti-Drift Rules

- If a new skill is proposed, name the agent, repeated task, and failure mode the current surface cannot cover.
- If a correction repeats twice, tighten either a heartbeat step or a local template in the same change.
- If a role is added, its required skills must be justified in this file before they are added to frontmatter.
- If a referenced skill stops being assigned to any role, remove its stub from `skills/`.
- If a fast-path change requires `chief-of-staff`, `workflow-designer`, `skills-architect`, or `quality-auditor` input, it is no longer a fast-path change; move it to the structural path in the same handoff.
- If a handoff fails because the next owner, output artifact, or API reassignment was implicit, update `templates/HANDOFF.md` in the same change that fixes the miss.
- If prompt drift causes an agent to skip its task comment or assignment patch, update `templates/AGENT-PROMPT-CHECKLIST.md` before closing the issue.
