# GEMINI TASK: Build Ordomation Landing Page

**Task ID:** ORDO-WEB-001
**Date:** 2026-02-22
**Priority:** High
**Estimated Effort:** 2-4 hours

---

## Overview

Build a clean, minimal landing page for **ordomation.com** - a Danish automation company focused on intelligent document processing for small businesses.

**Live URL:** https://ordomation.com (will be deployed via GitHub Pages)
**Repo:** https://github.com/ordomation/ordomation.github.io

---

## Tech Stack

- **Framework:** Astro (static site generator)
- **Styling:** Vanilla CSS (no Tailwind, keep it simple)
- **Hosting:** GitHub Pages
- **Build:** `npm run build` → outputs to `dist/`

---

## Design Specifications

### Color Palette

```css
:root {
  /* Neutrals */
  --midnight: #0f172a;
  --slate: #475569;
  --cloud: #f8fafc;
  --white: #ffffff;

  /* Accent */
  --electric: #3b82f6;
  --electric-hover: #2563eb;
  --glow: #60a5fa;

  /* Semantic */
  --success: #22c55e;
}
```

### Typography

```css
/* Import Inter from Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  font-size: 18px;
  line-height: 1.7;
  color: var(--midnight);
}

h1 { font-size: 56px; font-weight: 700; letter-spacing: -0.02em; }
h2 { font-size: 40px; font-weight: 600; letter-spacing: -0.01em; }
h3 { font-size: 24px; font-weight: 600; }
```

### Spacing System

Use 8px base unit: 8, 16, 24, 32, 48, 64, 96, 128

```css
--space-xs: 8px;
--space-sm: 16px;
--space-md: 24px;
--space-lg: 32px;
--space-xl: 48px;
--space-2xl: 64px;
--space-3xl: 96px;
--space-4xl: 128px;
```

### Container

```css
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
}
```

---

## Page Sections

Build these sections in order. Each section should be its own Astro component.

### 1. Navigation (`Nav.astro`)

**Layout:**
- Sticky at top
- Logo (text: "ORDOMATION") on left
- Right side: GitHub icon link
- Height: 64px
- Transparent on hero, white with subtle shadow when scrolled (use JS)

**HTML Structure:**
```html
<nav class="nav">
  <div class="container nav-content">
    <a href="/" class="logo">ORDOMATION</a>
    <div class="nav-links">
      <a href="https://github.com/ordomation" target="_blank" aria-label="GitHub">
        <!-- GitHub SVG icon -->
      </a>
    </div>
  </div>
</nav>
```

### 2. Hero (`Hero.astro`)

**Layout:**
- Full viewport height (100vh)
- Vertically and horizontally centered content
- Background: subtle gradient white → cloud

**Content:**
- Headline: "Automation that understands your business"
- Subhead: "Intelligent document processing and bookkeeping automation for Danish small businesses. From inbox to organized archive, automatically."
- Two buttons:
  - Primary: "Learn More" (scrolls to features)
  - Secondary: "View on GitHub" (links to org)

**CSS Notes:**
- Headline: 56px, midnight, max-width 800px
- Subhead: 20px, slate, max-width 600px
- Buttons: pill-shaped (border-radius: 9999px), 16px padding
- Optional: Add subtle animated dots or grid in background

### 3. Features (`Features.astro`)

**Layout:**
- Three cards in a row (flexbox or grid)
- Each card: centered content, 300px min-width

**Cards:**

**Card 1:**
- Icon: 📧 (or envelope SVG)
- Title: "Email Capture"
- Description: "Monitor multiple email accounts. Extract attachments automatically. No more manual downloading."

**Card 2:**
- Icon: 🤖 (or robot SVG)
- Title: "AI Classification"
- Description: "Our AI reads invoices like a human. Identifies suppliers, amounts, dates. Learns your business patterns."

**Card 3:**
- Icon: 📊 (or chart SVG)
- Title: "Bookkeeping Ready"
- Description: "Files organized by quarter, numbered sequentially, ready for e-conomic or Dinero. SKAT compliant from day one."

**CSS Notes:**
- Section padding: 96px top/bottom
- Cards: white background, subtle shadow, rounded corners (16px)
- On hover: slight lift (translateY -4px) and stronger shadow

### 4. Project (`Project.astro`)

**Layout:**
- Dark section (midnight background, white text)
- Two columns: text left (60%), visual right (40%)
- Mobile: stack vertically

**Content:**
- Section label: "Current Project" (small, uppercase, electric color)
- Title: "The Email Library"
- Description paragraphs:
  - "We're building an open-source email archival and classification system designed for Danish small businesses."
  - "It monitors Gmail accounts, extracts invoices and receipts, classifies them using AI, and organizes them into a structured archive ready for your accountant."
- Tech stack badges: n8n, PostgreSQL, Groq AI, TrueNAS
- CTA button: "View Architecture" (links to GitHub docs)

**CSS Notes:**
- Section padding: 128px top/bottom
- Tech badges: pill shape, dark slate background with white text
- Right side: can be a simple diagram SVG or screenshot (placeholder for now)

### 5. Team (`Team.astro`)

**Layout:**
- Two founder cards side by side
- Centered intro text below

**Cards:**
```html
<div class="team-card">
  <div class="team-photo">
    <!-- Placeholder: 200x200 circle with initials -->
  </div>
  <h3 class="team-name">Thue Tønnesen</h3>
  <p class="team-role">Server Admin & Automation</p>
  <p class="team-bio">
    Builds the infrastructure that keeps everything running.
    Passionate about TrueNAS, Kubernetes, and making complex systems simple.
  </p>
  <div class="team-links">
    <a href="#">LinkedIn</a>
    <a href="#">GitHub</a>
  </div>
</div>
```

**For Joachim:** Use placeholder bio until provided:
- Role: "[TBD]"
- Bio: "[Bio coming soon]"

**Shared Story (below cards):**
"We met at HTX Haderslev, where our shared love for building things brought us together. From hardware projects to software systems, we've been collaborating on ideas ever since. Ordomation is where we bring automation to small businesses that deserve the same tools as the big players."

**CSS Notes:**
- Cards: 350px max-width each, centered
- Photo placeholder: 200x200 circle, light gray background with initials
- Gap between cards: 64px

### 6. Open Source (`OpenSource.astro`)

**Layout:**
- Simple centered section
- Heading + description + repo list

**Content:**
- Title: "Open Source"
- Description: "We believe in building in the open. Our tools are free to use, modify, and contribute to."
- Repos (as cards or simple list):
  - email-library: "Email archival and classification system"
  - n8n-templates: "Reusable workflow templates"
  - docs: "Documentation and guides"
- CTA: "View All Repos on GitHub"

**CSS Notes:**
- Light background (cloud)
- Repo cards: minimal, icon + name + description

### 7. Footer (`Footer.astro`)

**Layout:**
- Two columns: left (logo + tagline), right (contact + social)
- Full-width dark section (midnight)

**Content:**
- Left:
  - Logo: "ORDOMATION"
  - Tagline: "Bringing order to business"
- Right:
  - Email: hello@ordomation.com
  - Location: Denmark 🇩🇰
  - Social links: GitHub, LinkedIn
- Bottom: © 2026 Ordomation

**CSS Notes:**
- Padding: 64px top/bottom
- White/slate text on midnight background

---

## File Structure

Create these files:

```
ordomation.com/
├── astro.config.mjs
├── package.json
├── tsconfig.json
├── src/
│   ├── layouts/
│   │   └── Layout.astro
│   ├── components/
│   │   ├── Nav.astro
│   │   ├── Hero.astro
│   │   ├── Features.astro
│   │   ├── Project.astro
│   │   ├── Team.astro
│   │   ├── OpenSource.astro
│   │   └── Footer.astro
│   ├── pages/
│   │   └── index.astro
│   └── styles/
│       └── global.css
├── public/
│   ├── favicon.ico
│   ├── CNAME (contains: ordomation.com)
│   └── images/
│       ├── thue.jpg (placeholder)
│       └── joachim.jpg (placeholder)
└── README.md
```

---

## Configuration Files

### astro.config.mjs
```javascript
import { defineConfig } from 'astro/config';

export default defineConfig({
  site: 'https://ordomation.com',
  base: '/',
});
```

### package.json
```json
{
  "name": "ordomation-website",
  "type": "module",
  "version": "1.0.0",
  "scripts": {
    "dev": "astro dev",
    "build": "astro build",
    "preview": "astro preview"
  },
  "dependencies": {
    "astro": "^4.0.0"
  }
}
```

### public/CNAME
```
ordomation.com
```

---

## GitHub Actions Deployment

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm install
      - run: npm run build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: dist

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - uses: actions/deploy-pages@v4
        id: deployment
```

---

## Responsive Breakpoints

```css
/* Mobile first */
@media (min-width: 640px) { /* sm */ }
@media (min-width: 768px) { /* md */ }
@media (min-width: 1024px) { /* lg */ }
@media (min-width: 1280px) { /* xl */ }
```

**Key responsive changes:**
- Hero headline: 56px → 36px on mobile
- Feature cards: 3 columns → 1 column on mobile
- Project section: 2 columns → stacked on mobile
- Team cards: 2 columns → 1 column on mobile

---

## Animations (Optional)

Keep animations subtle and performant:

1. **Scroll reveal:** Elements fade up when entering viewport
2. **Button hover:** Scale 1.02, shadow increase
3. **Card hover:** Lift (translateY -4px)
4. **Nav background:** Transition opacity on scroll

Use CSS transitions, avoid heavy JS animation libraries.

---

## SEO & Meta

In `Layout.astro`, include:

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ordomation - Intelligent Business Automation</title>
  <meta name="description" content="Intelligent document processing and bookkeeping automation for Danish small businesses. From inbox to organized archive, automatically.">

  <!-- Open Graph -->
  <meta property="og:title" content="Ordomation">
  <meta property="og:description" content="Intelligent business automation for Danish small businesses">
  <meta property="og:image" content="/images/og-image.png">
  <meta property="og:url" content="https://ordomation.com">

  <!-- Favicon -->
  <link rel="icon" type="image/x-icon" href="/favicon.ico">

  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
</head>
```

---

## Checklist

When building, verify:

- [ ] All sections render correctly
- [ ] Responsive at 375px, 768px, 1024px, 1440px
- [ ] All links work (GitHub, email)
- [ ] Smooth scroll to sections works
- [ ] Nav changes on scroll
- [ ] `npm run build` succeeds
- [ ] GitHub Pages deployment works
- [ ] Custom domain resolves correctly
- [ ] Lighthouse score > 90 for performance

---

## Assets Needed

Before completion, we need:

1. **Founder photos:** thue.jpg, joachim.jpg (square, 400x400 minimum)
2. **Favicon:** favicon.ico (32x32 and 16x16)
3. **OG image:** og-image.png (1200x630)
4. **Joachim's bio:** 2-3 sentences about his background

---

## Questions for Clarification

If anything is unclear:
1. Should we add a contact form, or is email link sufficient?
2. Any specific architecture diagram to include?
3. Danish language toggle needed for v1?
4. Any additional projects to showcase?

---

**Build this and push to GitHub. The site should go live automatically via GitHub Pages.**

Good luck! 🚀
