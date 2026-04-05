---
name: review
description: >
  Pre-landing PR review with two-pass checklist. Pass 1 critical: SQL safety,
  race conditions, LLM trust boundaries, enum completeness. Pass 2 informational:
  side effects, magic numbers, dead code, test gaps. Adversarial review auto-scaled
  by diff size. Scope drift detection.
metadata:
  sources:
    - kind: github-file
      repo: garrytan/gstack
      path: review/SKILL.md
      commit: bd8d44d64175a839f553ad0b023bd9d774bb73a7
      attribution: Garry Tan
      license: MIT
      usage: referenced
---

Use the upstream gstack review workflow as the structural pre-release gate.
