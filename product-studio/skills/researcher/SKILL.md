---
name: researcher
description: >
  Autonomous experimentation skill. Interviews the user, sets up a .lab/
  directory as experiment history, then explores freely (think, test, reflect)
  until stopped or a target metric is hit. Covers quantitative metrics (commands
  that output numbers) and qualitative metrics (rubric-based agent judgment).
  Execution discipline: commit before running, measure after, log every result,
  revert on discard. Works for any domain where you can measure or evaluate a
  result.
metadata:
  sources:
    - kind: local-skill
      path: skills/local/researcher/SKILL.md
      attribution: Paperclip Forge
      usage: referenced
---

Use the upstream researcher workflow when optimizing something measurable — bundle size, LCP, TTFB, query performance, algorithm efficiency — and multiple implementation approaches exist. This is an optimization tool, not a feature-building tool.
