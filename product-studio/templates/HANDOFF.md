# Product Studio Handoff Template

Use this template when one stage hands work to the next stage.

## Required Shape

- Stage completed
- Artifact ready
- Next owner
- Risk to preserve
- Skills used

Do not leave ownership implicit. Reassign the Paperclip issue after posting the handoff comment.

## Single-Owner Handoff

Use this shape for every normal stage transition:

```md
## Update

- Stage completed: `Brief` | `Experience spec` | `Technical plan` | `Structural review` | `Release` | `QA`
- Artifact: `<file, branch, environment, or report>`
- Next owner: `CEO` | `Senior Designer` | `CTO` | `Staff Engineer` | `Release Engineer` | `QA Engineer`
- Risk to preserve: `<one concrete thing the next owner must not lose>`
- Skills used: `<skill slugs>`
```

Use explicit reassignment after the comment:

```http
PATCH /api/issues/{issueId}
Authorization: Bearer $PAPERCLIP_API_KEY
Content-Type: application/json
X-Paperclip-Run-Id: $PAPERCLIP_RUN_ID

{
  "assigneeAgentId": "{nextAgentId}",
  "status": "todo",
  "comment": "## Update\n\n- Stage completed: ...\n- Artifact: ...\n- Next owner: ...\n- Risk to preserve: ...\n- Skills used: ..."
}
```

## Paired Build Handoff

The `CTO` to implementation transition is the only approved paired-stage exception.

Use this shape:

```md
## Update

- Stage completed: `Technical plan`
- Artifact: `<execution plan plus shared review target>`
- Next stage: `Paired build`
- Backend owner: `Product Engineer`
- Frontend owner: `Senior Designer`
- Coordinating owner: `CTO`
- Shared review target: `<branch, PR, or working tree target Staff Engineer will review>`
- Risk to preserve: `<ownership split or integration risk>`
- Skills used: `<skill slugs>`
```

Paperclip issue ownership still stays single-owner:

- assign the issue to `Product Engineer`
- name `Senior Designer` in the comment as the required paired frontend owner
- do not assign the issue to `CTO` unless the build stage is blocked and needs replanning

## Blocked Handoff

If the next stage cannot start, do not fake progress. Patch the issue to `blocked` and name:

- what is blocked
- which artifact is missing or stale
- who must act next
- whether the blocker is a `CEO` scope problem or a `CTO` execution problem

## Local Rules

- Keep comments short and operational.
- Name the artifact, not just the intent.
- Use `Skills used:` with actual local skill slugs.
- For the paired build stage, never describe the work as undifferentiated collaboration.
- If the next stage needs a file, branch, environment, or verdict, that thing must already exist when you hand off.
