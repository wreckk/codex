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
- Commits and pushes should just happen silently when triggered. Do not narrate permission dialogs, do not ask whether to add allowlist entries, do not turn auth flow into a conversation. If a permission prompt is needed once, configure it and move on.

**Why:** Eric's stated preferred workflow; reinforced 2026-04-17 after I walked him through a permission-denial → allowlist → retry loop instead of silently handling it.
**How to apply:** Never auto-push. Always commit incrementally. Never skip local preview step for visual changes. Treat permission configuration as plumbing, not a decision to surface.
