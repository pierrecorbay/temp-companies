---
name: land-and-deploy
description: >
  Merge PR, wait for deploy, verify production health. 10-step workflow:
  pre-flight, CI check, readiness gate, merge (respects merge queue), detect
  platform, wait for deploy, canary verification, revert option, deploy report.
  Auto-detects Fly, Render, Vercel, Netlify, Heroku, GitHub Actions.
metadata:
  sources:
    - kind: github-file
      repo: garrytan/gstack
      path: land-and-deploy/SKILL.md
      commit: bd8d44d64175a839f553ad0b023bd9d774bb73a7
      attribution: Garry Tan
      license: MIT
      usage: referenced
---

Use the upstream gstack land-and-deploy workflow to complete the final release step.
