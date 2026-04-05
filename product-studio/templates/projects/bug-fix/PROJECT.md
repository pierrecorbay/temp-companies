---
name: Bug Fix
description: Starter project for triaging, fixing, shipping, and verifying a reported bug through the full pipeline
slug: bug-fix
owner: cto
---

Use this starter project when a confirmed bug needs to be fixed and deployed. This is a shorter pipeline than new-product-launch — it skips the CEO brief and design spec stages unless the fix requires UX changes.

## Pipeline

1. **Triage** (`CTO`) — classify severity, confirm reproduction, assign fix owner
2. **Investigate and Fix** (`Product Engineer`) — root-cause the bug and implement the fix with tests
3. **Review and Ship** (`Staff Engineer` → `Release Engineer`) — structural review, then ship
4. **Verify** (`QA Engineer`) — post-ship verification against the specific bug scenario

## When to involve Senior Designer

If the fix requires a UX change (error message copy, flow correction, empty state addition), add the **Senior Designer** to the investigate-and-fix stage before implementation begins.

## When to escalate to CEO

If root-cause analysis reveals a product scope question (e.g., the bug is a symptom of an underspecified feature), route to **CEO** before continuing.
