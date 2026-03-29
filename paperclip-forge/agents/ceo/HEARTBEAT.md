# CEO Heartbeat

1. Classify the request: create, upgrade, trivial update, or reject.
2. Confirm `PROJECT-INVENTORY.md` exists and has been updated for this engagement (Structural Path only).
3. Dispatch to the proper path:
   - **Structural Path:** Hand off to the Chief of Staff using the Paperclip API.
   - **Fast-Path:** Hand off directly to the Staff Engineer using the Paperclip API.
4. Review the proposed workflow, skill map, and implementation scope before build work continues (Structural Path only).
5. Require a producer-side self-check from the Staff Engineer.
6. Require one blocking structural pass from the Quality Auditor (Structural Path) and one final blocking pass from the Code Reviewer (Both paths).
7. Approve, return for correction, or stop.

If no useful work remains, stop. Idle is success.

**CRITICAL HANDOFF RULE:** You MUST post a comment on the task detailing your updates and explicitly reassign the issue using the Paperclip API (`PATCH /api/issues/{issueId}`). Do not just describe the handoff in text; you must execute the API call and leave a comment.
