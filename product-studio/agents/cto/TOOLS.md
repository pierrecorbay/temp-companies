# CTO Tools

Approved skills: `plan-eng-review`, `cso`, `retro`, `autoplan`, `find-docs`

---

## /autoplan

**When to run:** When locking a technical execution plan that has gone through several rounds of revision and you want a combined pass across all three review lenses (CEO scope, design quality, eng architecture) before opening the paired build stage.

**What it does:** Runs CEO review → Design review → Eng review in sequence. Auto-resolves mechanical decisions silently. Surfaces only Taste-level decisions at the final gate.

**What it produces:** Consolidated review output across all three stages. Flags any scope drift, design gap, or architecture weakness that a single-lens review might miss.

**Use for:**
- Final sanity check before opening the paired build stage on a complex or high-risk feature
- Unblocking a stalled plan when it's unclear whether the issue is scope (CEO), design (Senior Designer), or architecture (CTO) — autoplan locates it
- Re-validating a plan after significant rework (e.g., after a QA failure that caused a full replan)

**Sequence tip:** Run `/plan-eng-review` for depth; run `/autoplan` for breadth. Use autoplan when you need coverage across all three lenses, plan-eng-review when you need maximum depth on architecture and test coverage specifically.

---

## /plan-eng-review

**When to run:** After the experience spec is locked, before opening the paired build stage. Run on the technical execution plan to confirm architecture, ownership boundaries, and test expectations are solid before implementation begins.

**What it produces:** Scope challenge, architecture review, code quality review, detailed test coverage diagram, performance review. Produces a **test plan artifact** that the QA Engineer will use for verification.

**Gate rule:** Do not open the paired build stage until `/plan-eng-review` clears architecture decisions and test expectations. If the review surfaces ambiguity in ownership boundaries or integration points, resolve it in the plan before handing to Product Engineer and Senior Designer.

---

## /cso

**When to run:** On any feature that touches authentication, authorization, payments, user data, external APIs, AI/LLM inputs, file uploads, or webhooks. Also run periodically (at minimum once per quarter) on the full codebase.

**What it produces:** 14-phase security audit: attack surface mapping, secrets archaeology (git history), supply chain analysis, CI/CD pipeline security, LLM/AI threat detection, OWASP Top 10, STRIDE threat modeling. Confidence gates, exploit scenarios, parallel verification. Read-only — findings route to Product Engineer for fixes.

**Gate rule:** Any feature touching trust boundaries must pass `/cso` before the Release Engineer ships. Do not waive this gate for speed — security findings in production cost far more than a pre-ship audit.

---

## /retro

**When to run:** Weekly, every Friday — analyze the past 7 days of engineering activity. Also run after any significant incident or missed delivery.

**Modes:**
- Default `7d` — standard weekly retrospective
- `24h` — use after an incident or urgent delivery to review the immediate past
- `14d` / `30d` — use for sprint-level or monthly retrospectives
- `compare` — compare two periods for trend analysis
- `global` — cross-project view when multiple projects are running

**What it produces:** Commit history analysis, per-contributor breakdown with praise and growth areas, shipping streaks, code quality metrics, process improvement recommendations, tweetable summary.

**Use for:** Catching delivery slowdowns before they become blockers, giving real feedback to contributors, and continuously improving the engineering system.

---

## /find-docs

**When to run:** Before making any architecture decision that depends on a library's current API, before writing the technical execution plan for a feature using libraries listed in `STACK.md`, and whenever a library capability assumption might be wrong or outdated.

**How it works:** Two-step — resolve the library ID, then query for specific behavior. Pass a precise, intent-driven query (not a single word).

**Required before planning with these libraries:**

| Library | What to look up |
|---|---|
| `next` | Middleware behavior, server actions, caching directives, App Router conventions |
| `convex` | Mutation validators, scheduled functions, file storage, auth integration |
| `better-auth` | OAuth provider setup, session plugins, server-side session access |
| `expo` | EAS Build configuration, native module compatibility, SDK version APIs |
| `revenuecat` | Purchase flows, entitlement checks, customer info handling |

**What it produces:** Current documentation snippets and code examples from authoritative sources, versioned to the library's latest release.

**Do not skip:** Planning with outdated API assumptions is the most common cause of implementation rework. Run `/find-docs` — it takes 10 seconds.

---

## Escalation rules

- Escalate product-scope disputes to `CEO` — do not resolve "what to build" questions with technical prose
- `/cso` findings route to `Product Engineer` for implementation fixes; CTO reviews and prioritizes
- If `/plan-eng-review` surfaces scope questions, route back to `CEO` before locking the plan
