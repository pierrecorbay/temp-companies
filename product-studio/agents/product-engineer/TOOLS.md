# Product Engineer Tools

Approved skills: `investigate`, `codex`, `guard`, `find-docs`, `researcher`

---

## /guard

**When to run:** At the start of every implementation session, before writing any code. Activate immediately when you receive a task.

**What it does:** Combines two protections:
- `careful` — warns before destructive commands (rm -rf, DROP TABLE, git reset --hard, force-push, kubectl delete)
- `freeze` — restricts file edits to the working directory, preventing accidental changes outside the intended scope

**Always on during paired build:** Guard must be active throughout the paired build stage to prevent accidental modifications to files owned by Senior Designer or to unrelated parts of the codebase.

**Do not skip:** Starting implementation without guard active is an anti-pattern. The shared review target is a collaborative artifact — accidental damage to it breaks the Senior Designer's work too.

---

## /investigate

**When to run:** Before touching any code when you encounter a bug, unexpected behavior, a failing test, or an unclear error. The Iron Law is: no fix without root cause first.

**Phases it runs:**
1. Root Cause Investigation — trace the failure to its origin, not its symptom
2. Pattern Analysis — match against 6 known bug patterns (race conditions, trust boundaries, N+1, stale reads, retry logic, invariant breaks)
3. Hypothesis Testing — 3-strike rule: test hypotheses, discard wrong ones before implementing
4. Implementation — write the fix only after root cause is confirmed

**What it produces:** Structured debug report with root cause, confidence rating, and implementation plan.

**Gate rule:** Do not commit a fix without first running `/investigate` and documenting the root cause in the issue comment. Fixes without root cause are symptoms-masking, not real fixes — they will resurface.

---

## /codex

**When to run:** Before committing an implementation decision on a complex or high-risk area, or when your approach feels uncertain.

**Modes:**
- `Review` — pass/fail gate on the current implementation. Use when the implementation is done and needs a structural second opinion before handing to Staff Engineer.
- `Challenge` — adversarial edge-case finder. Use when you want to stress-test your approach before writing it.
- `Consult` — freeform second opinion with session continuity. Use for open architectural questions or when you need to think through a tradeoff.

**What it produces:** Cross-model second opinion with streaming output and thinking traces. Read-only — it does not change your code.

**Use for:** Complex database queries, trust boundary logic, retry and rollback logic, concurrency decisions, or any area where the Staff Engineer is likely to find issues.

**Sequence tip:** Run `/codex` Challenge before implementation on high-risk areas, and `/codex` Review after implementation before handing to Staff Engineer. This reduces Staff Engineer fix-list round-trips.

---

## /find-docs

**When to run:** Before writing any code that calls a library API listed in `STACK.md` — Next.js, Convex, Better-Auth, Expo, RevenueCat, NativeWind. Do not rely on training knowledge for these libraries; their APIs evolve quickly and agents commonly use deprecated patterns.

**How it works:** Two-step — resolve library ID, then query with a precise intent-driven question.

**Required before implementing:**

| Operation | Library query |
|---|---|
| Next.js Server Components, server actions, route handlers | `next` |
| Convex mutations, queries, validators, scheduled functions | `convex` |
| Better-Auth session access, OAuth, middleware | `better-auth` |
| Expo native modules, EAS Build | `expo` |
| RevenueCat purchase flows, entitlement checks | `revenuecat` |
| NativeWind theming, Tailwind config for React Native | `nativewind` |
| shadcn/ui component usage, customization | `shadcn-ui` |

**What it produces:** Current documentation snippets and code examples, versioned to the library's latest release.

**Do not skip.** See `STACK.md` — "Agent Guidance" section for the most common patterns agents get wrong in each library.

---

## /researcher

**When to run:** When all of the following are true:
1. There is a measurable metric (LCP, TTFB, bundle size in KB, query duration in ms, a rubric score)
2. Multiple implementation approaches exist and the optimal one isn't obvious from inspection
3. The task is *optimization or experimentation*, not *feature-building*
4. Each experiment can be run with a single command in under 5 minutes

**What it does:** Interviews you on objective, metric, and termination condition. Sets up a `.lab/` experiment log. Then works autonomously — commit, run, measure, keep or revert — until the target is hit or you stop it.

**Use for:**
- LCP / TTFB optimization after a performance regression
- Bundle size reduction (identify and remove what's slow)
- Convex query performance (index selection, batching)
- Algorithm efficiency when multiple approaches exist (e.g., sorting, pagination)

**Do NOT use for:**
- Feature implementation (no measurable metric to optimize against)
- Bug fixes (use `/investigate` instead — different tool, different discipline)
- Design decisions (use `/plan-design-review` instead)

**What it produces:** `.lab/` directory with full experiment log, `results.tsv`, and `summary.md` at wrap-up. The working branch holds the best-found implementation.

---

## Escalation rules

- Escalate when the plan has gaps or architecture decisions are missing — route to `CTO` before building
- Escalate when the design is ambiguous or interaction behavior is unspecified — route to `Senior Designer` before implementing UX behavior
- Never implement beyond the scope of the approved plan
- Never invent API contracts — surface them to `CTO` before building against them
