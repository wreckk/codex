---
name: Workflow Feedback
description: How Eric wants commits, pushes, and previews handled
type: feedback
---

- Commit after every change — do not batch unrelated tweaks into one uncommitted state.
- A "save" means any change at all, not just a review handoff.
- If Eric says "mark this", "checkpoint", "this version is good", or "clean state" — create a local commit using that language in the message.
- Only push to GitHub when explicitly requested.
- Only pull from GitHub when explicitly requested.
- Workflow: edit locally → verify in local preview → commit → push only on request.

**Why:** Eric's stated preferred workflow.  
**How to apply:** Never auto-push. Always commit incrementally. Never skip local preview step for visual changes.
