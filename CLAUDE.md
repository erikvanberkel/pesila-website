# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML website for Pesila Thai Massage (www.pesila.nl), a Thai massage salon in Rotterdam, Netherlands. No build process - pure HTML/CSS/JS deployed directly to GitHub Pages.

## Development Commands

```bash
# Local development (no build required)
python -m http.server 8000    # or: npx http-server

# Deploy (automatic via GitHub Pages)
git push origin master        # Changes go live within minutes

# Code formatting
npx prettier --write .        # Uses .prettierrc config
```

## Architecture

### File Structure
```
/index.html               # Main SPA with all content (anchor navigation)
/gallery.html             # Photo gallery with fullscreen modal viewer
/css/main.css             # Global styles with CSS variables
/images/services/         # Service images (AVIF only, 10 services)
/images/gallery/w*/       # Responsive gallery (w320, w640, w1280, w1920)
/*/index.html             # Meta refresh redirects to preserve old URLs
```

### Single-Page Pattern
- `index.html` - Main SPA with all content (anchor navigation: #home, #services, #booking, etc.)
- `gallery.html` - Photo gallery with fullscreen modal viewer
- `*/index.html` subdirectories - Meta refresh redirects to preserve old URLs

### CSS Variables (main.css)
```css
/* Primary Colors */
--primary-color: #604429;       /* WCAG AAA compliant brown */
--primary-color-light: #6b4e31; /* Lighter brand brown */
--secondary-color: #8b6f47;     /* Hover states */

/* Backgrounds */
--background-color: #f8f4ef;    /* Warm off-white */
--cream-warm: #faf7f2;
--cream-deep: #f0e9de;

/* Accents */
--gold-accent: #c9a961;         /* Refined luxury gold */
--gold-light: #e8d5a3;
--sage-accent: #8b9e82;

/* Shadows */
--shadow-soft: 0 4px 20px rgba(96, 68, 41, 0.08);
--shadow-medium: 0 8px 30px rgba(96, 68, 41, 0.12);
--shadow-lifted: 0 20px 40px rgba(96, 68, 41, 0.15);

/* Transitions */
--transition: all 0.3s ease;
--transition-fast: all 0.2s ease;
```

### JavaScript Structure (inline in index.html)
```javascript
// Configuration object with all constants
CONFIG = {
  vacation: { startDate, endDate, daysBeforeNotice },
  google: { placeId, cacheDuration, minRating, maxReviews },
  validation: { emailRegex, phoneRegex }
}

// Key functions
handleVacationNotices()   // Date-based visibility of vacation alerts
hidePreloader()           // Remove loading spinner on page load
initFormValidation()      // Email OR phone required (live validation)
initNavigation()          // Mobile nav close, active link tracking on scroll
initServiceCards()        // Expand/collapse with keyboard support (Enter/Space)
GoogleReviews.init()      // Async fetch with localStorage caching (24h TTL)
```

## External Integrations

| Service | Purpose | Details |
|---------|---------|---------|
| Treatwell Widget | Booking | widget.treatwell.nl/salon/482688/menu/ |
| FormSubmit.co | Contact form | Hashed endpoint, works without JS |
| Google Maps API | Reviews | Place ID: ChIJayy_TwM1xEcRGWhh99q1o48 |
| Google Analytics | Tracking | GA4: G-69BZRSS6JF |
| Bootstrap 5.3.0 | UI framework | CDN via jsDelivr |
| Google Fonts | Typography | Playfair Display + DM Sans (preloaded) |

## Important Conventions

### Language
All user-facing content is in **Dutch** (lang="nl"). Maintain this for any additions.

### Image Formats
- **Service images**: AVIF only (no fallbacks needed, browser support sufficient)
- **Gallery images**: AVIF with WebP fallback via `<picture>` element
- **Responsive breakpoints**: 320px, 640px, 1280px, 1920px in `images/gallery/w*/`

### Accessibility Requirements (WCAG 2.2 AA)
- Skip link to main content (visible on focus)
- Semantic HTML: `<header>`, `<nav>`, `<section>`, `<article>`, `<footer>`
- aria-labels on navigation and interactive elements
- aria-expanded on expandable service cards
- Focus indicators: 3px solid gold outline with 2px offset
- `scroll-margin-top: 5rem` for fixed navbar offset
- Keyboard navigation: Tab, Enter, Space, Escape (modal close)
- Modal focus trapping in gallery fullscreen view
- All images need descriptive Dutch alt text

### Progressive Enhancement
- Core functionality works without JavaScript
- Forms submit via FormSubmit.co (no JS required)
- Mobile nav toggle is CSS-only (checkbox hack)
- `<noscript>` tags hide preloader and show fallback messages
- Google Reviews section shows link to external reviews if API fails

### 10 Massage Services
1. Traditionele Thaise Massage (30/60/90/120 min)
2. Aroma-oliemassage (60/90/120 min)
3. Voetreflexmassage (30/60/90/120 min)
4. Nek-schouder-hoofdmassage (30/60/90/120 min)
5. Hot Stone Massage (60/90/120 min)
6. Duo-massage (60/90/120 min)
7. Zwangerschapsmassage (60 min only)
8. Sportmassage (60/90/120 min)
9. Deep Tissue Massage (60/90/120 min)
10. Kruidenstempelmassage (60/90/120 min)

## Business Context

- **Address**: Schiedamseweg 17A, 3026 AB Rotterdam
- **Phone**: +31623899709
- **Email**: pesilawellness@gmail.com
- **Important**: Site explicitly states "GEEN EROTIEK" (no erotic services) - this is culturally important for Thai massage businesses in Netherlands
