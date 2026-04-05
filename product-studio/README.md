# Product Studio

> Lean engineering company powered by gstack workflow skills — distinct cognitive modes for product vision, design critique, technical planning, paired implementation, structural review, release, and QA

> An [Agent Company](https://agentcompanies.io) based on [gstack](https://github.com/garrytan/gstack) with a tighter local runtime surface for paired build handoffs, shared workflow memory, and reusable starter templates

## What's Inside

| Content | Count |
| ------- | ----- |
| Agents  | 7     |
| Skills  | 25    |

The package also includes the lean runtime docs and local capability assets Product Studio needs to start work without guessing: root `BOOTSTRAP.md`, root `CONTRIBUTING.md`, root `SKILL-ARCHITECTURE.md`, `.paperclip.yaml`, shared `memory/`, canonical `templates/`, and one role-contract bundle (`AGENTS.md`, `HEARTBEAT.md`, `TOOLS.md`) for each agent.

### Agents

| Agent            | Role     | Reports To | Core Skills                                                                                |
| ---------------- | -------- | ---------- | ------------------------------------------------------------------------------------------ |
| CEO              | CEO      | -          | `office-hours`, `plan-ceo-review`, `autoplan`                                              |
| Senior Designer  | Designer | `ceo`      | `design-consultation`, `plan-design-review`, `design-review`, `browse`                     |
| CTO              | CTO      | `ceo`      | `plan-eng-review`, `cso`, `retro`, `autoplan`, `find-docs`                                 |
| Product Engineer | Engineer | `cto`      | `investigate`, `codex`, `guard`, `find-docs`, `researcher`                                 |
| Staff Engineer   | Engineer | `cto`      | `review`, `investigate`, `codex`                                                           |
| Release Engineer | Engineer | `cto`      | `ship`, `land-and-deploy`, `document-release`, `setup-deploy`                              |
| QA Engineer      | Engineer | `cto`      | `browse`, `qa`, `qa-only`, `benchmark`, `canary`, `design-review`, `setup-browser-cookies` |

### Skills

| Skill                 | Description                                                                                       | Source                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| autoplan              | Fully automated review pipeline — CEO, design, and eng reviews in one pass with auto-decisions.   | [github](https://github.com/garrytan/gstack/blob/main/autoplan/SKILL.md)              |
| benchmark             | Performance regression detection — TTFB, FCP, LCP, bundle sizes, request counts.                  | [github](https://github.com/garrytan/gstack/blob/main/benchmark/SKILL.md)             |
| browse                | Headless Chromium CLI for QA testing and site dogfooding.                                         | [github](https://github.com/garrytan/gstack/blob/main/SKILL.md)                       |
| canary                | Post-deploy monitoring — watches live app for console errors, perf regressions, visual anomalies. | [github](https://github.com/garrytan/gstack/blob/main/canary/SKILL.md)                |
| codex                 | Multi-AI second opinion via OpenAI Codex CLI — review, challenge, consult modes.                  | [github](https://github.com/garrytan/gstack/blob/main/codex/SKILL.md)                 |
| cso                   | Infrastructure-first security audit across 14 phases including OWASP Top 10 and STRIDE.           | [github](https://github.com/garrytan/gstack/blob/main/cso/SKILL.md)                   |
| design-consultation   | Build a complete design system from scratch with competitive research.                            | [github](https://github.com/garrytan/gstack/blob/main/design-consultation/SKILL.md)   |
| design-review         | Live-site visual QA audit with fix loop — 10-category checklist, AI slop detection.               | [github](https://github.com/garrytan/gstack/blob/main/design-review/SKILL.md)         |
| document-release      | Post-ship documentation sync — README, ARCHITECTURE, CHANGELOG, TODOS, VERSION.                   | [github](https://github.com/garrytan/gstack/blob/main/document-release/SKILL.md)      |
| guard                 | Combines careful + freeze — destructive command warnings plus edit boundary enforcement.          | [github](https://github.com/garrytan/gstack/blob/main/guard/SKILL.md)                 |
| investigate           | Systematic root-cause debugging — no fixes without root cause investigation first.                | [github](https://github.com/garrytan/gstack/blob/main/investigate/SKILL.md)           |
| land-and-deploy       | Merge PR, wait for deploy, verify production health — auto-detects platform.                      | [github](https://github.com/garrytan/gstack/blob/main/land-and-deploy/SKILL.md)       |
| office-hours          | YC Office Hours — product idea diagnostic before writing code.                                    | [github](https://github.com/garrytan/gstack/blob/main/office-hours/SKILL.md)          |
| plan-ceo-review       | CEO/founder-mode plan review — 10 review sections, nuclear scope challenge.                       | [github](https://github.com/garrytan/gstack/blob/main/plan-ceo-review/SKILL.md)       |
| plan-design-review    | Design critique with 7 rated passes including AI slop risk detection.                             | [github](https://github.com/garrytan/gstack/blob/main/plan-design-review/SKILL.md)    |
| plan-eng-review       | Eng manager-mode plan review — architecture, test coverage, performance.                          | [github](https://github.com/garrytan/gstack/blob/main/plan-eng-review/SKILL.md)       |
| qa                    | Systematically QA test a web app with browser-based bug fixing — 4 modes.                         | [github](https://github.com/garrytan/gstack/blob/main/qa/SKILL.md)                    |
| qa-only               | Report-only QA — documents bugs with screenshots and repro steps, no code changes.                | [github](https://github.com/garrytan/gstack/blob/main/qa-only/SKILL.md)               |
| retro                 | Weekly engineering retrospective — commit analysis, per-person breakdowns, shipping streaks.      | [github](https://github.com/garrytan/gstack/blob/main/retro/SKILL.md)                 |
| review                | Pre-landing PR review — two-pass checklist, adversarial review, scope drift detection.            | [github](https://github.com/garrytan/gstack/blob/main/review/SKILL.md)                |
| setup-browser-cookies | Import cookies from real browsers into headless browse sessions.                                  | [github](https://github.com/garrytan/gstack/blob/main/setup-browser-cookies/SKILL.md) |
| setup-deploy          | One-time deployment configuration — detects platform, persists to CLAUDE.md.                      | [github](https://github.com/garrytan/gstack/blob/main/setup-deploy/SKILL.md)          |
| ship                  | Fully automated ship workflow — tests, reviews, version bump, CHANGELOG, PR.                      | [github](https://github.com/garrytan/gstack/blob/main/ship/SKILL.md)                  |

### Workflow

Product Studio uses a tight pipeline with explicit handoffs:

1. The `CEO` turns raw requests into a product brief with scope, user value, and success criteria.
2. The `Senior Designer` converts the brief into user flows, interface states, and design-system direction.
3. The `CTO` turns the brief plus experience spec into a technical execution plan with architecture, ownership boundaries, risk controls, and test coverage.
4. The paired build stage opens: `Senior Designer` owns frontend, UI behavior, and design-system implementation while `Product Engineer` owns backend, app logic, and integration on one shared review target.
5. The `Staff Engineer` performs structural review and either approves the shared build artifact or sends it back with concrete fixes.
6. The `Release Engineer` ships the approved work and closes release-documentation work.
7. The `QA Engineer` verifies the shipped experience, performance, and visual quality, then reports pass/fail status back to the `CTO`.

Fallback coverage exists only to preserve routing continuity. `CTO` backs `Senior Designer`, `Product Engineer`, `Staff Engineer`, `Release Engineer`, and `QA Engineer`. `CEO` backs `CTO`. These fallbacks do not waive any gates.

### Roles

`CEO` owns product framing and scope decisions.

`Senior Designer` owns UX direction, design-system decisions, and the frontend slice during the paired build stage.

`CTO` owns architecture, delivery planning, technical risk, and the paired-build ownership split.

`Product Engineer` owns backend, app logic, and integration implementation on the shared review target.

`Staff Engineer` owns the hard structural review gate before release.

`Release Engineer` owns branch landing, deployment flow, and release documentation.

`QA Engineer` owns post-ship verification, performance checks, and visual QA.

## Starter Work

The package includes:

- One reusable project template: `templates/projects/new-product-launch`
- One recurring weekly portfolio review task template in `templates/tasks/weekly-portfolio-review`
- One engineering team scaffold in `teams/engineering/TEAM.md`

## Runtime Surface

Product Studio's required local runtime surface is:

- Root docs: `COMPANY.md`, `README.md`, `BOOTSTRAP.md`, `CONTRIBUTING.md`, `SKILL-ARCHITECTURE.md`, `.paperclip.yaml`
- Role bundles: `agents/<role>/AGENTS.md`, `agents/<role>/HEARTBEAT.md`, `agents/<role>/TOOLS.md`
- Shared memory: `memory/session-history.md`, `memory/decisions.md`
- Canonical templates: `templates/HANDOFF.md`, `templates/AGENT-PROMPT-CHECKLIST.md`, `templates/projects/**`, `templates/tasks/**`
- Capability assets: `skills/**`

## References

- Agent Companies specification: [agentcompanies.io/specification](https://agentcompanies.io/specification)
- Paperclip: [github.com/paperclipai/paperclip](https://github.com/paperclipai/paperclip)
- Upstream workflow foundation: [github.com/garrytan/gstack](https://github.com/garrytan/gstack)

## Getting Started

```bash
paperclipai company import --from /path/to/product-studio
```

After import, read `BOOTSTRAP.md`, then `COMPANY.md`, then the active role bundle under `agents/<role>/`.
