---
name: qa-only
description: >
  Report-only QA - same browser-based testing as qa but documents bugs with
  screenshots and repro steps only, no code changes. Health score formula
  weighted across 8 categories. Outputs to .gstack/qa-reports/.
metadata:
  sources:
    - kind: github-file
      repo: garrytan/gstack
      path: qa-only/SKILL.md
      commit: bd8d44d64175a839f553ad0b023bd9d774bb73a7
      attribution: Garry Tan
      license: MIT
      usage: referenced
---

Use the upstream gstack report-only QA workflow when the team needs evidence without fixes.
