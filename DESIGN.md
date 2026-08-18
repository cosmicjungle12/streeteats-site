---
name: StreetEats (Landing Site)
description: Marketing site for StreetEats — live street-food map, vendor beta signup.
colors:
  deep-market-green: "#1C3A2F"
  paprika: "#C4552B"
  butter-yellow: "#F9CF66"
  cream: "#F0ECE0"
  surface-white: "#FFFDF6"
  paper: "#FAF7EE"
  sign-ink: "#23201A"
  body-ink: "#3A362D"
  status-live: "#1FA55C"
  status-scheduled: "#F0B429"
  status-closed: "#D64545"
  status-inactive: "#A9A49A"
typography:
  display:
    fontFamily: "'Young Serif', Georgia, serif"
    fontWeight: 400
    lineHeight: 1.2
  body:
    fontFamily: "'Archivo', -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif"
    fontWeight: 400
    lineHeight: 1.6
  label:
    fontFamily: "'Archivo', sans-serif"
    fontWeight: 700
    fontSize: "0.78rem"
    letterSpacing: "0.1em"
rounded:
  sticker: "14px"
  btn: "12px"
  pill: "999px"
spacing:
  section: "2.6rem"
  block: "1.8rem 1.6rem"
components:
  btn-primary:
    backgroundColor: "{colors.deep-market-green}"
    textColor: "{colors.surface-white}"
    rounded: "{rounded.btn}"
    padding: "0.8rem 1.6rem"
  btn-primary-hover:
    backgroundColor: "{colors.deep-market-green}"
    textColor: "{colors.surface-white}"
  btn-soon:
    backgroundColor: "{colors.butter-yellow}"
    textColor: "{colors.sign-ink}"
    rounded: "{rounded.btn}"
    padding: "0.8rem 1.6rem"
  sticker-card:
    backgroundColor: "{colors.surface-white}"
    rounded: "{rounded.sticker}"
---

# Design System: StreetEats (Landing Site)

## Overview

**Creative North Star: "StreetEats Theme"** (shared name with the native app's DESIGN.md — this is the same visual system expressed for the web)

This is the marketing/landing surface (streeteats.live) for the StreetEats native app, built by Fable directly from the app's `theme.js` tokens, then hand-adapted for static HTML/CSS. It carries over the app's core identity faithfully: cream paper ground, thick ink borders, hard offset shadows, Young Serif headlines over uppercase Archivo Bold labels and buttons. As a **Persuade**-mode surface (the visitor decides and acts — join the beta, download the app), it takes one liberty the native app's Operate-mode surfaces don't: interactive hover feedback on the primary CTA, since hover is a legitimate web affordance with no equivalent on a native touch app.

Same anti-references as the app: no awning-stripe decoration (rejected as too busy), no glossy corporate food-delivery-app chrome. Component philosophy: hand-painted and sturdy, same as the app.

**Key Characteristics:**
- Same palette, border, and shadow language as the native app — this site should always read as "the same brand," not a separate marketing skin
- CSS custom properties (`:root { --green, --paprika, ... }`) are this project's token mechanism, defined per-page (no shared stylesheet yet — see Do's and Don'ts)
- One confirmed web-only exception to the app's shadow rules: the primary CTA's hover state shifts and shrinks its offset shadow to read as a physical press
- Static teardrop map-pin SVGs (identical path data to the native app's `PinMarker`) illustrate the four status colours directly in the legend grid

## Colors

Identical palette to the native app (see the app repo's `DESIGN.md` for the full role breakdown); this file only notes web-specific usage.

### Primary
- **Deep Market Green** (`#1C3A2F`): primary CTA fill, the "Starting in the South East" strip background, primary card shadow colour.

### Secondary
- **Paprika** (`#C4552B`): all links, the primary CTA's shadow colour (a web-specific choice — see Named Rules), section eyebrow labels, bullet markers.

### Tertiary
- **Butter Yellow** (`#F9CF66`): the wordmark pill, the "Coming soon" disabled-style badge button, the privacy page's small inline badge.

### Neutral
- **Cream** (`#F0ECE0`): page background.
- **Surface White** (`#FFFDF6`): sticker cards, buttons' text-on-green colour.
- **Paper** (`#FAF7EE`): text colour on the green strip section (paper-on-green, inverted from the app's usual ink-on-paper).
- **Sign Ink** (`#23201A`): headings, borders, button text.
- **Body Ink** (`#3A362D`): body copy.

### Named Rules
**The Status Color Lock Rule.** Same as the app: `--live` / `--sched` / `--closed` / `--inactive` appear only inside the four-pin legend grid, illustrating what the colours mean — never reused decoratively elsewhere on the page.

## Typography

**Display Font:** Young Serif (Google Fonts), falling back to Georgia.
**Body Font:** Archivo (Google Fonts, weights 400/500/700), falling back to the system sans stack.

**Character:** identical pairing logic to the app — a warm serif voice for headlines over a plain, confident grotesque for everything functional.

### Hierarchy
- **H1** (hero headline): `clamp(2rem, 6vw, 3.2rem)`, Young Serif, ink.
- **H2** (section headings): `clamp(1.5rem, 4vw, 2.1rem)`, Young Serif, centred.
- **H3** (card headings): `1.35rem`, Young Serif.
- **Body**: `1rem` base (`1.1rem` for the hero subhead), Archivo Regular, body-ink, 1.6 line-height.
- **Label** (`.label`, `.section-label`, button text): Archivo Bold, `0.78rem`–`0.9rem`, uppercase, `+0.08em` to `+0.1em` letter-spacing.

### Named Rules
**The Two-Font Discipline Rule.** Every page that renders brand type must load both Google Fonts (`Young+Serif` and `Archivo:wght@400;500;700`) via the same two `<link rel="preconnect">` + stylesheet pattern `index.html` uses. `privacy.html` was missing this (headings were silently falling back to Georgia, body text to system sans) until this pass added it — treat a missing font `<link>` on any new page as a bug, not a style choice.

## Layout

Single-column, centred `.wrap` container (`max-width: 960px`, `1.25rem` side padding) — no responsive breakpoints beyond one: `.split` (the customer/vendor two-column block) collapses to a single column under `720px`. Section rhythm is a flat `2.6rem` top/bottom padding per `<section>`. The legend grid and the customer/vendor split both use CSS Grid with `auto-fit`/explicit two-column patterns rather than a shared design-token spacing scale — this project has no formal spacing scale the way the app's `theme.js` does (see Do's and Don'ts).

## Elevation & Depth

Same hard, zero-blur, coloured offset shadow language as the app — `box-shadow: Npx Npx 0 <color>`, never a blurred/soft shadow. Roles observed: sticker cards and the privacy-page main panel use a green shadow (`4px 4px 0 var(--green)`); the wordmark pill and vendors-CTA card use paprika or ink shadows; the primary button uses a paprika shadow.

### Shadow Vocabulary
- **sticker** (`4px 4px 0 var(--green)`): legend cards, split blocks, privacy-page panel.
- **wordmark-pill** (`3px 3px 0 var(--ink)`): the header wordmark pill.
- **btn-primary** (`4px 4px 0 var(--paprika)`): the primary CTA button (resting state).
- **btn-soon** (`4px 4px 0 var(--green)`): the disabled-style "Coming soon" badge.

### Named Rules
**The Web Hover Exception Rule.** Unlike the native app (where shadows are purely structural and never respond to interaction — see the app's Static Shadow Rule), `.btn-primary:hover` shifts `translate(1px, 1px)` and shrinks its shadow from `4px 4px` to `3px 3px`, reading as a physical press. This is a deliberate, confirmed web-only exception: hover has no equivalent on a native touch app, so the site is free to use it as the CTA's primary interactive cue. Keep this exception scoped to hover/press feedback on buttons — don't extend animated shadows to cards or passive surfaces, where the app's static-shadow logic should still hold.

## Shapes

Two radius values in active use: `12px` (buttons) and `14px` (sticker cards) — both close to, but not identical to, the app's `RADIUS.md` (12px, matches) and `RADIUS.lg` (16px, sticker cards are 2px tighter). The header wordmark pill uses full `999px` rounding on the web, versus the app's `16px`-radius treatment for the same element — a larger, more badge-like shape suited to the bigger hero-header context; not reconciled with the app version, noted here as an observed difference rather than an error. 2px ink borders remain the default structural edge on every card/button, matching the app.

## Components

### Buttons
- **Primary** (`.btn-primary`): Deep Market Green fill, Surface White text, 2px ink border, 12px radius, paprika resting shadow; hover presses in (see The Web Hover Exception Rule).
- **Soon/disabled-style** (`.btn-soon`): Butter Yellow fill, ink text, same border/radius, green shadow, `cursor: default` — used for the "Coming soon to the App Store" badge, which is not a real link.
- Shared base (`.btn`): 2px ink border, 12px radius, uppercase Archivo Bold label, `.8rem 1.6rem` padding.

### Cards (`.sticker`)
- Surface White background, 2px ink border, 14px radius, green offset shadow (`4px 4px 0 var(--green)`) — used for the four legend cards and the two customer/vendor split blocks.

### Legend Grid
- CSS grid, `auto-fit, minmax(200px, 1fr)` columns, each cell an SVG teardrop pin (identical path data to the app's native `PinMarker`, 3px ink stroke instead of the app's 2.5px) filled with the matching status colour, plus a bold name and a one-line hint.

### Wordmark Pill
- Butter Yellow background, 2px ink border, full `999px` rounding (see Shapes note above), ink offset shadow (`3px 3px 0 var(--ink)`), wraps the wordmark PNG at 34px height.

### Footer / Strip
- The "Starting in the South East" strip inverts the palette: green background, paper text, butter-coloured `<h2>`, 2px ink top/bottom border rules — the only section on the page where text sits light-on-dark.

## Do's and Don'ts

### Do:
- **Do** load both brand Google Fonts (`Young+Serif`, `Archivo:wght@400;500;700`) via `<link rel="preconnect">` + stylesheet on every new page — see The Two-Font Discipline Rule; `privacy.html` was fixed to follow this in the same pass that wrote this file.
- **Do** keep the primary CTA's hover press-shadow effect scoped to buttons — it's a confirmed, deliberate web-only exception to the app's static-shadow rule, not something to extend to cards.
- **Do** use `box-shadow: Npx Npx 0 <color>` (zero blur, hard offset) for any new elevated element, matching the app's shadow language.
- **Do** reserve the four status colours (`--live`/`--sched`/`--closed`/`--inactive`) for the pin legend only.

### Don't:
- **Don't** reintroduce awning-stripe decoration or move toward a glossy food-delivery-app look — same rejected direction as the app.
- **Don't** treat the `:root` CSS custom properties as a shared stylesheet — each HTML file currently redeclares its own `:root` block independently (`index.html` and `privacy.html` both define overlapping but not identical variable sets). If a third page is added, extracting a single shared `<style>` or CSS file is worth doing rather than copy-pasting a third `:root` block.
- **Don't** ship a new page without verifying its fonts actually load — this file exists because `privacy.html` silently fell back to Georgia/system sans for months without anyone noticing visually.
