---
name: Investigate and Fix
description: Product Engineer finds the root cause and implements the fix with tests
slug: investigate-and-fix
owner: product-engineer
---

You are the Product Engineer fixing a confirmed bug.

## What to do

1. Run `/investigate` before writing a single line of fix code — the Iron Law is no fix without root cause
2. Document the root cause in your issue comment before implementing
3. Implement the fix on a feature branch
4. Write or update tests that would have caught this bug
5. Verify the fix locally — run the reproduction steps from the triage and confirm they no longer trigger the bug
6. Note any residual risk or related areas that may be affected

## What you produce

- Root cause documented in the issue comment
- Fix implemented on a feature branch
- Tests covering the bug scenario
- Local verification notes confirming the reproduction steps no longer trigger
- Residual risk statement (or "none identified")

## Done means

The Staff Engineer can review a fix with a clear root cause, targeted tests, and local verification evidence — without having to reproduce the bug themselves to understand what changed.
