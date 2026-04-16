# Codex Project Context

This file is the handoff doc for continuing work on `wreckk/codex` across machines.

## Project

- Repo: `https://github.com/wreckk/codex`
- Branch: `main`
- Site type: static site driven by:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/index.html`
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/styles.css`
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/timeline-content.json`

## Workflow

- Preferred workflow:
  1. edit locally
  2. verify in local preview
  3. only push when explicitly requested
- Local preview URL:
  - `http://localhost:4173`

### Local server

From repo root:

```bash
cd "/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex"
python3 -m http.server 4173
```

## Important Workflow Rule

This project uses an explicit local-commit workflow.

### Required behavior

- Every save gets a local commit.
- A “save” means any round of work that is handed back for review locally.
- Do not wait for the user to separately ask to save it.

### User callouts

If the user says things like:

- `mark this`
- `checkpoint this`
- `this version is good`
- `clean state`

that should still create a local commit, and that phrasing should influence the commit message so rollback is easy later.

### Push / pull rules

- The user will be explicit about pushing to GitHub.
- Do not push unless explicitly requested.
- The user will be explicit about pulling from GitHub.
- Do not pull unless explicitly requested.

### Why

The user wants to be able to say things like:

- `roll back 2 versions`
- `go back to the good checkpoint`

and have that mean rolling back through local commits, not guessing from uncommitted working state.

## Source Of Truth

- Content source of truth:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/timeline-content.json`
- Layout / interaction source of truth:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/index.html`
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/styles.css`

## Current Layout Model

### Desktop

- Three-column editorial layout
- Left: profile / bio / strengths / interests / links
- Middle: vertical timeline
- Right: story/content card
- Desktop timeline focus line is now around `25%` from the top

### Tablet

- Left and right cards remain similar to desktop
- Timeline is a fixed bottom rail
- Tablet uses its own mask / rail behavior and should not be casually merged with desktop fixes

### Mobile

- Top: compact left-card summary
- Middle: story/content card
- Bottom: fixed horizontal timeline rail
- Mobile spacing is very sensitive
- Desktop-only timeline fixes must stay desktop-only unless explicitly requested

## Timeline State

### Desktop

- Active item focus is aligned to the desktop focus lane near `25%`
- Desktop timeline items are clickable and auto-scroll into focus
- Desktop pinned year behavior was heavily tuned
- The scrolling desktop year labels use:
  - `.timeline-entry.year .entry-pill { left: -71px; }`
- Desktop year swap behavior currently depends on the year marker hitting the desktop trigger, not just story item activation

### Mobile

- Mobile year spacing was recently tightened and is considered acceptable right now
- Mobile timeline guide lines are currently OFF
- Mobile active item scaling issue was fixed by changing transform origin so the pill grows from center instead of dropping downward
- Mobile content card supports swipe left/right to move between timeline items
- Mobile timeline items can be tapped to scroll them into focus

## Current Story / Content Behavior

- Story card transitions:
  - desktop uses stronger vertical motion
  - mobile uses horizontal motion
  - content card transition blur is intentionally present
- Story image area supports:
  - real image
  - default FPO placeholder
  - animated no-image fallback for `Start Here` only

### First entries in 2026

Current first entries:

1. `Start Here`
2. `Closer to the Work`
3. `GLP-1 Launch`

### `Start Here`

- This is now the first entry before `Closer to the Work`
- It has:
  - no kicker
  - no chips
  - no note/caption under the fallback visual
- Copy:
  - `This is a timeline of some of my work over the years, and a few highlights along the way.`
  - `Scroll through the timeline to explore, details update as you move.`
- Its no-image state now uses a custom animated fallback graphic instead of the normal FPO container

### `Closer to the Work`

- Headline:
  - `Closer to the Work`
- Copy:
  - `Took a short career break to focus on how things actually get built now.`
  - `Spent the time working across design, prototypes, and code to stay sharp and hands-on.`
- Tags:
  - `Design + Code`
  - `Prototyping`
  - `AI Tools`
  - `Workflow`
  - `Craft`
- Real image asset:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/assets/images/ai.png`

## FPO / Image Behavior

### Real image

- `Closer to the Work` uses a real `<img>` from `/assets/images/ai.png`
- The real-image container grows to the image height instead of forcing the old fixed FPO box

### Default FPO container

- Non-updated / non-image stories are back to a plain centered `FPO` placeholder
- The animated fallback is NOT global anymore

### Animated fallback

- Only `Start Here` uses the animated fallback
- Current direction of that animation:
  - green box = default viewport
  - pink section scrolls in
  - blue section scrolls in
  - then the loop repeats
- The current structure is intentionally a `6 + 3 + 3` tick runner
- This area was still being refined at the end of the session, but the active goal is explicit:
  - no blank space during flicks
  - first flick reveals the next 3 ticks
  - second flick reveals the next 3 ticks
  - then loop

## Current Labels / Pills

- Fallback milestone/company pill label is now:
  - `Highlights`
- `Taking a Break` was replaced by:
  - `Closer to the Work`

## Mobile UI Details

### Scroll hint

- Mobile has a delayed hint:
  - `Scroll To`
  - `See More`
- Chevron sits to the left of the two-line label
- It only appears after `25s` of no timeline scrolling
- Once the user scrolls the timeline, it should stay dismissed

### Header pullbar / arrow

- Mobile header pullbar is an idle animation now
- Intended sequence:
  - flat line
  - transform to down arrow
  - bounce twice
  - flatten again
- This was refined a lot and is still delicate

## Visual Details

- Story image border is now a dedicated overlay on `.story-image-shell`
- The visible image object border was lightened and made thinner
- Real image / FPO shell behavior is intentionally different depending on state

## Strengths / Interests

### Strengths

- `ORG SCALE`
- `EXECUTIVE PARTNERSHIP`
- `DESIGN SYSTEMS`
- `GROWTH & MONETIZATION`
- `UX RESEARCH`
- `VIBE-CODING`
- `BRAND DESIGN`
- `AI PROTOTYPING`
- `VOICE & TONE`
- `0–100 INITIATIVES`
- `CULTURE BUILDING`
- `SAAS & B2B`

### Interests

- `CLASSIC GAMING`
- `COFFEE`
- `BIRD WATCHING`
- `HOME NETWORKING`
- `SNEAKERS`
- `PC BUILDING`
- `COMICS`
- `STREET WEAR`
- `DADDING`
- `VINYL & MINIDISC`
- `COOKING`
- `SMART HOME`
- `3D PRINTING`
- `PHOTOGRAPHY`
- `THE GOLDEN GIRLS`

## Latest Pushed State

- Latest pushed commit at handoff time:
  - `57c9391`

That includes:
- `Start Here` note/caption removed
- animated fallback only on `Start Here`
- plain FPO placeholder restored for other non-image stories
- real image for `Closer to the Work`

## Resume Prompt

Use this on the laptop:

`Pull latest main, read /Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/context.md, then continue locally. Respect the current mobile spacing, desktop year logic, and the rule that only Start Here uses the animated FPO fallback.`
