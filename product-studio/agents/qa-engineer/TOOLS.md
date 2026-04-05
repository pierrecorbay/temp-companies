# QA Engineer Tools

Approved skills: `browse`, `qa`, `qa-only`, `benchmark`, `canary`, `design-review`, `setup-browser-cookies`

---

## /setup-browser-cookies  *(one-time per environment)*

**When to run:** Before testing any authenticated page for the first time, or when session cookies expire. Must run before `qa`, `qa-only`, or `browse` can access authenticated surfaces.

**What it does:** Imports cookies from a real browser (Chrome, Arc, Brave, Edge) via macOS Keychain integration. Interactive picker UI or direct domain import.

**Gate rule:** If the product has authenticated pages, run `/setup-browser-cookies` before starting any QA session. Testing logged-out behavior on logged-in pages produces false bugs.

---

## /browse

**When to run:** For targeted investigation — reproducing a specific bug, verifying a specific element or interaction state, capturing screenshot evidence, or confirming a fix before writing the verification report.

**What it produces:** Screenshots, page state, network request logs, console output. Persistent session with cookies, tabs, and snapshots.

**Use for:**
- Reproducing a bug report step-by-step before writing the repro steps
- Capturing before/after evidence for a fix
- Quick manual checks on a specific state that `qa` would take longer to reach
- Inspecting responsive layouts at specific breakpoints

**Do not use as a substitute for systematic testing:** `/browse` is for targeted investigation; `/qa` and `/qa-only` are for systematic coverage.

---

## /qa

**When to run:** Standard post-ship verification when the release needs full testing and bugs found should be fixed inline.

**Modes:**
- `Diff-aware` *(default for feature branches)* — analyzes the git diff, identifies affected pages, tests them. Use by default on feature branch releases.
- `Full` — systematic exploration of the entire product across all major flows. Use after major releases or when regressions are suspected.
- `Quick` — 30-second smoke test of homepage and top navigation targets. Use for fast confidence checks after a hotfix or minor deploy.
- `Regression` — compare against a stored baseline. Use when you suspect a specific area regressed.

**What it produces:** Pass/fail verdict, bug list with repro steps and screenshots, health score across 8 categories, atomic bug fixes (committed inline).

**When to use vs `/qa-only`:** Use `/qa` when you have authorization to fix bugs. Use `/qa-only` when evidence is needed without code changes.

---

## /qa-only

**When to run:** When the team needs a QA report without code modifications — for a blocked handoff, a disputed QA result, a regression baseline, or when fix authorization is unclear.

**What it produces:** Same testing as `/qa` but documentation-only: bugs with screenshots and repro steps, health score, outputs to `.gstack/qa-reports/`. No code changes.

**Use for:** Building the evidence record for a CTO routing decision, or when running QA on a surface you should not touch (e.g., a third-party integration).

---

## /benchmark

**When to run:** After every deploy that could affect performance — after any backend change, frontend bundle change, or dependency update. Also run as part of the one-time project setup baseline.

**What it produces:** TTFB, FCP, LCP, bundle sizes, request counts compared against the stored baseline. Regression flag if degradation exceeds 50% or 500ms.

**Gate rule:** Requires the project-setup baseline to exist (see `templates/projects/project-setup`). If no baseline exists, run the baseline benchmark task first — `/benchmark` cannot detect regressions without a reference point.

---

## /canary

**When to run:** Immediately after every live deploy — start monitoring as soon as `land-and-deploy` completes. Default monitoring window is 10 minutes.

**What it produces:** Real-time alerts on console errors, performance regressions, page failures, and visual anomalies. Delta-based alerting (changes from baseline, not absolute values). Transient tolerance: 2+ consecutive checks before firing an alert.

**Gate rule:** Run `/canary` before declaring QA complete on any production release. A deploy that passes all static tests can still fail under real traffic — canary catches this. If canary fires, route back to CTO immediately.

---

## /design-review

**When to run:** On every release that includes UI changes — run on the live deployed surface after `land-and-deploy` completes.

**Modes:**
- `Diff-aware` *(default for feature branches)* — targets pages affected by the current diff
- `Full` — systematic 80-item audit of the entire product
- `Quick` — fast scan of primary surfaces
- `Deep` — comprehensive audit with atomic fix commits and before/after screenshots
- `Regression` — compare visual state against a stored baseline

**What it produces:** A–F grade, 80-item checklist results, AI slop detection (10 blacklisted patterns), before/after screenshots, fix loop.

**AI slop flag = blocker:** If `/design-review` surfaces AI slop patterns, do not issue a QA pass. Route back to Senior Designer with the specific findings. AI slop patterns are always release blockers.

---

## Standard post-ship verification sequence

For a standard feature release, run skills in this order:

1. `/setup-browser-cookies` (if authenticated pages are in scope and not yet configured)
2. `/canary` — start monitoring immediately after deploy
3. `/qa` diff-aware — test affected pages
4. `/benchmark` — check for performance regressions
5. `/design-review` diff-aware — audit visual quality on affected pages
6. `/browse` — targeted evidence capture for any specific failures found above

Then report pass/fail verdict to **CTO** with evidence for all failures.

---

## Escalation rules

- Escalate when release context is incomplete — route to `Release Engineer` for environment details
- Escalate when failures need prioritization or routing — send to `CTO` with evidence
- Never route bugs directly to implementers — all routing goes through `CTO`
- Never issue a pass without evidence — screenshots, logs, or canary output must back every verdict
