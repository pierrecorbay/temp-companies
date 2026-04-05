---
name: Project Setup
description: One-time setup project to configure deployment and capture the initial performance baseline before the first product sprint
slug: project-setup
owner: cto
---

Run this project once, before the first product sprint. It establishes the production infrastructure baseline that all future releases and QA will measure against.

## Pipeline

1. **Deploy Config** (`Release Engineer`) — configure the deploy platform, health checks, and environment URLs
2. **Baseline Benchmark** (`QA Engineer`) — capture initial performance baseline for regression detection

## Done means

- Deploy config is committed and verified (Release Engineer can land branches without guessing the platform)
- Performance baseline is captured (QA Engineer can run `/benchmark` and detect regressions on future builds)

## Why this matters

Without a deploy config, Release Engineer improvises on every release. Without a benchmark baseline, QA cannot detect performance regressions — they can only report on absolute numbers without context.
