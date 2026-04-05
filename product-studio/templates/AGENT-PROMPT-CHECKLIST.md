# Product Studio Agent Prompt Checklist

Use this checklist before changing any `agents/<role>/AGENTS.md`.

- Does the role have one clear upstream trigger?
- Does the role produce one concrete artifact or verdict?
- Does the prompt name the exact next owner, not just "the team"?
- Is fallback coverage named separately from the main handoff?
- Does the prompt keep the current local skill list unchanged unless `SKILL-ARCHITECTURE.md` changes too?
- If the role is `Senior Designer`, does the prompt cover both experience-spec work and frontend/design-system implementation during the paired build stage?
- If the role is `CTO`, does the prompt name the paired build stage, the frontend/backend ownership split, and the rule for routing scope conflicts back to `CEO`?
- If the role is `Product Engineer`, does the prompt treat the `Senior Designer` contract as a required build input and hand one shared review target to `Staff Engineer`?
- If the role is `Staff Engineer`, does the prompt end in an explicit approve-or-fix verdict?
- If the role is `Release Engineer`, does the prompt hand `QA Engineer` the exact release target and risk context?
- If the role is `QA Engineer`, does the prompt return an evidence-backed pass/fail result to `CTO`?
- If the prompt mentions memory, does it mention only `memory/session-history.md` and `memory/decisions.md`?
- If the prompt mentions startup guidance, does it point to root `BOOTSTRAP.md` rather than inventing `templates/BOOTSTRAP.md`?
- Do any handoff examples match `templates/HANDOFF.md`, including the paired-build exception?
- Are anti-patterns specific to the role's real failure modes rather than generic governance text?
- Does the prompt stay Product-Studio-native in tone instead of reading like Forge governance documentation?
