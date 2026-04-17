---
name: Project Context
description: timeline — personal portfolio timeline site, key files, stable baselines, and content notes
type: project
---

Repo: https://github.com/wreckk/timeline  
Branch: main  
Local path: /Users/ericcenteno/Desktop/Projects/Vibe Coding/timeline

**Primary source files:**
- `index.html` — layout and behavior
- `styles.css` — styling
- `timeline-content.json` — all timeline/story content (source of truth)

**Local preview:** `python3 -m http.server 4173` → http://localhost:4173  
Same-network mobile: http://192.168.1.102:4173

**Asset locations:**
- Employer logos: `assets/company-logos/employers/`
- AI montage logos: `assets/company-logos/ai-logos/`
- GLP-1 gallery images: `assets/images/examples-glp1/` (01–04, shown in filename order)

**Stable baselines (do not revisit unless asked):**
- Mobile timeline is spine-anchored
- EXPERIENCE row sits in normal flow above compact rail
- Compact startup centering and reverse-order behavior
- Compact active-pill behavior
- Employer pill beside EXPERIENCE is correct model
- COMPANY • YEAR inside content card stays plain text
- Employer pill fallback text: "Highlight" (softer gray); non-company items preserve row height

**2026 timeline order:** 👋 Welcome → Closer to the Work → Taking a Break → GLP-1 Launch

---

## Closer to the Work montage

- Lighter gray radial background, frosted logo containers, loose non-uniform placement
- AI logo tiles light up only when clicked by cursor (whole frosted tile, soft highlight)
- Cursor moves deliberately with pulse feedback on click; all tiles get clicked over full loop
- AI input: 90% width, 10px bottom margin, prompt left-aligned ~20% inset
- Send button ~20% from right, points up, turns orange when typing finishes
- Prompt sequence: type → hold → send highlights → text flies up/blurs/fades → next prompt

## GLP-1 Launch gallery

- Headline: 💉 GLP-1 Launch
- Pills: Live Prototype → https://glp-1.ericcenteno.com, Subscription, Growth, Product Vision
- Description: Original approach through AI exploration to the final shipped experience.
- Not a carousel; images load full-width, top-aligned, scroll page-down style with pauses
- Never scroll past bottom; after final pause: crossfade + blur + zoom to next screen
- Faux cursor: top-right quadrant, glass styling, simple flick
- Light visible border on sample container, must not clip at rounded corners

## Welcome example

- Mobile: custom cards + faux timeline, bottom-fixed, card size intentionally smaller, top spacing ~25px, spacing via layout offsets not padding
- Desktop: tick opacity softened to ~70%; sidebar title/name fit is sensitive during live resize

## Responsive / sidebar fit

- Compact breakpoint: 960px; narrow desktop band: 1280px → 961px
- Name/logo line: resizes by font-size only, always expands to full width when room available
- Title/role line: tracking-led full-width fit, especially sensitive around 1280px+
- Uses live computed baseline reads, ResizeObserver + double-rAF scheduling, no sidebar breakpoint snaps at 1280px
- If title underfills/clips: inspect `fitSidebarHeading()` in `index.html`, verify desktop "extra room" path for `sidebarRole`, verify no CSS breakpoint override shrinking `.sidebar-heading p`

## Story fade / scroll behavior

- Progressive fade/blur logic under story headline
- Sensitive — avoid hard clipping edge near top mask/cutline
