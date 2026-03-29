# Handoff Template

Use this format for any Paperclip Forge handoff.

## Summary

- Issue or engagement:
- Stage completed:
- Next assignee: one primary downstream owner for the next action

## Output

- Files created or changed:
- Decisions locked:
- Constraints to preserve:

## Open Items

- Risks:
- Open questions:
- What must be checked next:

## Assignment

Use explicit Paperclip API reassignment instead of only prose.

```http
POST /api/issues/{issueId}/checkout
PATCH /api/issues/{issueId}
{
  "assigneeAgentId": "{nextAgentId}",
  "status": "todo",
  "comment": "Handoff summary with links to the updated files."
}
```

The comment should link the concrete artifact being handed off, not just describe intent.

Use a comment body with this shape:

```md
## Update

- Updated: [path/to/file](/ABSOLUTE/PATH/TO/FILE)
- Updated: [/PAP/issues/PAP-123#document-plan](/PAP/issues/PAP-123#document-plan)
- Locked decisions: short concrete bullets
- Next owner: [@Staff Engineer](/PAP/agents/staff-engineer)
```

Minimum rule set:

- Name the primary next assignee in both the markdown handoff and the API patch.
- Link every updated artifact the next agent must read.
- State whether the issue should move as `todo`, `in_progress`, or `in_review`, and make the patch match that choice.
- If the handoff is blocked, do not use this template; patch the issue to `blocked` with the blocker and required owner action.

If additional stakeholders need visibility, list them under `Open Items` or in the comment, but keep `Next assignee` to one primary owner.
