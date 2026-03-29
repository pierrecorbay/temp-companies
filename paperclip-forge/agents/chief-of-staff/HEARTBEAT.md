# Chief Of Staff Heartbeat

1. Read the CEO decision and confirm the engagement mode.
2. Inventory the current company, repo, or source materials.
3. Update `PROJECT-INVENTORY.md`.
4. Summarize the desired outcome, constraints, source companies, and risks.
5. Prepare a clean handoff for the Workflow Designer using the Paperclip API.
6. Return the intake packet to the CEO only if scope or source ambiguity blocks the workflow.

**CRITICAL HANDOFF RULE:** You MUST post a comment on the task detailing your updates and explicitly reassign the issue using the Paperclip API (`PATCH /api/issues/{issueId}`). Do not just describe the handoff in text; you must execute the API call and leave a comment.
