# Eleventy Migration Plan for Pesila Website

This document outlines an incremental migration from static HTML to Eleventy (11ty), reducing code repetition while maintaining GitHub Pages deployment.

## Overview

**Current state:** 2 main HTML files + 11 redirect pages with significant duplication
**Target state:** Templated site with shared components and data-driven content

**Estimated file reduction:** ~2,500 lines → ~800 lines (68% reduction)

---

## Phase 1: Setup (Non-Breaking)

### 1.1 Install Eleventy

```bash
npm init -y
npm install @11ty/eleventy --save-dev
```

### 1.2 Create Configuration

Create `.eleventy.js` in project root:

```js
module.exports = function(eleventyConfig) {
  // Copy static assets
  eleventyConfig.addPassthroughCopy("css");
  eleventyConfig.addPassthroughCopy("images");

  // Watch CSS for changes
  eleventyConfig.addWatchTarget("css/");

  return {
    dir: {
      input: "src",
      output: "_site",
      includes: "_includes",
      layouts: "_layouts",
      data: "_data"
    },
    htmlTemplateEngine: "njk",
    markdownTemplateEngine: "njk"
  };
};
```

### 1.3 Create Directory Structure

```
pesila-website/
├── src/
│   ├── _data/           # JSON data files
│   ├── _includes/       # Reusable components
│   ├── _layouts/        # Page layouts
│   ├── index.njk        # Homepage
│   └── gallery.njk      # Gallery page
├── css/                 # Stays in place
├── images/              # Stays in place
├── .eleventy.js
└── package.json
```

### 1.4 Update package.json Scripts

```json
{
  "scripts": {
    "build": "eleventy",
    "serve": "eleventy --serve",
    "clean": "rm -rf _site"
  }
}
```

---

## Phase 2: Extract Layouts

### 2.1 Create Base Layout

Create `src/_layouts/base.njk`:

```njk
<!DOCTYPE html>
<html lang="nl">
  <head>
    <script async src="https://www.googletagmanager.com/gtag/js?id=G-69BZRSS6JF"></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag() { dataLayer.push(arguments); }
      gtag("js", new Date());
      gtag("config", "G-69BZRSS6JF");
    </script>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>{{ title }} | Pesila Thai Massage Rotterdam</title>
    <meta name="description" content="{{ description }}" />
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" />
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;600&family=DM+Sans:wght@400;500;600&display=swap" />
    <link rel="stylesheet" href="/css/main.css" />
    <link rel="icon" type="image/png" href="/images/icon.png" />
    {% block head %}{% endblock %}
  </head>
  <body>
    {% include "nav.njk" %}

    <main id="main-content">
      {{ content | safe }}
    </main>

    {% include "footer.njk" %}

    {% block scripts %}{% endblock %}
  </body>
</html>
```

### 2.2 Create Navigation Component

Create `src/_includes/nav.njk`:

```njk
<a href="#main-content" class="skip-link">Spring naar hoofdinhoud</a>
<header>
  <nav class="navbar navbar-expand-lg fixed-top" aria-label="Hoofdnavigatie">
    <div class="container">
      <a class="navbar-brand" href="/#home">
        <img src="/images/logo.png" alt="Pesila Thai Massage Logo" />
      </a>
      <input type="checkbox" id="navbar-toggle" class="d-none" />
      <label for="navbar-toggle" class="navbar-toggler" aria-label="Navigatie in-/uitschakelen">
        <span class="navbar-toggler-icon"></span>
      </label>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          {%- for item in navigation -%}
          <li class="nav-item">
            <a class="nav-link{% if page.url == item.url %} active{% endif %}" href="{{ item.url }}">{{ item.title }}</a>
          </li>
          {%- endfor -%}
        </ul>
      </div>
    </div>
  </nav>
</header>
```

### 2.3 Create Footer Component

Create `src/_includes/footer.njk`:

```njk
<footer>
  <div class="container">
    <p>{{ site.name }} | {{ site.address }} | <a href="tel:{{ site.phone }}">{{ site.phoneDisplay }}</a></p>
    <p>&copy; {{ site.year }} {{ site.name }}. Alle rechten voorbehouden.</p>
  </div>
</footer>
```

---

## Phase 3: Data Files

### 3.1 Site Configuration

Create `src/_data/site.json`:

```json
{
  "name": "Pesila Thai Massage",
  "address": "Schiedamseweg 17A, 3026 AB Rotterdam",
  "phone": "+31623899709",
  "phoneDisplay": "06-23899709",
  "email": "pesilawellness@gmail.com",
  "url": "https://www.pesila.nl",
  "year": 2025
}
```

### 3.2 Navigation Data

Create `src/_data/navigation.json`:

```json
[
  { "title": "Home", "url": "/#home" },
  { "title": "Openingstijden", "url": "/#timetable" },
  { "title": "Massages", "url": "/#services" },
  { "title": "Recensies", "url": "/#testimonials" },
  { "title": "Over ons", "url": "/#about" },
  { "title": "Boek nu", "url": "/#booking" },
  { "title": "Contact", "url": "/#contact" },
  { "title": "Gallerij", "url": "/gallery/" }
]
```

### 3.3 Services Data

Create `src/_data/services.json`:

```json
[
  {
    "id": "traditional-massage",
    "name": "Traditionele Thaise Massage",
    "image": "traditioneel.avif",
    "alt": "Traditionele Thaise massage bij Pesila",
    "description": "De Traditionele Thaise massage, ook wel nuat phaen boran...",
    "pricing": [
      { "duration": "30 min.", "price": "€ 40,-" },
      { "duration": "60 min.", "price": "€ 65,-" },
      { "duration": "90 min.", "price": "€ 95,-" },
      { "duration": "120 min.", "price": "€ 125,-" }
    ]
  },
  {
    "id": "aroma-massage",
    "name": "Aroma-oliemassage",
    "image": "aroma.avif",
    "alt": "Aroma-oliemassage bij Pesila",
    "description": "Een aroma-olie massage is een vorm van kruidengeneeskunde...",
    "pricing": [
      { "duration": "60 min.", "price": "€ 75,-" },
      { "duration": "90 min.", "price": "€ 105,-" },
      { "duration": "120 min.", "price": "€ 135,-" }
    ]
  }
]
```

### 3.4 Gallery Data

Create `src/_data/gallery.json`:

```json
[
  { "number": "01", "orientation": "landscape", "alt": "Interieur Pesila Thai Massage" },
  { "number": "02", "orientation": "landscape", "alt": "Wachtruimte met comfortabele stoelen" },
  { "number": "03", "orientation": "portrait", "alt": "Massagetafel in behandelkamer" },
  { "number": "04", "orientation": "landscape", "alt": "Ontspanningsruimte" },
  { "number": "05", "orientation": "portrait", "alt": "Decoratieve elementen" }
]
```

---

## Phase 4: Reusable Components

### 4.1 Service Card Component

Create `src/_includes/service-card.njk`:

```njk
<div class="col-xl-4 col-md-6 mb-4">
  <article class="service-card" tabindex="0" role="button" aria-expanded="false" aria-labelledby="{{ service.id }}">
    <img src="/images/services/{{ service.image }}" loading="lazy" alt="{{ service.alt }}" />
    <h3 id="{{ service.id }}">{{ service.name }}</h3>
    <div class="text-container">
      <div>
        <p>{{ service.description }}</p>
      </div>
    </div>
    <div class="pricing-table">
      <table aria-label="Prijzen voor {{ service.name | lower }}">
        <tr>
          <th scope="col">Duur</th>
          <th scope="col">Prijs</th>
        </tr>
        {%- for price in service.pricing -%}
        <tr>
          <td>{{ price.duration }}</td>
          <td>{{ price.price }}</td>
        </tr>
        {%- endfor -%}
      </table>
    </div>
  </article>
</div>
```

### 4.2 Responsive Picture Component

Create `src/_includes/picture.njk`:

```njk
{# Usage: {% include "picture.njk", img: { number: "01", orientation: "landscape", alt: "Description" } %} #}
<picture class="{{ img.orientation }}">
  {%- set sizes = [1920, 1280, 640, 320] -%}
  {%- set breakpoints = { 1920: 1200, 1280: 768, 640: 320, 320: 0 } -%}
  {%- for format in ["avif", "webp"] -%}
    {%- for size in sizes -%}
      {%- if breakpoints[size] > 0 -%}
  <source media="(min-width: {{ breakpoints[size] }}px)" srcset="/images/gallery/w{{ size }}/photo-{{ img.number }}.{{ format }}" type="image/{{ format }}" />
      {%- else -%}
  <source media="(max-width: 319px)" srcset="/images/gallery/w{{ size }}/photo-{{ img.number }}.{{ format }}" type="image/{{ format }}" />
      {%- endif -%}
    {%- endfor -%}
  {%- endfor -%}
  <img src="/images/gallery/w640/photo-{{ img.number }}.webp" alt="{{ img.alt }}" class="{{ img.orientation }}" loading="lazy" />
</picture>
```

---

## Phase 5: Convert Pages

### 5.1 Homepage

Create `src/index.njk`:

```njk
---
layout: base.njk
title: Authentieke Thaise Massage
description: Ontspan met authentieke Thaise massages bij Pesila Thai Massage in Rotterdam.
---

{% block head %}
<script async src="https://maps.googleapis.com/maps/api/js?key=..."></script>
<!-- Page-specific meta tags -->
{% endblock %}

<!-- Hero Section -->
<section id="home" class="hero-section">
  <!-- Hero content -->
</section>

<!-- Services Section -->
<section id="services" class="services-section">
  <div class="container">
    <h2 class="section-title">Massages & Prijzen</h2>
    <div class="row">
      {%- for service in services -%}
        {% include "service-card.njk" %}
      {%- endfor -%}
    </div>
  </div>
</section>

<!-- Other sections... -->

{% block scripts %}
<script>
  // Page-specific JavaScript
</script>
{% endblock %}
```

### 5.2 Gallery Page

Create `src/gallery.njk`:

```njk
---
layout: base.njk
title: Gallerij
description: Bekijk foto's van Pesila Thai Massage in Rotterdam.
---

<section aria-labelledby="gallery-heading">
  <div class="container">
    <h2 id="gallery-heading" class="section-title">Gallerij</h2>
    <div class="gallery">
      {%- for img in gallery -%}
        {% include "picture.njk" %}
      {%- endfor -%}
    </div>
  </div>
</section>
```

---

## Phase 6: Redirect Pages

### 6.1 Generate Redirects Automatically

Create `src/_data/redirects.json`:

```json
[
  { "from": "aroma-oliemassage", "to": "/#services" },
  { "from": "traditionele-thaise-massage", "to": "/#services" },
  { "from": "voetenmassage", "to": "/#services" },
  { "from": "hotstone-massage", "to": "/#services" },
  { "from": "sportmassage", "to": "/#services" },
  { "from": "deep-tissue", "to": "/#services" },
  { "from": "zwangerschapmassage", "to": "/#services" },
  { "from": "kruidenstempelmassage", "to": "/#services" },
  { "from": "about", "to": "/#about" },
  { "from": "contact", "to": "/#contact" },
  { "from": "service", "to": "/#services" }
]
```

Create `src/redirects.njk`:

```njk
---
pagination:
  data: redirects
  size: 1
  alias: redirect
permalink: "/{{ redirect.from }}/index.html"
---
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="refresh" content="0; url={{ redirect.to }}">
</head>
<body>
    <p>Redirecting to <a href="{{ redirect.to }}">{{ redirect.to }}</a>...</p>
</body>
</html>
```

This generates all 11 redirect pages from a single template!

---

## Phase 7: GitHub Pages Deployment

### 7.1 Update GitHub Actions

Create `.github/workflows/deploy.yml`:

```yaml
name: Build and Deploy

on:
  push:
    branches: [master]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Build site
        run: npm run build

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./_site
```

### 7.2 Update .gitignore

```
node_modules/
_site/
.cache/
```

---

## Migration Checklist

- [ ] Phase 1: Install Eleventy, create config
- [ ] Phase 2: Create base layout and extract nav/footer
- [ ] Phase 3: Move data to JSON files
- [ ] Phase 4: Create reusable components
- [ ] Phase 5: Convert index.html and gallery.html
- [ ] Phase 6: Generate redirect pages from data
- [ ] Phase 7: Set up GitHub Actions deployment
- [ ] Test locally with `npm run serve`
- [ ] Deploy and verify

---

## Benefits After Migration

| Before | After |
|--------|-------|
| Nav repeated 2× (80 lines) | Nav in 1 file (25 lines) |
| Footer repeated 2× (10 lines) | Footer in 1 file (5 lines) |
| 10 service cards (~600 lines) | 1 template + JSON (~100 lines) |
| 25 picture elements (~800 lines) | 1 template + JSON (~50 lines) |
| 11 redirect files (99 lines) | 1 template + JSON (~20 lines) |

**Total reduction:** ~1,600 lines of repetitive HTML eliminated

---

## Rollback Plan

If issues arise, the original HTML files can be restored:
1. Keep original files in a `backup/` folder during migration
2. GitHub Pages can serve static HTML directly (no build required)
3. Simply remove Eleventy config to revert

---

## Next Steps

1. Run `npm init -y && npm install @11ty/eleventy --save-dev`
2. Create directory structure
3. Start with Phase 2 (layouts) - biggest impact with minimal changes
4. Gradually move through phases, testing at each step
