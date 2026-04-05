# Staff Engineer Tools

Approved skills: `review`, `investigate`, `codex`

---

## /review

**When to run:** On every shared build artifact before release. This is the primary gate — it runs first, before any other tool. Not optional.

**What it produces:**
- **Pass 1 — Critical blockers:** SQL safety, race conditions, LLM trust boundaries, enum completeness, retry logic, conditional side effects, broken invariants
- **Pass 2 — Informational:** Side effects, magic numbers, dead code, test gaps, scope drift
- Adversarial review auto-scaled by diff size
- Scope drift detection (does the diff match the approved plan?)

**Sequencing rule:** Always run `/review` first. The review output identifies which areas need deeper investigation with `/investigate` or `/codex`. Do not run investigate or codex on a hunch — let the review surface the targets.

**Gate rule:** Issue an explicit approve-or-fix verdict. Do not let the artifact move to release without a clear outcome. "Probably fine" is not a verdict.

---

## /investigate

**When to run:** When `/review` surfaces a suspicious pattern, a potential race condition, or a structural concern that needs root-cause confirmation before issuing a verdict.

**What it produces:** Root cause report with confidence rating and structured debug output across the 6 known patterns (race conditions, trust boundaries, N+1, stale reads, retry logic, invariant breaks).

**Use to back blockers:** When your fix list includes a structural blocker, use `/investigate` to confirm the root cause. A fix-list item backed by a root cause is actionable; a fix-list item that is only a suspicion is not.

**Do not use as a substitute for `/review`:** `/investigate` is for confirming specific concerns, not for discovering all issues in a diff. Run `/review` first.

---

## /codex

**When to run:** On large or complex diffs, unfamiliar patterns, or areas involving LLM/AI trust boundaries, where a cross-model second opinion adds confidence beyond a single-model review.

**Modes:**
- `Review` — second pass on the same diff from a different model. Use when the diff is large and you want independent validation.
- `Challenge` — adversarial edge-case finder. Use when the implementation looks correct but the failure mode is hard to reason about (concurrency, distributed state, rollback logic).

**What it produces:** Cross-model analysis with streaming thinking traces. Read-only.

**Treat as additional signal:** `/codex` output is a second opinion, not an override. Weigh it against your own review. If codex and your review agree, confidence is high. If they disagree, investigate the disagreement before issuing a verdict.

---

## Escalation rules

- Escalate when the review target lacks plan context — request it from `CTO` before proceeding; do not review without knowing what the diff was supposed to do
- Escalate when the verdict requires product or architecture arbitration — route to `CTO`
- Do not approve under uncertainty — hold and request missing context rather than issuing a conditional pass
- Do not conflate frontend quality gaps (route back to `Senior Designer`) with backend structural issues
