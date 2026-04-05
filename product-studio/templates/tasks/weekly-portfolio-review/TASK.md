---
name: Weekly Portfolio Review
description: Weekly operating cadence for resetting company priorities, handoffs, and B2C activation health
assignee: ceo
project: new-product-launch
schedule:
  timezone: Europe/Paris
  startsAt: 2026-03-30T09:00:00+02:00
  recurrence:
    frequency: weekly
    interval: 1
    weekdays:
      - monday
    time:
      hour: 9
      minute: 0
---

You are the CEO running the weekly portfolio review for Product Studio.

## Part 1 — Pipeline health

Review all active initiatives in `memory/PROJECT-INVENTORY.md`:

- Is each active project moving or stalled?
- Where is design or engineering blocked, and who must act to unblock it?
- Are any handoffs overdue or missing a named next owner?
- Cut any scope that no longer earns its place in the current sprint.
- Reset the week's handoffs: confirm each active task has one explicit next owner and one concrete next artifact.

## Part 2 — Activation health (B2C)

For every feature shipped in the last 30 days, review whether it is being activated by real users:

- **Is the activation metric moving?** Check the metric named in the original brief (the concrete user action that proves value was received).
- **Where are users dropping off?** If the feature is live but the activation metric is flat or declining, identify the most likely drop-off point: discoverability, onboarding flow, first empty state, or friction in the core action.
- **What is the retention signal?** Are users who activated once coming back? If not, is there a retention mechanic in the product or was it absent from the brief?

### Routing rules based on activation review

| Signal | Route to |
|--------|---------|
| Activation metric flat after 7+ days live | Senior Designer — discoverability or onboarding improvement |
| Users activate but do not return | CEO + Senior Designer — retention mechanic missing or broken |
| Users cannot find the feature | Senior Designer — entry point or navigation review |
| Activation is healthy but performance is slow | CTO — performance investigation |
| Activation is healthy | No action — this is a success state |

Do not manufacture work when activation is healthy. An empty action list from this review is a good outcome.

## Part 3 — Priorities for the week

Based on Part 1 and Part 2:

- Confirm the top one or two active initiatives for the week
- Identify anything that should be paused or cut
- Name one thing that would make the biggest difference to user activation or retention this week
- Update `memory/PROJECT-INVENTORY.md` to reflect any status changes

## Done means

Every active initiative has a clear next owner and next artifact. Any flat-activation features have a concrete routing decision. Priorities for the week are explicit.
