# Codex Project Context

This file is the handoff document for continuing work on `wreckk/codex` across machines.

## Project

- Repo: `https://github.com/wreckk/codex`
- Production branch: `main`
- Site type: static `index.html` / `styles.css` / JSON content
- Primary working files:
  - `/Users/wreckk/Desktop/Projects/Vibe Coding/Codex/index.html`
  - `/Users/wreckk/Desktop/Projects/Vibe Coding/Codex/styles.css`
  - `/Users/wreckk/Desktop/Projects/Vibe Coding/Codex/timeline-content.json`

## Current Workflow

- Local preview first, do not rely on Vercel for iteration.
- The preferred workflow is:
  1. edit locally
  2. refresh local preview on desktop/mobile
  3. only push when explicitly requested
- Local preview has been used successfully across devices on the same network.
- If resuming on another machine, pull latest repo state first, then read this file.

## Local Preview

- This machine is currently running a simple local server on port `4173`.
- The current process is a Python server listening on `*:4173`.
- Local preview URL:
  - `http://localhost:4173`
- Same-network mobile testing URL should use the current machine IP with that same port.

### Recommended local server command

From the repo root:

```bash
cd "/Users/wreckk/Desktop/Projects/Vibe Coding/Codex"
python3 -m http.server 4173
```

Then open:

```bash
http://localhost:4173
```

If testing on another device on the same network, use:

```bash
http://<your-local-ip>:4173
```

## Source Of Truth

- Content source of truth is now:
  - `/Users/wreckk/Desktop/Projects/Vibe Coding/Codex/timeline-content.json`
- The old markdown planning doc is no longer the source of truth.
- Timeline `order` numbers in the JSON are internal sequencing only.

## Current Layout Model

### Desktop

- Three-column editorial layout
- Left: profile / bio / strengths / interests / links
- Middle: vertical timeline
- Right: story/content card

### Tablet

- Left/right content remains visually similar to desktop
- Timeline is moved to a fixed bottom rail
- Tablet still has some known roughness, but the current geometry was considered acceptable enough to move on

### Mobile

- Top: compact accordion version of the left card
- Middle: right/story content card
- Bottom: fixed horizontal timeline rail
- Mobile timeline/header spacing is very sensitive and should be treated carefully

## GOOD Baseline

If someone says “go back to the good version”, they mean the state after these were working together:

- mobile tick/spine behavior is correct
- compact startup centering/callout handling is correct
- compact reorder animation is correct
- current timeline/header spacing model is correct
- current active pill animation is correct

### Important Mobile Timeline Rules

- The mobile timeline shell is fixed to the bottom of the viewport.
- The `EXPERIENCE` row is in normal flow above the rail, not absolutely floated over it.
- If spacing is added above/below the `EXPERIENCE` row, the shell height should increase rather than nudging rail geometry independently.
- The mobile rail model is easiest to reason about as:
  - header region
  - gap under header
  - rail/ticks region
  - year region
- Tick orientation matters:
  - the spine is the anchor
  - tick height should conceptually grow upward from the spine
  - do not casually “fix” tick height by changing unrelated offsets

## Current Timeline / Content Behavior

- Compact timelines center the first visible item on initial load in either direction.
- In forward mode, the first/current item should be centered on load.
- In reverse mode, the earliest item should also be centered on load.
- Callouts do not drive the story card.
- If a centered item is a callout, the story card clears instead of selecting another work item.
- The reorder toggle now rebuilds the rail from the new start side rather than jumping to the far end.
- Compact year locking uses the newer pin/lock treatment and was being refined; do not assume old fake-overlay experiments are valid.

## Current Company / Identity Behavior

- The employer pill lives beside `EXPERIENCE` in the timeline header.
- The content card no longer uses a separate company pill.
- The `COMPANY • YEAR` line in the content card should remain plain text.
- For non-company items, use a `MILESTONE` pill/state in the timeline header so the header row remains stable.
- Callouts inherit the employer grouping they belong to.
- `Taking a Break` is a non-company item and should behave like a milestone.

### Employer Pill Transition Intent

- The header employer pill should never disappear during a swap.
- The pill shape stays present.
- Width stretches/compresses to fit the next label.
- Background/border color crossfades.
- Label text can blur/fade in/out.
- The transition should feel like one persistent pill morphing, not a pill blinking out and a new one appearing.

## Current Story Card Behavior

- The story card uses a faint top-left company tint.
- FPO screens are now neutral gray.
- Story image area is a container, not treated as a final image layout.
- The `COMPANY • YEAR` kicker sits above the story title as plain text.
- Headline-to-paragraph spacing was tightened recently.

### Scroll / Fade Behavior

- The previous hard white header mask was removed.
- Story content now experiments with scroll-driven fade/blur.
- The desired effect is:
  - no hard clipping line
  - fade should begin before content crosses the cutoff
  - text should fade progressively, not as one instant block
- This area is still being refined locally.

## Current Content Notes

- `timeline-content.json` is the living content document.
- `2026` order is:
  1. `Taking a Break`
  2. `GLP-1 Launch`
- `McDonald’s` is a callout and should not become an active selected story.

## Current Employer Colors

- GoodRx: `#FDDB00`
- Outreach: `#4F47EA`
- Slack: `#4A154B`
- Disney: `#36A3D7`
- AWeber: `#1173BC`
- Navan: `#8C2988`
- Okayplayer: `#000000`

## What Is Already Pushed

- Latest pushed checkpoint at the time of this handoff:
  - commit `9f6d568`
- That push included:
  - plain-text `COMPANY • YEAR`
  - employer pill beside `EXPERIENCE`
  - timeline/content transition refinements
  - progressive text fade work in progress

## Current Local-Only State

There are currently unpushed local edits in:

- `/Users/wreckk/Desktop/Projects/Vibe Coding/Codex/index.html`
- `/Users/wreckk/Desktop/Projects/Vibe Coding/Codex/styles.css`

These local changes are mainly:

- content card `COMPANY • YEAR` remains plain text with no background
- `story-scroll` top padding forced to `0`
- employer pill beside `EXPERIENCE` stays visible during company/milestone swaps and morphs instead of disappearing
- story scroll fade/blur behavior is still being tuned to avoid hard clipping

If resuming on another machine and you need the exact local state, copy these unpushed changes first or push them before switching.

## Resume Prompt

On another machine, the fastest handoff prompt is:

`Pull latest repo state, read context.md, then continue working on codex locally. Respect the current mobile timeline “good baseline” and do not casually rework the tick/header spacing model.`
