# Product Studio

> Lean engineering company powered by gstack workflow skills — distinct cognitive modes for product vision, design critique, technical planning, implementation, security auditing, code review, shipping, deployment, and QA

> An [Agent Company](https://agentcompanies.io) based on [gstack](https://github.com/garrytan/gstack) — engineering workflow skills for headless browsing, QA testing, PR review, shipping, retrospectives, and plan reviews

## What's Inside

| Content | Count |
| ------- | ----- |
| Agents  | 7     |
| Skills  | 22    |

### Agents

| Agent            | Role     | Reports To | Core Skills                                                                                |
| ---------------- | -------- | ---------- | ------------------------------------------------------------------------------------------ |
| CEO              | CEO      | -          | `office-hours`, `plan-ceo-review`                                                          |
| Senior Designer  | Designer | `ceo`      | `design-consultation`, `plan-design-review`, `design-review`, `browse`                     |
| CTO              | CTO      | `ceo`      | `plan-eng-review`, `cso`, `retro`                                                          |
| Product Engineer | Engineer | `cto`      | `investigate`, `codex`, `guard`                                                            |
| Staff Engineer   | Engineer | `cto`      | `review`, `investigate`, `codex`                                                           |
| Release Engineer | Engineer | `cto`      | `ship`, `land-and-deploy`, `document-release`, `setup-deploy`                              |
| QA Engineer      | Engineer | `cto`      | `browse`, `qa`, `qa-only`, `benchmark`, `canary`, `design-review`, `setup-browser-cookies` |

### Skills

| Skill                 | Description                                                                                       | Source                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
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
2. The `Senior Designer` converts the brief into user flows, interface states, design-system direction.
3. The `CTO` turns the experience spec into a technical execution plan with architecture, risk controls, and test coverage.
4. The `Product Engineer` implements the feature and prepares a reviewable branch.
5. The `Staff Engineer` performs structural review and either approves the branch or sends it back with concrete fixes.
6. The `Release Engineer` ships the approved branch and closes release-documentation work.
7. The `QA Engineer` verifies the shipped experience, performance, and visual quality, then reports pass/fail status back to the CTO.

### Roles

`CEO` owns product framing and scope decisions.

`Senior Designer` owns UX direction, design-system decisions, and interaction states.

`CTO` owns architecture, delivery planning, technical risk, and engineering orchestration.

`Product Engineer` owns implementation of the approved product and prepares code for review.

`Staff Engineer` owns the hard structural review gate before release.

`Release Engineer` owns branch landing, deployment flow, and release documentation.

`QA Engineer` owns post-ship verification, performance checks, and visual QA.

## Starter Work

The package includes:

- One reusable project: `new-product-launch`
- Five starter project tasks that mirror the company pipeline
- One recurring weekly portfolio review task for the CEO

## References

- Agent Companies specification: [agentcompanies.io/specification](https://agentcompanies.io/specification)
- Paperclip: [github.com/paperclipai/paperclip](https://github.com/paperclipai/paperclip)
- Upstream workflow foundation: [github.com/garrytan/gstack](https://github.com/garrytan/gstack)

## Getting Started

```bash
paperclipai company import --from /Users/pierrecorbay/Paperclip/companies/product-studio
```
