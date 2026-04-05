---
name: codex
description: >
  Multi-AI second opinion via OpenAI Codex CLI. Three modes: Review (pass/fail
  gate), Challenge (adversarial edge-case finder), Consult (freeform with
  session continuity). Read-only with streaming output and thinking traces.
  Cross-model analysis when review has already run.
metadata:
  sources:
    - kind: github-file
      repo: garrytan/gstack
      path: codex/SKILL.md
      commit: bd8d44d64175a839f553ad0b023bd9d774bb73a7
      attribution: Garry Tan
      license: MIT
      usage: referenced
---

Use the upstream gstack codex workflow for a second opinion on plans, diffs, or debugging.
