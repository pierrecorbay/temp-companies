---
name: Experience Spec
description: Turn the approved CEO brief into a full product and design specification — this document IS the PRD
assignee: senior-designer
project: new-product-launch
skills: design-consultation, plan-design-review, browse
---

# Experience Spec

This task produces the consolidated PRD for the product. It confirms the CEO brief, expands it into a full experience specification, and locks the 9 required elements before CTO writes the technical execution plan.

**Input required:** Approved CEO brief (from `discovery-brief` task) with all 4 B2C fields filled in.

**Output:** This document, fully completed, confirmed by Senior Designer, and handed to CTO.

---

## Step 1 — Confirm the Brief

Before writing the spec, confirm the brief is complete. Copy the values from the approved CEO brief and fill in each field.

**Problem statement:**
> [What real user problem does this solve? One sentence.]

**Target user:**
> [Who specifically? Not "users" — a concrete persona or segment.]

**Scope — in:**
> [What is included in this release?]

**Scope — non-goals (out):**
> [What is explicitly excluded? Name at least 3.]

**Success criteria:**
> [How will we know this shipped successfully? Name the primary metric.]

**B2C activation metric:**
> [What is the one action that means a user is activated? e.g., "user completes first export", "user invites one other person"]

**B2C distribution vector:**
> [How does this product reach its first 100 users? e.g., "App Store organic search", "referral loop built into the product", "SEO from user-generated content"]

**B2C retention mechanic:**
> [Why does a user come back next week? e.g., "weekly digest email", "streak mechanic", "ongoing project state"]

**B2C delight moment:**
> [What is the one moment in the product that makes a user say "wow"? Describe it in one sentence.]

**Stack:**
> [Confirm the platform targets: web / mobile / both. Confirm stack from STACK.md or name the approved deviation.]

If any field is missing or unclear, stop here and route back to CEO before continuing.

---

## Step 2 — Run Design Consultation (if DESIGN.md does not exist)

If no `DESIGN.md` exists in the project root, run `/design-consultation` before writing the spec. The spec must reference design tokens, typography, and component direction from the design system — not invent them inline.

If `DESIGN.md` exists but is more than one quarter old or does not reflect the current product, update it before proceeding.

---

## Step 3 — Write the 9-Element Spec

Complete all 9 sections. Do not leave a section as "TBD" — if the answer is unknown, surface it as an open question and route to CEO or CTO before handing off.

### 1. User Flows

Map every primary user journey as a numbered sequence of steps. Include the trigger (what the user does or sees to begin the flow) and the terminal state (what success looks like).

**Flow: [Name]**
1. [Step]
2. [Step]
3. [Terminal state — what the user now has or sees]

Add one flow per primary journey. Minimum: the core activation flow, the returning-user flow, and the error/recovery flow.

---

### 2. Interaction States

For every interactive element and every screen, define all reachable states. Do not leave implicit states to the Product Engineer to invent.

| Element / Screen | States | Notes |
|---|---|---|
| [e.g., Submit button] | default, loading, success, error, disabled | Error state shows inline message |
| [e.g., Dashboard] | empty, loading, populated, error | Empty state has CTA, not a blank screen |

Every screen must have: loading, empty, error, and success states defined.

---

### 3. Design System Direction

Reference `DESIGN.md`. Specify which tokens, components, and patterns this feature uses. Flag any new components or token changes needed.

**Using existing:**
- [Component or token name and how it applies here]

**New components needed:**
- [Name, purpose, and key behavior — enough for Senior Designer to implement]

**Token changes needed:**
- [Name the token, the change, and why]

If no changes are needed, write: "No design system changes required. All components and tokens are available in DESIGN.md."

---

### 4. Platform Matrix

Define behavior per platform. If the product is web-only, this section confirms that. If it targets both web and mobile, every behavior difference must be named.

| Behavior | Web | iOS (Expo) | Notes |
|---|---|---|---|
| [e.g., Push notifications] | No | Yes (APNs) | Requires opt-in prompt |
| [e.g., File upload] | Drag-and-drop + picker | Device photo/file picker | Max 10MB both |

**Shared behaviors (identical across platforms):**
- [List behaviors that are identical — no duplication needed in implementation]

**Platform-specific behaviors:**
- [List each divergence explicitly]

---

### 5. Error and Edge Cases

Name every error condition the user might encounter and what the product does in each case.

| Scenario | User sees | System behavior |
|---|---|---|
| [e.g., Network offline during submit] | "No connection. Your work is saved." toast | Queue the request, retry on reconnect |
| [e.g., Auth session expired] | Redirect to login with return URL | Preserve in-progress form state in sessionStorage |
| [e.g., Empty state — no data yet] | Illustrated empty state with CTA | Show onboarding CTA, not blank |

---

### 6. Copy and Microcopy

Name every user-visible string that requires product judgment. Do not leave strings as "[placeholder]" in the spec.

| Location | Copy | Notes |
|---|---|---|
| [e.g., Activation CTA] | "Start your first project" | Not "Get started" — names the action |
| [e.g., Error message — upload failed] | "Upload failed. Try again or use a smaller file." | Actionable, not just "Error" |
| [e.g., Empty state headline] | "Nothing here yet" | Followed by CTA button |

---

### 7. Accessibility Requirements

List the accessibility bar this feature must meet. Default is WCAG 2.1 AA unless a higher bar is explicitly approved.

- Minimum contrast ratio: 4.5:1 for body text, 3:1 for large text and UI components
- All interactive elements have keyboard focus states
- All images have alt text
- All form inputs have visible labels (not placeholder-only)
- All modals trap focus and return focus on close
- [Any feature-specific requirements, e.g., "screen reader label for the drag-and-drop upload zone"]

---

### 8. Analytics Events

Name every event that must be tracked to measure the activation metric, retention mechanic, and success criteria defined in Step 1.

| Event name | Trigger | Properties |
|---|---|---|
| `[feature]_started` | User begins the core flow | `user_id`, `source` |
| `[feature]_completed` | User reaches the terminal state | `user_id`, `duration_seconds` |
| `[activation_event]` | User reaches the activation moment | `user_id`, `method` |

Minimum events required: one for flow start, one for flow completion, one for the activation moment.

---

### 9. Onboarding Flow (cold-start new-user journey)

Define the complete experience for a user who has never used the product before. This section is required for every release that introduces a new primary flow.

**Entry point:**
> [Where does the new user land? e.g., "Redirected to /onboarding after email verification"]

**First-run empty state:**
> [What does the user see before they have done anything? Describe the screen state — not a blank page.]

**First action prompt:**
> [What does the product ask the user to do first? One clear CTA. Name the copy.]

**Guided steps (if applicable):**
1. [Step the product walks the user through]
2. [Step]
3. [Terminal state — what does "onboarding complete" look like?]

**Activation moment:**
> [The specific moment that matches the B2C activation metric from Step 1. Describe exactly what the user sees and does.]

**Skip / defer path:**
> [Can the user skip onboarding? If yes, what do they see instead? If no, explain why.]

**Return-user behavior:**
> [After onboarding is complete, what happens the second time the user opens the product? Does onboarding ever appear again?]

---

## Step 4 — Self-Review

Before handing off, run `/plan-design-review` on this document to confirm the spec is complete and has no underspecified sections.

Fix any rated areas below 7 before handing to CTO. Do not hand off a spec with open questions in Sections 1–5 or a missing onboarding flow.

---

## Done Criteria

- [ ] All 9 CEO brief fields confirmed (including 4 B2C fields)
- [ ] DESIGN.md exists and is current
- [ ] All 9 spec elements completed — no TBDs, no blank sections
- [ ] User flows cover: activation, returning-user, and error/recovery
- [ ] Every interactive element has all reachable states defined
- [ ] Platform matrix covers all target platforms
- [ ] Onboarding flow covers: entry point, empty state, first action, activation moment, and return-user behavior
- [ ] Analytics events cover activation metric and success criteria
- [ ] `/plan-design-review` run and all sections rated ≥ 7
- [ ] Handoff comment written using `templates/HANDOFF.md` and addressed to CTO

---

## Handoff

Use `templates/HANDOFF.md`. Addressed to: **CTO**.

The CTO uses this document as the primary input for the technical execution plan. Every section must be complete — the CTO should not need to ask the Senior Designer to fill in missing states, copy, or platform behavior during planning.
