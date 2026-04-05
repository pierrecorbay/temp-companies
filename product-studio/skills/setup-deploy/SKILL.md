---
name: setup-deploy
description: >
  One-time deployment configuration. Detects platform, gathers URLs and health
  checks, persists to CLAUDE.md for future land-and-deploy runs.
metadata:
  sources:
    - kind: github-file
      repo: garrytan/gstack
      path: setup-deploy/SKILL.md
      commit: bd8d44d64175a839f553ad0b023bd9d774bb73a7
      attribution: Garry Tan
      license: MIT
      usage: referenced
---

Use the upstream gstack setup-deploy workflow when a repo needs deployment settings.
