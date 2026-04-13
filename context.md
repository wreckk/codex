# Codex Project Context

This file is the handoff document for continuing work on `wreckk/codex` across machines.

## Project

- Repo: `https://github.com/wreckk/codex`
- Deploy: Vercel project connected to `main`
- Site type: static HTML/CSS/JS
- Main files:
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/index.html`
  - `/Users/ericcenteno/Desktop/Projects/Vibe Coding/codex/styles.css`

## Workflow

- Paper is the visual working surface.
- Code should stay aligned to the Paper frame.
- When changing UI, update Paper and code together whenever possible.
- If switching machines, pull latest repo state first, then continue from this file.

## Paper Context

- Paper file: `codex`
- Main artboard: `codex / index`
- Reference artboard: `Timeline ex`

Use `codex / index` as the source for the current page.
Use `Timeline ex` as a visual reference for the timeline treatment.

## Current Layout

Three-column editorial layout:

- Left: identity rail
- Middle: vertical timeline
- Right: active story card

Current column split in code:

- left: `3fr`
- middle: `2fr`
- right: `5fr`

## Current Design Direction

### Left Column

- Name: `ERIC CENTENO`
- Subtitle: `EXECUTIVE DESIGN LEADER`
- Portrait uses two headshot images from `ericcenteno.com`
- `Hey There` hover pill remains part of the concept
- Bio sits beside and beneath the portrait
- Strengths and Interests live below the link row

### Middle Timeline

- Timeline starts in `2026`
- `TODAY` is the first active work item
- Years should behave as real scrolling items, not fake label swaps
- Only one active tick/item should be highlighted at a time
- No duplicate visible years
- Long ticks are for labeled items
- Medium ticks are currently removed
- Small ticks form the baseline ruler rhythm

### Right Column

- White card background
- Date/kicker at top
- Serif headline
- Placeholder story copy for all active states for now
- Placeholder pills/chips for now
- Placeholder image block for now

## Known User Preferences

- No black copy; use the muted/plum family instead
- Paper typography/spacing is preferred over browser approximations
- Right-column spacing should match Paper more closely
- Left-column title should feel tightly fitted to the column width
- Subtitle should visually span the width cleanly
- Timeline month-to-label spacing should stay tight
- Long tick should touch the pill border

## Current Content Rules

- Right panel should be driven by month-level items, not by year-level summary items
- `TODAY` should behave like any other callout item, just first by default
- Dummy/FPO content is acceptable on the right for now

## Git / Auth Notes

This machine pushes via local git over HTTPS using macOS keychain:

- remote: `https://github.com/wreckk/codex.git`
- credential helper: `osxkeychain`

Useful checks on another machine:

```bash
git remote -v
git config --get credential.helper
git config --get user.name
git config --get user.email
git push --dry-run
```

If needed:

```bash
git config --global credential.helper osxkeychain
git config --global user.name "Eric Centeno"
git config --global user.email "7010862+wreckk@users.noreply.github.com"
```

## How To Resume

On another machine, the fastest handoff prompt is:

`Pull the latest repo state, read context.md, then continue work on codex using Paper as the visual source of truth.`

## Open Issues / Next Refinements

- Browser typography still needs to match Paper more closely
- Timeline year push behavior may still need tuning in the live site
- Left-column title fit can still be refined if the name feels too small or too clipped
- Right-column spacing should be checked against Paper after each major layout tweak
