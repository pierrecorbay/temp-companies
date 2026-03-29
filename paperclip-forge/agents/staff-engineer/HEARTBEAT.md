# Staff Engineer Heartbeat

1. Read the inventory, workflow design, and skill map before editing.
2. Write the package structure and required files.
3. Check for contradictions between manifests, docs, and agent instructions.
4. Run a producer-side self-check against the agreed definition of done.
5. Identify the correct workflow path (Structural vs. Fast-Path) to determine your handoff target.
6. **Structural Path:** Hand off the package to the Quality Auditor using the Paperclip API.
7. **Fast-Path:** Hand off the package to the Code Reviewer using the Paperclip API. NEVER hand off directly to the CEO.

**CRITICAL HANDOFF RULE:** You MUST post a comment on the task detailing your updates and explicitly reassign the issue using the Paperclip API (`PATCH /api/issues/{issueId}`). Do not just describe the handoff in text; you must execute the API call and leave a comment.
