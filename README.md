# Pesila Thai Massage Website

Official website for Pesila Thai Massage, located at Schiedamseweg 17A, 3026 AB Rotterdam, Netherlands.

**Live Site**: [www.pesila.nl](https://www.pesila.nl)

## Overview

A responsive, accessible single-page website for a Thai massage salon featuring:
- 10 massage services with descriptions and pricing
- Online booking via Treatwell
- Contact form (FormSubmit.co)
- Photo gallery with modal viewer
- Google Reviews integration
- Embedded location map

## Technology Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Framework**: Bootstrap 5.3.0 (CSS only)
- **Hosting**: GitHub Pages (deployed via GitHub Actions)
- **Domain**: www.pesila.nl
- **APIs**: Google Maps/Places API, Treatwell Booking Widget

## Project Structure

```
pesila-website/
├── index.html              # Main single-page application
├── gallery.html            # Photo gallery with modal viewer
├── CNAME                   # Custom domain configuration
├── css/
│   └── main.css            # Global styles with CSS variables
├── images/
│   ├── services/*.avif     # Service images (10 services)
│   └── gallery/w{320,640,1280,1920}/  # Responsive gallery images
└── [service-name]/         # SEO redirect pages (meta refresh → index.html#section)
    └── index.html
```

## Local Development

No build process required:

```bash
python -m http.server 8000    # or: npx http-server
```

Google Reviews won't load locally (requires API key injected during deploy). The site gracefully degrades to show a link to Google Reviews.

## Deployment

Pushing to `master` triggers a GitHub Actions workflow that injects secrets and deploys to GitHub Pages.

**Required secret**: `GOOGLE_MAPS_API_KEY` (set in repository Settings > Secrets > Actions)

## Accessibility

The site targets WCAG 2.2 Level AA compliance with selective AAA enhancements. See audit documents in the repo root for details.

## License

All rights reserved.
