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

### Single-Page Pattern with SEO Redirects
- `index.html` - Main SPA with all content (anchor navigation)
- `gallery.html` - Photo gallery with modal viewer
- `*/index.html` subdirectories - Meta refresh redirects to preserve old URLs

### Key Files
- `css/main.css` - Global styles with CSS variables (theming)
- `images/services/*.avif` - Service images (10 services)
- `images/gallery/w{320,640,1280,1920}/` - Responsive gallery images

### CSS Variables (main.css)
```css
--primary-color: #604429;      /* WCAG AAA compliant brown */
--primary-color-light: #6b4e31; /* Original brand color */
--secondary-color: #8b6f47;    /* Hover states */
--background-color: #f8f4ef;   /* Warm off-white */
--text-color: #333;
```

### JavaScript Structure (inline in index.html)
```javascript
CONFIG = { vacation, google, validation }  // Centralized constants
handleVacationNotices()   // Date-based visibility
initFormValidation()      // Email OR phone required
initServiceCards()        // Expand/collapse
GoogleReviews.init()      // Dynamic loading with cache
```

## External Integrations

| Service | Purpose | Fallback |
|---------|---------|----------|
| Treatwell Widget | Booking | Links to treatwell.nl/plaats/pesila-thai-massage/ |
| FormSubmit.co | Contact form | Phone/email displayed |
| Google Maps API | Reviews | External link to Google Reviews |
| Google Analytics | Tracking | Site works without it |

## Important Conventions

### Language
All user-facing content is in **Dutch** (lang="nl"). Maintain this for any additions.

### Image Format Priority
AVIF → WebP → JPG/PNG (use `<picture>` element with fallbacks)

### Responsive Images
Four breakpoints: 320px, 640px, 1280px, 1920px in `images/gallery/w*/`

### Accessibility Requirements
- WCAG 2.2 Level AA compliant - maintain this standard
- All images need descriptive Dutch alt text
- Focus indicators: 3px solid primary color
- Interactive elements need `scroll-margin-top: 5rem` (fixed navbar)
- Minimum touch target: 24×24px

### Progressive Enhancement
- Core functionality must work without JavaScript
- All forms work without JS (FormSubmit.co handles submission)
- Mobile nav toggle is CSS-only (checkbox hack)
- `<noscript>` tags hide preloader and show fallback messages

## Business Context

- **Address**: Schiedamseweg 17A, 3026 AB Rotterdam
- **Phone**: +31623899709
- **Email**: pesilawellness@gmail.com
- **Important**: Site explicitly states "GEEN EROTIEK" (no erotic services) - this is culturally important for Thai massage businesses in Netherlands
