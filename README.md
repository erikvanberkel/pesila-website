# Pesila Thai Massage Website

Official website for Pesila Thai Massage, located at Schiedamseweg 17A, 3026 AB Rotterdam, Netherlands.

🌐 **Live Site**: [www.pesila.nl](https://www.pesila.nl)

## Overview

A modern, responsive single-page website for a Thai massage salon featuring:
- 10 different massage services with detailed descriptions and pricing
- Online booking integration via Treatwell
- Contact form for appointment requests
- Photo gallery showcasing the facilities
- Customer testimonials
- Embedded location map

## Technology Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Framework**: Bootstrap 5.3.0 (CSS only)
- **Hosting**: GitHub Pages
- **Domain**: www.pesila.nl

## Features

- ✅ Fully responsive mobile-first design
- ✅ SEO-optimized with Schema.org markup
- ✅ Accessibility-compliant (ARIA labels, semantic HTML)
- ✅ Modern image formats (AVIF, WebP) with fallbacks
- ✅ Lazy loading for optimal performance
- ✅ Google Analytics integration
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
├── index.html          # Main single-page application
├── gallery.html        # Photo gallery with modal viewer
├── css/
│   └── main.css       # Global styles with CSS variables
├── images/
│   ├── services/      # Service images
│   └── gallery/       # Gallery photos (multiple resolutions)
└── [service-name]/    # SEO redirect pages
```

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

## Contact Information

- **Phone**: +31623899709
- **Email**: pesilawellness@gmail.com
- **Address**: Schiedamseweg 17A, 3026 AB Rotterdam

## Documentation

For a comprehensive codebase analysis and technical documentation, see [CLAUDE.md](CLAUDE.md).

## License

© 2024 Pesila Thai Massage. All rights reserved.
