# Senior Designer Tools

Approved skills: `design-consultation`, `plan-design-review`, `design-review`, `browse`

---

## /design-consultation

**When to run:**
- When starting a new product or major surface and no `DESIGN.md` exists — run before writing the experience spec
- When a new component category is introduced that the existing design system does not cover
- When a design-iteration project changes the design system direction (new tokens, updated component patterns, removed patterns)
- At minimum once per quarter if the product has been actively evolving — to resync `DESIGN.md` with what is actually built

**What it produces:** `DESIGN.md` — complete design system from competitive research, SAFE/RISK analysis of choices, self-contained HTML preview page. This is the design source of truth.

**DESIGN.md update cadence:** `DESIGN.md` is a living document, not a one-time artifact. It goes stale as the product evolves. Keep it current by:
- Running `/design-consultation` (or manually updating `DESIGN.md`) whenever a new component is added to the design system
- Noting divergences between `DESIGN.md` and the actual implementation in the experience spec — do not silently let them grow
- Treating a stale `DESIGN.md` as a blocker for new design work: if the file does not reflect what is actually built, update it before speccing new features on top of it

**Gate rule:** If `DESIGN.md` does not exist and the product area is new, run `/design-consultation` before writing the experience spec. If `DESIGN.md` exists but is clearly stale (references components that no longer exist or omits major additions), update it before the experience spec references it.

---

## /plan-design-review

**When to run:** After drafting the experience spec, before handing it off to the CTO for technical planning.

**What it produces:** 7 rated passes (0–10 each): Information Architecture, Interaction State Coverage, User Journey and Emotional Arc, AI Slop Risk (10-item blacklist), Design System Alignment, Responsive and Accessibility, Unresolved Decisions. Gap-fill loop on low scores. Parallel cross-model design voices.

**Gate rule:** Do not hand the spec to the CTO if any critical pass scores below 7 or if any unresolved decision is flagged. Resolve gaps before handoff — the CTO cannot plan around ambiguity.

---

## /design-review

**When to run:** After implementation is available on a feature branch or deployed — run on the live UI surface.

**Modes:**
- `Diff-aware` — automatically targets pages affected by the current branch diff. Use by default on feature branches.
- `Full` — systematic 80-item audit of the entire product. Use after major releases or design system changes.
- `Quick` — 30-second smoke test of the primary user-facing surface. Use for fast confidence checks.
- `Deep` — comprehensive audit with before/after screenshots and atomic fixes.
- `Regression` — compare current visual state against a stored baseline.

**What it produces:** A–F grade, 80-item checklist results, AI slop detection (10 blacklisted patterns), before/after screenshots, fix loop with atomic commits.

**Gate rule:** Do not mark the frontend slice done if `/design-review` surfaces AI slop patterns. These are always blockers. Fix before handing off to Staff Engineer.

---

## /browse

**When to run:** For targeted research or evidence gathering — when you need to inspect a competitor's UI, view a live interaction state, verify a specific component, or capture a screenshot as evidence.

**What it produces:** Screenshots, page state verification, responsive layout checks, form interaction results, console output. Persistent session with cookies and tabs.

**Use instead of guessing:** Before specifying how a state should behave, browse real examples. If you are unsure how a competitor handles an empty state or error flow, look it up first.

**Also use during spec work:** When describing an interaction that depends on real-world context (browser behavior, third-party widget), browse to confirm before specifying.

---

## Escalation rules

- Escalate scope questions to `CEO` — do not unilaterally expand or narrow the product
- Escalate technical tradeoffs to `CTO` — do not invent backend behavior in a spec; name it as a dependency
- Never hand off a spec with unresolved design decisions; resolve or name them explicitly
