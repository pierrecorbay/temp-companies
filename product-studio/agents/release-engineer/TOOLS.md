# Release Engineer Tools

Approved skills: `ship`, `land-and-deploy`, `document-release`, `setup-deploy`

---

## /setup-deploy  *(one-time per project)*

**When to run:** The first time shipping to a new project or environment — must run before any `land-and-deploy` call. Also re-run when the deploy platform changes.

**What it produces:** Deploy config persisted to `CLAUDE.md`: platform detection (Fly.io, Render, Vercel, Netlify, Heroku, GitHub Actions), production and staging URLs, health-check endpoints, rollback procedure.

**Prerequisite:** All subsequent `/ship` and `/land-and-deploy` runs depend on this config. Without it, every release involves guessing the platform and environment URLs.

---

## /ship

**When to run:** After the structural review passes and the build artifact is ready to become a release candidate. Run before `land-and-deploy`.

**What it produces:** Fully prepared release artifact:
- Pre-flight checks (branch health, conflicts)
- Tests run and coverage audited
- Pre-landing review, design review, and adversarial review applied
- VERSION bumped and CHANGELOG generated
- TODOS.md updated
- Bisectable commits created
- PR created and docs synced via `document-release`

**Sequencing rule:** `/ship` prepares the artifact. `/land-and-deploy` merges and deploys it. Always run `/ship` first — do not call `/land-and-deploy` on an unprepared branch.

**Gate rule:** Do not run `/ship` without a structural review verdict from the Staff Engineer. Shipping a branch without review approval is an anti-pattern.

---

## /land-and-deploy

**When to run:** After `/ship` completes and the PR is in release shape.

**What it produces:** 10-step deployment workflow:
1. Pre-flight check
2. CI status check
3. Readiness gate
4. Merge (respects merge queue)
5. Platform detection (uses config from `/setup-deploy`)
6. Deploy wait
7. Canary verification
8. Revert option (if canary fails)
9. Deploy report

**Do not skip the canary step:** `land-and-deploy` includes a built-in canary verification pass — this is not optional. If canary fails, use the revert option and route back to CTO.

---

## /document-release

**When to run:** After `land-and-deploy` completes successfully — sync all release-facing docs before handing off to QA.

**What it produces:** Updated README, ARCHITECTURE, CONTRIBUTING, CHANGELOG, TODOS, VERSION. Auto-applies factual corrections and asks before risky rewrites. Cross-doc consistency checks.

**Do not skip:** Release docs drift quickly. Running `/document-release` after every deploy keeps docs current without manual effort. QA and future agents depend on accurate docs.

---

## Skill execution order

For a standard release, run skills in this order:

1. `/setup-deploy` (once per project, before the first release)
2. `/ship` (prepares the artifact)
3. `/land-and-deploy` (merges and deploys)
4. `/document-release` (syncs docs post-deploy)

Then hand off to **QA Engineer** with: environment URL, expected behavior, and risk areas from the structural review.

---

## Escalation rules

- Do not proceed without a Staff Engineer review verdict — escalate to `CTO` if it is missing
- Do not mark release complete without a concrete deploy artifact at the target environment
- Escalate when deploy state is unclear or canary fails — route to `CTO`; do not paper over deployment failures
