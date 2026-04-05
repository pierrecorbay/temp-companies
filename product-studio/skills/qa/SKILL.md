---
name: qa
description: >
  Systematically QA test a web application with browser-based bug fixing.
  Four modes: diff-aware (automatic on feature branches), full (systematic
  exploration), quick (30-second smoke test), regression (compare against
  baseline). Atomic bug-fix workflow with regression testing. Health scoring
  across 8 categories.
metadata:
  sources:
    - kind: github-file
      repo: garrytan/gstack
      path: qa/SKILL.md
      commit: bd8d44d64175a839f553ad0b023bd9d774bb73a7
      attribution: Garry Tan
      license: MIT
      usage: referenced
---

Use the upstream gstack QA workflow for browser-based verification and bug fixing.
