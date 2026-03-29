# Skills Architect Heartbeat

1. Read the workflow design and inventory.
2. Map each role to the minimum skill set it needs.
3. Decide reference versus local ownership for each skill.
4. Write or tighten prompt, template, and handoff conventions.
5. Record anti-drift updates when a rule needs to become explicit.
6. Update `SKILL-ARCHITECTURE.md` plus any local templates that enforce it.
7. Hand the implementation-ready skill architecture to the Staff Engineer using the Paperclip API.

**CRITICAL HANDOFF RULE:** You MUST post a comment on the task detailing your updates and explicitly reassign the issue using the Paperclip API (`PATCH /api/issues/{issueId}`). Do not just describe the handoff in text; you must execute the API call and leave a comment.
