# Service Cards Redesign + Consistency Polish

**Date:** 2026-04-11
**Scope:** Visual refresh of service cards from vertical grid to compact expandable list, plus minor consistency tweaks to testimonials and FAQ.

## Goal

Replace the current tall vertical service cards (image + title + truncated description + pricing table) with a compact list layout where all 10 services are visible at a glance. Visitors can expand any service to see the full description, larger image, and pricing. This improves scannability and reduces scrolling.

## 1. Service Cards — Compact List with Expand

### Collapsed State (default)

Each service renders as a compact horizontal row (~80px tall):

- **Thumbnail** (left): 72x72px square, `border-radius: 12px`, uses existing AVIF service images with `object-fit: cover`
- **Title area** (center): Service name in Playfair Display + subtitle line "Vanaf €X · 30–120 min" in muted text
- **Pricing pills** (right): Rounded capsules (e.g., `30m €40`, `60m €65`) with cream background, gold border, inline layout
- **Chevron** (far right): Gold accent arrow, rotates 90deg on expand
- **Badge**: "Meest gekozen" badge on Traditionele Thaise Massage as a small pill, positioned inline near the title

Cards are stacked vertically with `0.75rem` gap, each with:
- `border-radius: 16px`
- `border: 1px solid rgba(201, 169, 97, 0.1)`
- `background: linear-gradient(180deg, #ffffff 0%, #faf7f2 100%)`
- `box-shadow: 0 4px 20px rgba(96, 68, 41, 0.08)`

### Expanded State (on click)

- Smooth height transition using CSS (matching the existing FAQ `::details-content` animation pattern or `max-height` transition)
- Reveals below the compact row:
  - **Larger image**: full-width within the card, ~240px height, `object-fit: cover`
  - **Full description**: the existing paragraph text, no truncation
  - **Pricing table**: the existing `<table>` markup with duration/price rows (the full table, not the collapsed-state pills)
- Only one card expanded at a time — clicking another collapses the current one
- The `<article>` element gets `aria-expanded="true"` when open
- Keyboard: Enter/Space to toggle (existing behavior, maintained)

### Mobile (< 768px)

- Thumbnail shrinks to 56x56px
- Pricing pills wrap below the title/subtitle instead of sitting to the right
- Chevron remains far-right
- Same expand/collapse behavior
- Touch target meets 24x24px minimum (the entire row is clickable)

### HTML Structure

The current structure uses `<article class="service-card">` inside a Bootstrap grid (`col-md-6 col-lg-4`). The new structure:

- Remove the grid wrapper — services become a stacked list inside a single `max-width: 800px` container (centered)
- Each service remains an `<article>` with `tabindex="0"` and `aria-expanded`
- The `<picture>` elements, description text, and pricing tables stay — just reorganized within the article
- The expand/collapse JavaScript (`initServiceCards()`) is adapted to the new layout

### Existing Content Preserved

No copy, image, or pricing changes. All 10 services keep their:
- Service names and heading IDs
- Full description paragraphs
- Pricing tables with aria-labels
- AVIF images with lazy loading
- Accessibility attributes

## 2. Consistency Tweaks

### Testimonial Cards

- Reduce padding from `2rem` to `1.5rem`
- Tighten spacing between quote text and cite element (reduce `margin-top` on cite from `1.25rem` to `1rem`)
- No structural changes

### FAQ Items

- Already uses a similar compact expandable pattern — verify visual consistency:
  - Bump `border-radius` from `12px` to `16px` to match the new service cards
  - Border and hover opacity values should use the same `rgba(201, 169, 97, ...)` values as the service cards
- No structural changes

### Pricing Pill CSS Class

Extract the pill styling into a reusable `.pricing-pill` class in `css/main.css`:
- `padding: 0.25rem 0.6rem`
- `background: #faf7f2`
- `border-radius: 14px`
- `font-size: 0.75rem`
- `border: 1px solid rgba(201, 169, 97, 0.15)`
- `color: #604429`
- `white-space: nowrap`

This class is used in the service cards. Available for reuse elsewhere if needed.

## 3. What Does NOT Change

- Hero section
- Navbar
- Timetable section
- About section
- Booking/contact area (form, map, gift callout)
- Footer
- Gallery page
- All SEO markup, structured data, meta tags
- All accessibility features (skip link, aria attributes, focus management, reduced motion)
- Color palette and CSS variables
- Typography (Playfair Display headings, DM Sans body)
- External integrations (Treatwell, FormSubmit, Google Reviews, chat widget)

## 4. Technical Notes

- All changes are in `index.html` (inline styles section) and `css/main.css`
- The existing `initServiceCards()` JavaScript function needs updating for the new expand/collapse behavior
- The Bootstrap grid classes on the services section are removed in favor of a simple stacked layout
- Responsive breakpoint at 768px for mobile pill wrapping
- `prefers-reduced-motion` media query must be respected — disable height transitions for users who prefer reduced motion
