---
name: benchmark
description: >
  Performance regression detection. Captures TTFB, FCP, LCP, bundle sizes,
  request counts. Regression thresholds: timing >50% or >500ms. Baseline
  comparison, trend tracking, budget compliance scorecard.
metadata:
  sources:
    - kind: github-file
      repo: garrytan/gstack
      path: benchmark/SKILL.md
      commit: bd8d44d64175a839f553ad0b023bd9d774bb73a7
      attribution: Garry Tan
      license: MIT
      usage: referenced
---

Use the upstream gstack benchmark workflow to check performance regressions after changes.
