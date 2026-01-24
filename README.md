# Pesila Thai Massage Website

Official website for Pesila Thai Massage, located at Schiedamseweg 17A, 3026 AB Rotterdam, Netherlands.

🌐 **Live Site**: [www.pesila.nl](https://www.pesila.nl)

## Overview

A modern, responsive, and accessible single-page website for a Thai massage salon featuring:
- 10 different massage services with detailed descriptions and pricing
- Online booking integration via Treatwell
- Contact form for appointment requests
- Photo gallery showcasing the facilities with modal viewer
- Google Reviews integration with dynamic loading
- Embedded location map
- Full WCAG 2.2 Level AA compliance + selective AAA enhancements

## Technology Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Framework**: Bootstrap 5.3.0 (CSS only, no JS dependencies)
- **Hosting**: GitHub Pages
- **Domain**: www.pesila.nl
- **Analytics**: Google Analytics (gtag.js)
- **APIs**: Google Maps API, Google Places API, Treatwell Booking Widget

## Features

### Design & UX
- ✅ Fully responsive mobile-first design
- ✅ CSS Grid and Flexbox layout
- ✅ Modern image formats (AVIF → WebP → JPG/PNG fallbacks)
- ✅ Responsive images with 4 breakpoints (320px, 640px, 1280px, 1920px)
- ✅ Lazy loading for optimal performance
- ✅ CSS-only animations and transitions
- ✅ Custom CSS variables for theming

### Accessibility (WCAG 2.2 Level AA Compliant)
- ✅ Semantic HTML5 structure (header, nav, main, section, article, footer)
- ✅ ARIA attributes (roles, labels, live regions, expanded states)
- ✅ Skip navigation link for keyboard users
- ✅ Full keyboard navigation support (Tab, Enter, Space, Escape)
- ✅ Focus management and visible focus indicators (3px solid outlines)
- ✅ Focus not obscured by fixed navbar (scroll-margin-top on all focusable elements)
- ✅ Interactive target sizes meet 24×24px minimum (WCAG 2.2)
- ✅ Proper form labels and error associations
- ✅ Modal focus trapping
- ✅ Screen reader friendly
- ✅ Color contrast ratios meet AA standards (4.5:1 for text, 3:1 for UI)
- ✅ Text resizable to 200%
- ✅ Content reflows at 320px width
- ✅ Multiple navigation methods
- ✅ Consistent navigation and identification
- ✅ Consistent help location across pages
- ✅ No redundant entry in forms

### SEO & Performance
- ✅ Schema.org LocalBusiness structured data
- ✅ Open Graph and Twitter Card meta tags
- ✅ Semantic heading hierarchy
- ✅ SEO-friendly redirect structure
- ✅ Canonical URLs
- ✅ Optimized page load performance
- ✅ Zero build process - pure static site

## Services Offered

1. Traditional Thai Massage (30-120 min)
2. Aroma Oil Massage (60-120 min)
3. Foot Reflexology (30-120 min)
4. Neck-Shoulder-Head Massage (30-120 min)
5. Hot Stone Massage (60-120 min)
6. Duo Massage (60-120 min)
7. Pregnancy Massage (60 min)
8. Sports Massage (60-120 min)
9. Deep Tissue Massage (60-120 min)
10. Herbal Stamp Massage (60-120 min)

## Project Structure

```
pesila-website/
├── index.html                    # Main single-page application
├── gallery.html                  # Photo gallery with modal viewer
├── CLAUDE.md                     # Comprehensive technical documentation
├── README.md                     # This file
├── WCAG-AA-AUDIT.md              # WCAG 2.1 Level AA compliance audit
├── WCAG-2.2-AUDIT.md             # WCAG 2.2 compliance audit
├── WCAG-AAA-ANALYSIS.md          # WCAG 2.1 Level AAA analysis
├── WCAG-AAA-ROADMAP.md           # Roadmap for optional AAA enhancements
├── CNAME                         # Custom domain configuration
├── .prettierrc                   # Code formatting rules
├── css/
│   └── main.css                  # Global styles with CSS variables
├── images/
│   ├── logo*.png                 # Brand logos and favicons
│   ├── services/                 # Service images (AVIF format)
│   │   ├── traditioneel.avif
│   │   ├── aroma.avif
│   │   └── ... (10 services)
│   └── gallery/                  # Gallery photos in multiple resolutions
│       ├── w320/                 # Mobile (320px)
│       ├── w640/                 # Small tablets (640px)
│       ├── w1280/                # Tablets/laptops (1280px)
│       └── w1920/                # Desktop (1920px)
└── [service-name]/               # SEO redirect pages
    └── index.html
```

## Recent Improvements (December 2026)

### Accessibility Enhancements (WCAG 2.1 Level AA)
- ✅ Fixed language declaration in gallery.html (nl instead of en)
- ✅ Added keyboard accessibility to all service cards (expandable with Enter/Space)
- ✅ Implemented skip navigation links on both pages
- ✅ Enhanced form accessibility with proper ARIA labels and error associations
- ✅ Added full modal accessibility (focus trapping, ARIA roles, keyboard support)
- ✅ Removed inline event handlers in favor of clean event listeners
- ✅ Added visible focus indicators for all interactive elements (3px solid outlines)
- ✅ Fixed color contrast ratios to meet AA standards:
  - Placeholder text: #888 → #757575 (4.55:1 ratio)
  - Empty star icons: #ddd → #c0c0c0 (3.0:1 ratio)

### WCAG 2.2 Compliance (New Success Criteria)
- ✅ Added scroll-margin-top to all focusable elements (prevents focus obscuring by fixed navbar)
- ✅ Verified interactive target sizes meet 24×24px minimum
- ✅ Consistent help mechanism location across pages
- ✅ No redundant entry required in forms
- ✅ No dragging movements required
- ✅ No authentication required

### WCAG 2.1 Level AAA Enhancements (Selective Implementation)
- ✅ Enhanced color contrast: Primary color darkened (#6b4e31 → #604429) for 7:1 ratio
- ✅ Line length optimization: Max-width 80ch for improved readability
- ✅ Technical term tooltips: Added explanations for specialized massage terminology
- ✅ Context-sensitive form help: Examples and guidance for all form fields
- ✅ Visual tooltip indicators: Dotted underlines for abbr elements

### Code Quality & Performance
- ✅ Refactored JavaScript into modular, maintainable sections
- ✅ Centralized all configuration in CONFIG object
- ✅ Converted Google Reviews to object-based pattern
- ✅ Added noscript fallbacks for graceful degradation
- ✅ Updated Treatwell fallback URL to salon-specific page

### Documentation
- ✅ Created WCAG-AA-AUDIT.md (detailed AA compliance audit)
- ✅ Created WCAG-2.2-AUDIT.md (WCAG 2.2 compliance analysis)
- ✅ Created WCAG-AAA-ANALYSIS.md (AAA color contrast analysis)
- ✅ Created WCAG-AAA-ROADMAP.md (optional AAA enhancement roadmap)

These improvements ensure the website meets **WCAG 2.2 Level AA** standards for accessibility.

## Deployment

The site is automatically deployed via GitHub Pages from the `master` branch.

To deploy changes:
```bash
git add .
git commit -m "Your commit message"
git push origin master
```

Changes go live automatically within a few minutes.

## Local Development

No build process required. Simply open `index.html` in a browser or use a local server:

```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx http-server

# Using PHP
php -S localhost:8000
```

## Browser Support

- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)
- ✅ Progressive enhancement for older browsers (graceful fallbacks)

## Code Quality

- Clean, readable, and maintainable code
- Separation of concerns (HTML, CSS, JavaScript)
- Consistent naming conventions
- Formatted with Prettier (2-space indentation, LF line endings)
- No dependencies or build process required
- Inline critical CSS for hero section
- Event delegation for optimal performance

## Contact Information

- **Phone**: +31623899709
- **Email**: pesilawellness@gmail.com
- **Address**: Schiedamseweg 17A, 3026 AB Rotterdam, Netherlands
- **Website**: [www.pesila.nl](https://www.pesila.nl)

## Documentation

### Technical Documentation
- [CLAUDE.md](CLAUDE.md) - Comprehensive codebase analysis and technical documentation

### Accessibility Audits
- [WCAG-AA-AUDIT.md](WCAG-AA-AUDIT.md) - WCAG 2.1 Level AA compliance audit with color contrast analysis
- [WCAG-2.2-AUDIT.md](WCAG-2.2-AUDIT.md) - WCAG 2.2 compliance audit (9 new success criteria)
- [WCAG-AAA-ANALYSIS.md](WCAG-AAA-ANALYSIS.md) - WCAG 2.1 Level AAA color contrast analysis
- [WCAG-AAA-ROADMAP.md](WCAG-AAA-ROADMAP.md) - Roadmap for optional AAA enhancements

## Contributing

This is a production website for a local business. For bug reports or suggestions, please contact the development team.

## License

© 2026 Pesila Thai Massage. All rights reserved.
