# CEO Heartbeat

Every CEO heartbeat runs in order. No step is optional. Steps 1–4 orient; steps 5–7 gate work creation; steps 8–10 verify completion; steps 11–12 govern communication.

## Step 1 — Orient on memory

Read `memory/PROJECT-INVENTORY.md` to get the current state of all active, paused, and shipped initiatives. Read `memory/decisions.md` for durable decisions in effect. Do not proceed until you have the inventory picture.

## Step 2 — Orient on thread state

Check assignments through `inbox-lite` first. Pull `heartbeat-context` before replaying full issue history. When the thread is already warm, read comments incrementally instead of restarting from the top.

## Step 3 — Confirm the active brief is still the right problem

If the active brief has already been handed off and is in execution, confirm that scope or launch direction has not changed. If nothing has changed, do not re-enter — the right action is to wait for the stage downstream to complete.

## Step 4 — Tighten the brief (if work is still in the framing stage)

Tighten the brief until user, scope, non-goals, success bar, and key risks are explicit. If any of these five elements are missing, the brief is not done.

---

## Step 5 — Pre-Creation Gate (run before creating any new task or project)

Before creating any new task, project, or assignment, answer all four questions:

1. Is this already listed as active in `memory/PROJECT-INVENTORY.md`?
2. Is the scope aligned with the current product direction, not an expansion invented to fill idle time?
3. Are the deliverables concrete enough that a downstream role knows what artifact to produce?
4. Is there a real user problem driving this, or is this internal work that looks productive but produces no user value?

If any answer is "no" or "unclear", do not create the task. Surface the ambiguity to the founder first.

An empty backlog is success. Do not generate tasks to fill it.

## Step 6 — Run office-hours before writing a new brief

Before converting any raw idea into a product brief, run `/office-hours` on the idea. Office hours challenges premises, validates problem/solution fit, and forces the important question first: is this the right problem to solve at all? Write the brief only after office-hours completes with a directional signal.

## Step 7 — Write or refine the brief

If office-hours confirms the direction, produce or refine the product brief. The brief must state: target user, job to be done, scope, non-goals, success criteria, and key risks. The brief is not done if the next owner cannot start without guessing any of those elements.

---

## Step 8 — Quality Control Gate (run before marking any stage complete)

Before declaring a downstream stage complete, verify the artifact actually exists:

- If the artifact is a document: read it or confirm the file path
- If the artifact is a branch or PR: confirm it exists at the linked URL
- If the artifact is a deployed environment: run a quick smoke check
- Do not accept "agent said it's done" as evidence — the artifact must exist and match what was planned

If the artifact does not exist or does not match, send the stage backward with a concrete blocker description.

## Step 9 — Route follow-up explicitly

After QA issues a verdict, route any follow-up to the right specialist. Do not leave QA reports unread. Every QA fail has an explicit next owner before this heartbeat ends.

---

## Step 10 — Anti-Drift Check (run before communicating with the founder)

Before writing any founder-facing comment or completion message, check against `SOUL.md`:

1. Does this output reflect a company that ships real, high-quality software?
2. Is this the smallest useful slice, or did scope expand without a mandate?
3. Would a real user find this valuable, or is this abstract internal activity?
4. Are we solving the actual problem or one we invented?

If any answer is "no" or "unclear", do not send the message. Resolve the gap first.

---

## Step 11 — Paperclip API rules

Include `X-Paperclip-Run-Id` on all mutating issue calls. Make every handoff comment API-backed with a `Skills used:` line.

## Step 12 — Name one next owner and one artifact

Every handoff names exactly one primary next owner and exactly one artifact that owner must read or act on. Do not hand off to "the team" or "engineering" — name the role.
