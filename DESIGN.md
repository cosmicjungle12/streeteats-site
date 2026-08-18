---
name: StreetEats (Landing Site)
description: Marketing site for StreetEats — live street-food map, vendor beta signup.
colors:
  deep-market-green: "#1C3A2F"
  paprika: "#C4552B"
  paprika-text: "#AF4C26"
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
    fontSize: "clamp(2rem, 6vw, 3.2rem)"
  h2:
    fontFamily: "'Young Serif', Georgia, serif"
    fontWeight: 400
    lineHeight: 1.2
    fontSize: "clamp(1.5rem, 4vw, 2.1rem)"
  h3:
    fontFamily: "'Young Serif', Georgia, serif"
    fontWeight: 400
    lineHeight: 1.2
    fontSize: "1.6rem"
  subhead:
    fontFamily: "'Archivo', -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif"
    fontWeight: 400
    fontSize: "1.2rem"
  body:
    fontFamily: "'Archivo', -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif"
    fontWeight: 400
    fontSize: "1rem"
    lineHeight: 1.6
  button:
    fontFamily: "'Archivo', sans-serif"
    fontWeight: 700
    fontSize: "0.95rem"
    letterSpacing: "0.08em"
  hint:
    fontFamily: "'Archivo', -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif"
    fontWeight: 400
    fontSize: "0.8rem"
  document-h1:
    fontFamily: "'Young Serif', Georgia, serif"
    fontWeight: 400
    fontSize: "2rem"
  document-h2:
    fontFamily: "'Young Serif', Georgia, serif"
    fontWeight: 400
    fontSize: "1.25rem"
  label:
    fontFamily: "'Archivo', sans-serif"
    fontWeight: 700
    fontSize: "0.7rem"
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
  btn-outline:
    backgroundColor: "transparent"
    textColor: "{colors.sign-ink}"
    rounded: "{rounded.btn}"
    padding: "0.8rem 1.6rem"
  soon-note:
    backgroundColor: "transparent"
    textColor: "{colors.body-ink}"
    rounded: "{rounded.btn}"
    padding: "0.5rem 1rem"
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
- **Paprika** (`#C4552B`): shadows only — the primary CTA's shadow colour (a web-specific choice — see Named Rules) and the vendors-CTA card shadow. Kept at full brand saturation since shadows aren't held to text-contrast rules.
- **Paprika Text** (`#AF4C26`): all links, section eyebrow labels, bullet markers — everywhere paprika renders as text. A darkened, hue-preserving variant of Paprika, introduced by an accessibility audit (2026-08) after the brand shade measured 3.8:1 on cream and 4.4:1 on white surface, both below the 4.5:1 WCAG AA minimum for normal text. Visually near-identical to Paprika; the split exists purely so shadows keep the true brand colour while text stays compliant.

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

**The Text-Safe Paprika Rule.** `--paprika` and `--paprika-text` are not interchangeable. Use `--paprika` only for `box-shadow` (or other non-text decoration); use `--paprika-text` for any color applied to text, links, or content that renders as text (including pseudo-element bullets). Never apply `--paprika` directly to text — it fails WCAG AA contrast on both `--cream` and `--surface`.

## Typography

**Display Font:** Young Serif (Google Fonts), falling back to Georgia.
**Body Font:** Archivo (Google Fonts, weights 400/500/700), falling back to the system sans stack.

**Character:** identical pairing logic to the app — a warm serif voice for headlines over a plain, confident grotesque for everything functional.

### Hierarchy
A six-step scale, deliberately spread (11.2px–25.6px, a 2.3:1 range) after an audit found the original scale's five secondary roles clustered within a 1.7:1 band and were hard to tell apart at a glance:
- **Display/H1** (hero headline): `clamp(2rem, 6vw, 3.2rem)` (32–51px), Young Serif, ink.
- **H2** (section headings): `clamp(1.5rem, 4vw, 2.1rem)` (24–34px), Young Serif, centred.
- **H3** (card headings): `1.6rem` (25.6px), Young Serif.
- **Subhead** (hero sub-copy only): `1.2rem` (19.2px), Archivo Regular.
- **Body**: `1rem` (16px) base, Archivo Regular, body-ink, 1.6 line-height — the floor; nothing goes smaller than this except Button/Hint/Label, which lean on weight and case instead of size to stay legible.
- **Button** (`.btn` CTA labels): `0.95rem` (15.2px), Archivo Bold, uppercase, `+0.08em` letter-spacing.
- **Hint** (`.hint`, footer, small-print asides): `0.8rem` (12.8px), Archivo Regular.
- **Label** (`.label`, `.section-label`, `.updated` on the privacy page): `0.7rem` (11.2px), Archivo Bold, uppercase, `+0.1em` letter-spacing — the smallest role, legible only because of the weight/case/tracking treatment carrying it.
- **Document H1/H2** (`privacy.html` only): `2rem`/`1.25rem` (32px/20px), Young Serif, static (not fluid) — a legal/Read-mode surface deliberately uses a plainer, fixed scale instead of the marketing page's `clamp()` headlines.

### Named Rules
**The Two-Font Discipline Rule.** Every page that renders brand type must load both Google Fonts (`Young+Serif` and `Archivo:wght@400;500;700`) via the same two `<link rel="preconnect">` + stylesheet pattern `index.html` uses. `privacy.html` was missing this (headings were silently falling back to Georgia, body text to system sans) until this pass added it — treat a missing font `<link>` on any new page as a bug, not a style choice.

**The Named-Role Rule.** Every font-size in the CSS should map to one of the eight roles above (Display/H1, H2, H3, Subhead, Body, Button, Hint, Label) rather than a bespoke value. An earlier version of this site had five different roles computing to near-identical sizes (12.5px–14.7px) purely by coincidence of independently-chosen rem values — pick from the named scale instead of eyeballing a new rem number.

## Layout

Single-column, centred `.wrap` container (`max-width: 960px`, `1.25rem` side padding) — no responsive breakpoints beyond one: `.split` (the customer/vendor two-column block) collapses to a single column under `720px`. Section rhythm is a flat `2.6rem` top/bottom padding per `<section>`. The legend grid and the customer/vendor split both use CSS Grid with `auto-fit`/explicit two-column patterns rather than a shared design-token spacing scale — this project has no formal spacing scale the way the app's `theme.js` does (see Do's and Don'ts).

**Legend grid density.** `.legend-grid` uses `grid-template-columns: repeat(auto-fit, minmax(140px, 1fr))` — tuned down from an original `200px` floor specifically so the four pin-status cards hold 2 columns on phone widths instead of forcing a 4-row single-column stack. Each card only holds an icon + two short lines, so a mobile layout audit found the original floor was burning nearly as much scroll height on the legend as the content-rich text cards below it. Keep the floor low enough for 2 columns at ~360px+ container widths; don't raise it back toward 200px without re-checking mobile.

**Hero desktop composition.** Below `900px` the hero stacks centred (van image, then `.hero-copy` with H1/subhead/CTAs) as a single column. At `900px+` it becomes a two-column flex row — van fixed at `340px` on the left, `.hero-copy` taking the remainder on the right, text left-aligned instead of centred. Added after a critique found the centred single-column layout left ~160px of unused cream on each side at desktop with nothing composed for the space; the fix is structural (reflow into two columns), not a scaled-up version of the mobile layout.

## Elevation & Depth

Same hard, zero-blur, coloured offset shadow language as the app — `box-shadow: Npx Npx 0 <color>`, never a blurred/soft shadow. Roles observed: sticker cards and the privacy-page main panel use a green shadow (`4px 4px 0 var(--green)`); the wordmark pill and vendors-CTA card use paprika or ink shadows; the primary button uses a paprika shadow.

### Shadow Vocabulary
- **sticker** (`4px 4px 0 var(--green)`, always paired with `border-radius: 14px`): legend cards, split blocks, privacy-page panel. The radius is part of the sticker treatment, not optional — the privacy-page panel shipped without it for a while (square corners on an otherwise-identical border+shadow) until an audit caught the mismatch; a shadow role and its radius travel together.
- **wordmark-pill** (`3px 3px 0 var(--ink)`): the header wordmark pill.
- **btn-primary** (`4px 4px 0 var(--paprika)`): the primary CTA button (resting state).
- **btn-soon** (`4px 4px 0 var(--green)`): the disabled-style "Coming soon" badge.

### Named Rules
**The Web Hover Exception Rule.** Unlike the native app (where shadows are purely structural and never respond to interaction — see the app's Static Shadow Rule), `.btn-primary:hover` shifts `translate(1px, 1px)` and shrinks its shadow from `4px 4px` to `3px 3px`, reading as a physical press. This is a deliberate, confirmed web-only exception: hover has no equivalent on a native touch app, so the site is free to use it as the CTA's primary interactive cue. Keep this exception scoped to hover/press feedback on buttons — don't extend animated shadows to cards or passive surfaces, where the app's static-shadow logic should still hold.

## Shapes

Two radius values in active use: `12px` (buttons) and `14px` (sticker cards) — both close to, but not identical to, the app's `RADIUS.md` (12px, matches) and `RADIUS.lg` (16px, sticker cards are 2px tighter). The header wordmark pill uses full `999px` rounding on the web, versus the app's `16px`-radius treatment for the same element — a larger, more badge-like shape suited to the bigger hero-header context; not reconciled with the app version, noted here as an observed difference rather than an error. 2px ink borders remain the default structural edge on every card/button, matching the app.

## Components

### Buttons
- **Primary** (`.btn-primary`): Deep Market Green fill, Surface White text, 2px ink border, 12px radius, paprika resting shadow; hover presses in (see The Web Hover Exception Rule). Reserved for the page's single strongest action — currently only "Join the vendor beta" in the dedicated vendor section.
- **Outline** (`.btn-outline`): transparent fill, ink text, same 2px border/12px radius/type as `.btn`, no shadow; hover gets a faint ink tint (`rgba(35,32,26,0.06)`). A genuinely clickable secondary action that shouldn't visually compete with the page's primary CTA — currently the hero's "Run a food van? →", which scrolls to the vendor section rather than being the vendor ask itself. A critique found the hero originally used `.btn-primary` here, making the only above-the-fold affordance a vendor-only action on a page whose headline and imagery pitch customers.
- Shared base (`.btn`): 2px ink border, 12px radius, uppercase Archivo Bold label, `.8rem 1.6rem` padding. Reserve `.btn` for genuinely clickable elements only — see the Non-Button Note pattern below.

### Named Rules (Components)
**The One Primary Rule.** Only one `.btn-primary` should be the strongest visual moment on any given viewport at a time. A page section pitching a different, smaller audience (like the hero's vendor-only link on a customer-framed headline) should use `.btn-outline` instead — visually secondary but still clearly clickable, unlike `.soon-note` which signals "not clickable at all."

### Non-Button Note (`.soon-note`)
Deliberately *not* built on `.btn` — no border-radius match by coincidence, no shadow, no button-scale type. Dashed 1.5px ink border, Hint-scale text (`.8rem`, not Button's `.95rem`), body-ink colour instead of full ink. Used for the "Coming soon to the App Store" badge: informational text that isn't a link, styled to read as an aside next to `.btn-primary`, not as a second, competing button. A mobile layout audit found the original version — full `.btn` treatment, hard shadow, same size as the real CTA, and positioned *before* it in the hero — made a non-interactive badge look like the primary action. Any future non-interactive status text should use this pattern, not a muted `.btn` variant.

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
- **Don't** treat the `:root` CSS custom properties as a shared stylesheet — each HTML file currently redeclares its own `:root` block independently (`index.html` and `privacy.html` both define overlapping but not identical variable sets). This isn't hypothetical: an audit caught `privacy.html`'s sticker panel missing `border-radius: 14px` (present on `index.html`'s `.sticker`) and its `.updated` label silently drifted to `font-weight: 600` / `letter-spacing: .08em` against `.label`'s `700` / `.1em` — two independently-typed copies of "the same role" diverging on properties the automated detector doesn't check. If a third page is added, extract a single shared `<style>` or CSS file rather than copy-pasting a fourth near-duplicate block.
- **Don't** ship a new page without verifying its fonts actually load — this file exists because `privacy.html` silently fell back to Georgia/system sans for months without anyone noticing visually.
