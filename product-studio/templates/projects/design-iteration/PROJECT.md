---
name: Design Iteration
description: Shorter pipeline for design-only changes that don't require new backend work or the full new-product-launch pipeline
slug: design-iteration
owner: senior-designer
---

Use this starter project when the work is design-system or frontend-only: updating visual treatments, refining interaction states, fixing AI slop patterns caught in review, or evolving the design system without new backend functionality.

## Pipeline

1. **Design Spec** (`Senior Designer`) — produce or refine the experience spec for the targeted area
2. **Implement** (`Senior Designer`) — implement the frontend/design-system change on a feature branch
3. **Design Review** (`QA Engineer`) — run `/design-review` to verify the change against the design system, accessibility, and AI slop checklist

## When to escalate to CTO

If the implementation requires backend changes (new API fields, schema changes, new endpoints), this is no longer design-iteration — escalate to **CTO** to open a technical execution plan.

## When to escalate to Staff Engineer

If the change is large enough to warrant a structural review (significant component refactor, design system overhaul), route to **Staff Engineer** before release.

## Done means

The visual or interaction change is implemented, verified by `/design-review`, and shipped without introducing new design debt or bypassing the design system.
