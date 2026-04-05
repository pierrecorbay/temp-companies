---
name: canary
description: >
  Post-deploy monitoring. Watches live app via headless browser for console
  errors, performance regressions, page failures, visual anomalies. Alert on
  deltas not absolutes, transient tolerance (2+ consecutive checks). Default
  10-minute monitoring window. Baseline capture mode.
metadata:
  sources:
    - kind: github-file
      repo: garrytan/gstack
      path: canary/SKILL.md
      commit: bd8d44d64175a839f553ad0b023bd9d774bb73a7
      attribution: Garry Tan
      license: MIT
      usage: referenced
---

Use the upstream gstack canary workflow to watch live deployments after release.
