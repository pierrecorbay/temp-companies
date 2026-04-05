---
name: Review and Ship
description: Staff Engineer reviews the fix; Release Engineer ships it
slug: review-and-ship
owner: staff-engineer
---

## Stage 1: Structural Review (Staff Engineer)

You are the Staff Engineer reviewing a bug fix.

Focus the review on:
- Does the fix address the root cause or just mask a symptom?
- Are the new tests actually covering the failure mode or just the happy path around the fix?
- Does the fix introduce any new race conditions, trust boundary issues, or N+1 queries?
- Are there any related invariants that the fix may have broken?

Produce an approve-or-fix verdict with specific findings. Do not issue a pass if tests only confirm the fix works — confirm they would have caught the original bug.

## Stage 2: Ship (Release Engineer)

Once the structural review passes, ship the fix:

1. Sync with target branch and resolve any conflicts deliberately
2. Run required checks
3. Update CHANGELOG if the repo expects it
4. Ship and monitor deploy status

Hand off to **QA Engineer** with: environment URL, original reproduction steps, and any residual risk areas called out in the structural review.

## Done means

The fix is live at the target environment and QA has the exact reproduction steps to verify it is resolved.
