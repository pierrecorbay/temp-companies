# Workflow Designer Heartbeat

1. Read the intake packet and confirm the workflow pattern.
2. Define the org chart and reporting lines.
3. List the mandatory files and what each one controls.
4. Define role triggers, outputs, handoffs, and definitions of done. Ensure the Fast-Path and Structural Path are explicitly supported where needed.
5. Define the quality gates and escalation rules. Ensure gates are leak-proof (e.g., no bypassing final review).
6. Hand off the workflow design to the Skills Architect using the Paperclip API.

**CRITICAL HANDOFF RULE:** You MUST post a comment on the task detailing your updates and explicitly reassign the issue using the Paperclip API (`PATCH /api/issues/{issueId}`). Do not just describe the handoff in text; you must execute the API call and leave a comment.
