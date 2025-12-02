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
- Full WCAG 2.1 Level A compliance

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

### Accessibility (WCAG 2.1 Level A Compliant)
- ✅ Semantic HTML5 structure (header, nav, main, section, article, footer)
- ✅ ARIA attributes (roles, labels, live regions, expanded states)
- ✅ Skip navigation link for keyboard users
- ✅ Full keyboard navigation support (Tab, Enter, Space, Escape)
- ✅ Focus management and visible focus indicators
- ✅ Proper form labels and error associations
- ✅ Modal focus trapping
- ✅ Screen reader friendly

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

## Recent Improvements (December 2025)

### Accessibility Enhancements
- ✅ Fixed language declaration in gallery.html (nl instead of en)
- ✅ Added keyboard accessibility to all service cards (expandable with Enter/Space)
- ✅ Implemented skip navigation links on both pages
- ✅ Enhanced form accessibility with proper ARIA labels and error associations
- ✅ Added full modal accessibility (focus trapping, ARIA roles, keyboard support)
- ✅ Removed inline event handlers in favor of clean event listeners
- ✅ Added visible focus indicators for all interactive elements

These improvements ensure the website meets **WCAG 2.1 Level A** standards for accessibility.

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

For a comprehensive codebase analysis and technical documentation, see [CLAUDE.md](CLAUDE.md).

## Contributing

This is a production website for a local business. For bug reports or suggestions, please contact the development team.

## License

© 2025 Pesila Thai Massage. All rights reserved.
