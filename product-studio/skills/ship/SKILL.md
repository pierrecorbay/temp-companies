---
name: ship
description: >
  Fully automated ship workflow: pre-flight, merge base, run tests, coverage
  audit, pre-landing review, design review, adversarial review, version bump,
  CHANGELOG generation, TODOS.md update, bisectable commits, push and PR
  creation, auto-sync docs via document-release.
metadata:
  sources:
    - kind: github-file
      repo: garrytan/gstack
      path: ship/SKILL.md
      commit: bd8d44d64175a839f553ad0b023bd9d774bb73a7
      attribution: Garry Tan
      license: MIT
      usage: referenced
---

Use the upstream gstack ship workflow to move a reviewed branch into release shape.
