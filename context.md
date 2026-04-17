# Codex Project Context

This is the handoff doc for continuing work on `wreckk/codex` across machines.

## Project

- Repo: `https://github.com/wreckk/codex`
- Branch: `main`
- Current local repo path:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex`
- Primary source files:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/index.html`
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/styles.css`
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/timeline-content.json`

## Workflow

- Preferred workflow:
  1. edit locally
  2. verify in local preview
  3. only push when explicitly requested
- Every local save / reviewable state should get a local commit.
- If Eric says `mark this`, `checkpoint`, or `good version`, use that language to shape the commit message.
- Only pull from GitHub when explicitly requested.

### Local preview

From repo root:

```bash
cd "/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex"
python3 -m http.server 4173
```

- Desktop URL:
  - `http://localhost:4173`
- Same-network mobile URL:
  - `http://192.168.1.102:4173`

## Source Of Truth

- Timeline/story content:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/timeline-content.json`
- Layout and behavior:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/index.html`
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/styles.css`

## Stable Baseline

Treat the current timeline behavior as the good baseline unless explicitly revisiting it:

- mobile timeline is spine-anchored and considered stable
- `EXPERIENCE` row sits in normal flow above the compact rail
- compact startup centering and reverse-order behavior are stable
- compact active-pill behavior is stable
- employer pill beside `EXPERIENCE` is the correct model
- `COMPANY • YEAR` inside the content card should stay plain text

## Current Timeline Content Notes

### 2026 order

Current order in `2026`:

1. `👋 Welcome`
2. `Closer to the Work`
3. `Taking a Break`
4. `GLP-1 Launch`

### `👋 Welcome`

- This replaced `Start Here`
- The timeline pill uses the waving-hand animation
- It keeps the custom faux timeline animation in the image area
- Current copy:
  - `Thanks for stopping by. This is a timeline of some of my work over the years, with a few highlights mixed in.`
  - `Scroll through to explore, the details update as you move through each moment, unfolding as you go.`

### `Closer to the Work`

- This story now uses a custom AI-tools montage instead of a normal real image
- It should keep the lighter gray radial background
- It should keep the frosted logo containers and loose, non-uniform placement
- The montage now uses:
  - AI logo tiles
  - a faux cursor click path
  - a docked AI input screenshot at the bottom
  - typed prompt animation

## `Closer to the Work` Montage Intent

This is the most recent active refinement area.

### What should remain true

- use assets from:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/assets/company-logos/ai-logos`
- use employer logos from:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/assets/company-logos/employers`
- frosted tiles and varied placement are correct
- the AI input should sit on top of the icon layer
- the AI input should feel like a real prompt field rather than a generic tile

### Current desired behavior

- app tiles only light up when clicked by the cursor
- tile click should affect the whole frosted tile, not just the icon
- click state should be a soft highlight, not a full-white blast
- icon sizing should feel visually balanced across all apps
- cursor should show click feedback with a pulse under it
- cursor should move deliberately, not too fast
- all app tiles should eventually get clicked over the full loop

### AI input behavior

- width should be about `90%`
- bottom margin should be `10px`
- prompt text should be left aligned in the real text-entry zone, with about `20%` left inset
- send button should sit farther left than a default right edge placement, roughly with `20%` right inset
- send button should point upward correctly
- when prompt finishes typing, send button should turn orange
- prompt sequence should be:
  1. type in letter by letter
  2. hold briefly
  3. send button highlights/clicks
  4. text flies up, fully blurs, and fully fades out
  5. next prompt begins

## Asset Organization

The logo assets were reorganized.

- employer logos now live in:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/assets/company-logos/employers`
- AI montage assets live in:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/assets/company-logos/ai-logos`

If employer logo rendering breaks, check `COMPANY_LOGOS` in `index.html` first and make sure it still points at `employers/...`.

## Current Employer Pill Behavior

- employer pill stays beside `EXPERIENCE`
- fallback pill text is:
  - `Highlight`
- fallback pill is a softer gray
- non-company items should still preserve row height / alignment

## Current Story Fade / Scroll Behavior

- text under the story headline is using progressive fade/blur logic
- this area is still sensitive and easy to overdo
- avoid bringing back a hard clipping edge near the top mask/cutline

## `💉 GLP-1 Subscription`

- Headline:
  - `💉 GLP-1 Subscription`
- Text:
  - `I stepped into the work when it wasn’t really landing and pushed to reset the direction.`
  - `Built a new vision in under 48 hours, tying product and brand together in a way that finally clicked.`
  - `Ended up being the most successful launch to date, ~1200% MoM subscription growth.`
- Pills:
  - `Live Prototype` → `https://glp-1.ericcenteno.com`
  - `Subscription`
  - `Growth`
  - `Product Vision`
- Description:
  - `Original approach through AI exploration to the final shipped experience.`

### GLP-1 example behavior

- Local gallery assets live in:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/assets/images/examples-glp1`
- Files are numbered and should be shown in filename order:
  1. `01 -  version 1.png`
  2. `02 - ai v1.png`
  3. `03 - ai v2.png`
  4. `04 - shipped.png`
- The gallery is not a carousel.
- Each image should:
  - load full-width
  - be top-aligned
  - pause
  - scroll in page-down style steps
  - pause between each step
  - never scroll past the bottom of the image
- After the final pause, transition to the next screen with:
  - crossfade
  - blur
  - zoom
- The faux cursor should:
  - live in the top-right quadrant
  - use the shared glass cursor styling
  - flick simply, not over-animate
- The sample container uses a very light visible border. Current work recently focused on making sure the border does not clip at the rounded corners.

## Welcome Example Notes

- Mobile `👋 Welcome` has a custom cards + faux timeline example.
- Important mobile layout rules:
  - card size is intentionally smaller than earlier revisions
  - faux timeline stays bottom-fixed
  - card/tick spacing is controlled by layout offsets, not by shrinking the card via padding
  - top spacing should stay around `25px`

## Last Known Good Push

- Most recent pushed state should include the context from the commits after `b13acb7`, including:
  - custom `Welcome` example work
  - `Closer to the Work` AI montage
  - `GLP-1 Subscription` gallery behavior
