---
name: Baseline Benchmark
description: QA Engineer captures the initial performance baseline for regression detection on all future releases
slug: baseline-benchmark
owner: qa-engineer
---

You are the QA Engineer establishing the initial performance baseline for this project.

## What to do

Run `/benchmark` against the production (or staging) environment to capture baseline metrics. This baseline is what all future releases will be compared against to detect regressions.

Baseline covers:
- TTFB (Time to First Byte)
- FCP (First Contentful Paint)
- LCP (Largest Contentful Paint)
- Bundle sizes
- Request counts per page
- Any platform-specific performance signals

## What you produce

- Baseline benchmark report committed or logged for future comparison
- Notes on any existing performance issues to track (not to fix now — document as known state)
- Regression thresholds configured (>50% or >500ms degradation triggers a flag)

## Done means

Future releases can be evaluated against concrete numbers. The QA Engineer can run `/benchmark` on any future build and detect regressions relative to this baseline.

## Note

If the production environment is not yet deployed, run against staging. Note which environment was used as the baseline so future comparisons use the same environment.
