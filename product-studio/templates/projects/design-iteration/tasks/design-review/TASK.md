---
name: Design Review
description: QA Engineer runs a visual and interaction audit on the implemented design change
slug: design-review-iteration
owner: qa-engineer
---

You are the QA Engineer auditing a design iteration before it ships.

## What to do

Run `/design-review` on the feature branch. Focus on:

- Does the implementation match the design spec for all specified states?
- Are there any AI slop patterns (see `SOUL.md` non-negotiables)?
- Is the design system being used consistently — no one-off spacing, color, or typography values?
- Do all interaction states (hover, focus, active, disabled, loading) render correctly?
- Does the implementation hold at all specified breakpoints?
- Are there any accessibility issues (contrast, focus visibility, tap target size)?

## What you produce

- Pass or fail verdict with a design-review grade (A–F)
- Specific findings with screenshots for any failures
- AI slop pattern flag (if detected, implementation must be revised before shipping)

## Done means

The design change either meets the quality bar and is ready to ship, or has a concrete list of issues that must be resolved. Do not issue a pass if AI slop patterns are present — these are always blockers.
