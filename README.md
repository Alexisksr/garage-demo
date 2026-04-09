# Websites — Project Root

This directory contains client website projects built for local businesses.

---

## Projects

### `garage auto essaie/`

A single-page French-language website for **Garage Auto-Ban**, an all-brand automotive repair garage in Fribourg, Switzerland.

- **Owner**: Ban TUY (Ingénieur diplômé HES)
- **Location**: Rue de la Carrière 42b, 1700 Fribourg
- **Domain**: auto-ban.ch
- **Founded**: 2018

#### Files

| File | Purpose |
|------|---------|
| `démonstration:Garage.html` | The complete website (single self-contained file) |
| `ALK-presentation.pptx` | Business pitch/overview presentation |
| `ALK-devis-contrat.pdf` | Sample quotation & contract template |
| `ALK-facture.pdf` | Sample invoice template |

---

## Architecture

### Stack

- **HTML5** — semantic markup, French (`lang="fr"`)
- **CSS** — fully embedded in a `<style>` block (no external stylesheet)
- **JavaScript** — minimal vanilla JS, no frameworks or libraries
- **Fonts** — Google Fonts: Bebas Neue (headings) + Outfit (body)
- **Icons** — inline SVGs only (no image files)

### Single-File Design

The entire website lives in one `.html` file. There are no separate CSS or JS files, no build step, and no dependencies beyond Google Fonts. This makes the site trivially portable and deployable by dropping a single file onto any web host.

### Page Sections (anchor navigation)

| Section | Anchor | Content |
|---------|--------|---------|
| Navigation | — | Fixed sticky navbar with smooth-scroll links |
| Hero | `#home` | Full-viewport landing with tagline, stats, and CTAs |
| Services | `#services` | 8-card grid of offered automotive services |
| About | `#about` | Company timeline, founder background, credentials |
| Why Us | `#why` | 4-card value proposition grid |
| Contact | `#contact` | Address, hours, contact form, map link |
| Footer | — | Minimal footer with copyright and anchor links |

Navigation uses `<a href="#section">` anchor links with `scroll-behavior: smooth`.

### CSS Design System

CSS custom properties define the design tokens:

```css
--red: #D92B2B        /* brand accent */
--bg:  #0C0C0C        /* dark background */
--text: #F2EDE6       /* primary text */
--muted: #888880      /* secondary text */
```

Layout uses **CSS Grid** for multi-column sections and **Flexbox** for alignment. Fluid typography is achieved with `clamp()`. A single responsive breakpoint at `900px` collapses layouts to single-column for mobile.

### JavaScript

One `<script>` block at the end of the file handles:

- **Scroll animations** — `IntersectionObserver` watches `.reveal` elements and adds a `.visible` class when they enter the viewport, triggering CSS opacity/transform transitions with staggered delays (`i × 0.08s`)
- **Form feedback** — the submit button switches to a checkmark state on click

No libraries, no build tools, no bundler required.
